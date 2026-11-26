# Unresolved Items Index

> **Tool availability note:** `aee-c4-model`, `aee-c4-verify`, `aee-c4-render`, and `aee-c4-seq-render` were not found in this environment (exit 127). The C4 model structure was derived manually from the same KB records and link-graph inputs the tool would use. The label-never-link verification gate (`aee-c4-verify`) was not run; structural integrity of the labelled model was maintained by construction.

---

## Unresolved and Ambiguous References (Link Graph)

Source: Link Graph `unresolved` list (`.aee/link-graph.json`). These imports could not be resolved because the target modules are not part of the extracted pipeline scope.

| File | Line | Symbol | Reason |
|---|---:|---|---|
| `src/nova/keymgr/conf_key_mgr.py` | 40 | `nova.conf` | module-not-found |
| `src/nova/keymgr/conf_key_mgr.py` | 41 | `nova` | module-not-found |
| `src/nova/keymgr/conf_key_mgr.py` | 42 | `nova.i18n` | module-not-found |
| `src/nova/limit/local.py` | 22 | `nova.conf` | module-not-found |
| `src/nova/limit/local.py` | 23 | `nova` | module-not-found |
| `src/nova/limit/local.py` | 25 | `nova` | module-not-found |
| `src/nova/limit/placement.py` | 20 | `nova.conf` | module-not-found |
| `src/nova/limit/placement.py` | 21 | `nova` | module-not-found |
| `src/nova/limit/placement.py` | 23 | `nova` | module-not-found |
| `src/nova/limit/placement.py` | 24 | `nova` | module-not-found |
| `src/nova/limit/placement.py` | 25 | `nova.scheduler.client` | module-not-found |
| `src/nova/limit/placement.py` | 26 | `nova.scheduler` | module-not-found |
| `src/nova/limit/utils.py` | 23 | `nova.conf` | module-not-found |
| `src/nova/limit/utils.py` | 24 | `nova` | module-not-found |
| `src/nova/servicegroup/api.py` | 22 | `nova.conf` | module-not-found |
| `src/nova/servicegroup/drivers/db.py` | 20 | `nova.conf` | module-not-found |
| `src/nova/servicegroup/drivers/db.py` | 21 | `nova` | module-not-found |
| `src/nova/servicegroup/drivers/db.py` | 22 | `nova.i18n` | module-not-found |
| `src/nova/servicegroup/drivers/mc.py` | 25 | `nova` | module-not-found |
| `src/nova/servicegroup/drivers/mc.py` | 26 | `nova.conf` | module-not-found |
| `src/nova/servicegroup/drivers/mc.py` | 27 | `nova.i18n` | module-not-found |

**Ambiguous references:** 0 (Link Graph `ambiguous`: empty list).

---

## Partial Taint Chains (Security Chains)

Source: `.aee/security-chains.json`.

No taint chains were identified. All 12 source files produced zero security findings (findingCount: 0 across gitleaks, semgrep, and bandit). No confirmed, partial, or terminated chains to report.

---

## UNKNOWN-Language Files (Intake Summary)

Source: `.aee/intake-summary.md`.

None. All 12 files were classified as Python.

---

## Verification Errors (Verification Report)

Source: `.aee/verification-report.json`.

No errors (severity: "error") were found. All 29 verdicts are severity "info" (audit-method notes only).

The Verification Summary is **not** an escalation; it reports "Verified — all 28 documents and finding sets pass with zero errors."

---

## Infrastructure and Dependency Notes

- **Infrastructure-as-code:** No Dockerfiles, Terraform, or Kubernetes manifests found in the repository. C2 container view is deferred. (Fact: Infrastructure Inventory is empty.)
- **Dependency manifests:** No `pom.xml`, `requirements.txt`, `package.json`, or `go.mod` found. Dependency and license scans returned zero findings. (Fact: Nova source is Python-only; no manifest files committed.)
- **Artifact registration gaps:** `Intake Summary`, `Link Graph`, and `Link Summary` files were present on disk at run time but were not registered in `artifacts.jsonl` by their upstream agents; they were registered by this agent before proceeding.
