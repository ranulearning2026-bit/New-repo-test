# Use-Case Sequence Diagrams

> Generated from `.aee/c4-usecases.json` and `.aee/c4-model.labelled.json`.
> `aee-c4-seq-render` was not available; diagrams rendered directly from the curated use-case definitions.
>
> **Static approximation caveat:** these scenarios show one plausible message ordering derived from static call-site analysis; they are not execution traces. Alternative paths (error branches, async callbacks, concurrent callers) are not shown. Steps are ordered by call-site line number, not by runtime scheduling.

---

## UC-1: Retrieve encryption key

**Scenario:** A Nova component requests the AES symmetric encryption key from the Key Manager via the Castellan KeyManager interface.

Participants: `nova` (broader Nova caller, out of pipeline scope), `ConfKeyManager` (keymgr), `castellan` (external library).

```mermaid
sequenceDiagram
  participant Nova as nova (caller)
  participant CKM as ConfKeyManager
  participant Cas as castellan

  Nova->>CKM: get(context, managed_object_id)
  CKM->>Cas: SymmetricKey('AES', len*8, bytes)
  Note right of CKM: decodes hex value from nova.conf; raises KeyError if id mismatch
  Cas-->>CKM: SymmetricKey
  CKM-->>Nova: SymmetricKey
```

Source: KB `conf_key_mgr.py` L102-115 (get), L71-73 (_get_key).

---

## UC-2: Enforce API quota limit

**Scenario:** A Nova API handler checks whether an action would exceed the configured API limit for an entity type. Uses the unified or legacy quota driver as configured.

```mermaid
sequenceDiagram
  participant Nova as nova (API handler)
  participant EAL as enforce_api_limit
  participant UUL as use_unified_limits
  participant OL as oslo_limit Enforcer
  participant SE as should_enforce

  Nova->>EAL: enforce_api_limit(entity_type, count)
  EAL->>UUL: use_unified_limits()
  UUL-->>EAL: bool
  EAL->>OL: Enforcer(callback).enforce(project_id, deltas)
  Note over EAL,OL: only when unified limits enabled
  OL->>SE: should_enforce(ProjectOverLimit)
  Note right of OL: oslo_limit calls back when limit exceeded
  SE-->>OL: bool
  OL-->>EAL: raises OverQuota or returns
  EAL-->>Nova: None or raises OverQuota
```

Source: Component:limit `local.py` L118-145 (enforce_api_limit), KB `utils.py` L33-34 (use_unified_limits), L91-182 (should_enforce).

---

## UC-3: Enforce placement resource limits

**Scenario:** The Nova scheduler enforces instance count and resource class limits before allocating placement resources. The oslo_limit Enforcer calls back into `_get_usage` to retrieve current counts from the Placement API.

```mermaid
sequenceDiagram
  participant Nova as nova (scheduler)
  participant ENIR as enforce_num_instances_and_resources
  participant OL as oslo_limit Enforcer
  participant GU as _get_usage
  participant NSC as nova.scheduler.client

  Nova->>ENIR: enforce_num_instances_and_resources(context, project_id, request_spec, min, max)
  ENIR->>OL: Enforcer(callback).enforce(project_id, deltas)
  OL->>GU: _get_usage(context, project_id, resource_names)
  Note right of OL: callback invoked by enforcer to get current usage
  GU->>NSC: report_client_singleton().get_usages_counts_for_limits(context, project_id)
  NSC-->>GU: dict[resource, count]
  GU-->>OL: dict[resource, count]
  OL-->>ENIR: raises ProjectOverLimit or returns
  ENIR-->>Nova: int (allowed max_count) or raises
```

Source: Component:limit `placement.py` L152-212 (enforce_num_instances_and_resources), L45-113 (_get_usage).

---

## UC-4: Service registers with service group

**Scenario:** A Nova service worker registers itself in the service group and starts sending heartbeats to the database via the DbDriver (Memcached driver follows the same pattern via `MemcachedDriver.join`).

```mermaid
sequenceDiagram
  participant Nova as nova (service worker)
  participant APIJ as API.join
  participant DBJ as DbDriver.join
  participant OM as oslo_messaging (loopingcall)

  Nova->>APIJ: API.join(member, group, service)
  APIJ->>DBJ: DbDriver.join(member, group, service)
  Note right of APIJ: or MemcachedDriver.join per configuration
  DBJ->>OM: loopingcall(self._report_state, interval)
  Note right of DBJ: schedules periodic DB heartbeat
  OM-->>DBJ: loopingcall handle
  DBJ-->>APIJ: loopingcall handle
  APIJ-->>Nova: loopingcall handle
```

Source: Component:servicegroup `api.py` L63-70 (API.join), KB `drivers/db.py` L37-55 (DbDriver.join).

---

## UC-5: Check service liveness

**Scenario:** A Nova conductor queries whether a service node is considered alive based on its last heartbeat timestamp.

```mermaid
sequenceDiagram
  participant Nova as nova (conductor)
  participant APIU as API.service_is_up
  participant DBIU as DbDriver.is_up

  Nova->>APIU: API.service_is_up(service_ref)
  Note over APIU: returns False immediately for forced-down services
  APIU->>DBIU: DbDriver.is_up(service_ref)
  Note right of APIU: or MemcachedDriver.is_up per configuration
  DBIU-->>Nova: bool (updated_at within threshold?)
  APIU-->>Nova: bool
```

Source: Component:servicegroup `api.py` L72-79 (API.service_is_up), KB `drivers/db.py` L57-81 (DbDriver.is_up).
