# Quality Report

<!-- quality-source:src/nova/ start -->
76db4114

## 1. Summary

**Batch:** `76db4114` · **Source:** `src/nova/` · **Date:** 2026-11-26

### Measure / Count

| Measure | Count |
|---------|------:|
| Files analysed | 12 |
| Files with findings | 7 |
| Confirmed findings | 24 |
| Severity: CRITICAL | 0 |
| Severity: HIGH | 1 |
| Severity: MEDIUM | 13 |
| Severity: LOW | 10 |
| Severity: INFO | 0 |
| Source: Scanner | 24 |
| Source: Agent Studio analysis | 0 |
| Production findings | 24 |
| Test findings | 0 |
| Scan tool: ruff | 24 (co-scanner) |
| Scan tool: pylint | 24 (co-scanner) |
| Scan tool: lizard | 24 (co-scanner) |
| Scan tool: cpd | 24 (co-scanner) |
| Agent Studio analysis | 0 |

### Severity × Category

| Class | CRITICAL | HIGH | MEDIUM | LOW | INFO | Total |
|-------|:--------:|:----:|:------:|:---:|:----:|------:|
| excessive-complexity | — | 1 | 6 | — | — | 7 |
| code-quality | — | — | 3 | 9 | — | 12 |
| error-handling / CWE-703 | — | — | 2 | 1 | — | 3 |
| bug-risk | — | — | 1 | — | — | 1 |
| code-duplication | — | — | 1 | — | — | 1 |
| **Total** | — | **1** | **13** | **10** | — | **24** |

---

## 2. Findings

| Severity | ID | Class / CWE | Location | Title | Sources and tools | Evidence |
|----------|----|-------------|----------|-------|-------------------|----------|
| HIGH | M-eb91d80449c3 | excessive-complexity | `src/nova/limit/placement.py:45-113` | _get_usage has maximum nesting depth 10, exceeding threshold of 4 | Scanner; lizard | lizard nesting |
| MEDIUM | M-210abd4aa8a1 | excessive-complexity | `src/nova/limit/local.py:148-195` | enforce_db_limit has maximum nesting depth 5, exceeding threshold of 4 | Scanner; lizard | lizard nesting |
| MEDIUM | M-bfbd8b7dfec1 | excessive-complexity | `src/nova/limit/placement.py:45-45` | _get_usage has 13 branches, exceeding the threshold of 12 | Scanner; pylint | pylint R0912 |
| MEDIUM | M-93c9728fc5f5 | excessive-complexity | `src/nova/limit/placement.py:45-113` | _get_usage has cyclomatic complexity 16, exceeding threshold of 15 | Scanner; lizard | lizard ccn |
| MEDIUM | M-ea0bc9437d05 | bug-risk | `src/nova/limit/placement.py:68-68` | .strip() with multi-character string strips individual chars, not the whole substring | Scanner; ruff | ruff B005 |
| MEDIUM | M-00c927e09fcd | code-quality | `src/nova/limit/placement.py:152-152` | enforce_num_instances_and_resources has 7 arguments, exceeding the threshold of 5 | Scanner; pylint | pylint R0913 |
| MEDIUM | M-6be5ae5b8952 | code-quality | `src/nova/limit/placement.py:152-212` | enforce_num_instances_and_resources has 7 parameters, exceeding threshold of 6 | Scanner; lizard | lizard params |
| MEDIUM | M-f81890a836e6 | excessive-complexity | `src/nova/limit/placement.py:152-212` | enforce_num_instances_and_resources has maximum nesting depth 7, exceeding threshold of 4 | Scanner; lizard | lizard nesting |
| MEDIUM | M-99cc7c0a4fe1 | excessive-complexity | `src/nova/limit/utils.py:52-88` | _identity_client has maximum nesting depth 6, exceeding threshold of 4 | Scanner; lizard | lizard nesting |
| MEDIUM | M-5d0fac719c61 | code-quality | `src/nova/limit/utils.py:53-53` | Global statement in _identity_client creates a mutable singleton without thread safety | Scanner; pylint | pylint W0603 |
| MEDIUM | M-aa4819b0836b | excessive-complexity | `src/nova/limit/utils.py:91-182` | should_enforce has maximum nesting depth 7, exceeding threshold of 4 | Scanner; lizard | lizard nesting |
| MEDIUM | M-b2370611310b | error-handling / CWE-703 | `src/nova/servicegroup/drivers/db.py:117-117` | Broad 'except Exception' in _report_state can silently swallow unexpected errors | Scanner; pylint | pylint W0718 |
| MEDIUM | M-a093f815104b | code-duplication | `src/nova/servicegroup/drivers/mc.py:1-1` | Duplicated _convert_keys_to_legacy_name and get_legacy_default_limits between limit/local.py and limit/placement.py | Scanner; pylint | pylint R0801 |
| MEDIUM | M-3ebe9add5a3a | error-handling / CWE-703 | `src/nova/servicegroup/drivers/mc.py:111-111` | Broad 'except Exception' in _report_state can silently swallow unexpected errors | Scanner; pylint,ruff | pylint,ruff W0718 |
| LOW | M-5d7639b7de80 | code-quality | `src/nova/keymgr/conf_key_mgr.py:87-87` | 3 public methods of ConfKeyManager lack docstrings (create_key_pair L87, add_consumer L133, remove_consumer L138) | Scanner; pylint | pylint C0116 |
| LOW | M-f2ed48b0e43f | code-quality | `src/nova/limit/local.py:208-208` | Public function get_legacy_default_limits lacks a docstring | Scanner; pylint | pylint C0116 |
| LOW | M-29e6d401b413 | code-quality | `src/nova/limit/placement.py:143-143` | _get_enforcer's outer project_id parameter is unused; the closure shadows it with its own | Scanner; pylint | pylint W0613 |
| LOW | M-4d631c66594c | error-handling / CWE-703 | `src/nova/limit/placement.py:209-209` | Exception raised without chaining; original ValueError context is lost | Scanner; pylint | pylint W0707 |
| LOW | M-3569d2d92dde | code-quality | `src/nova/limit/placement.py:223-223` | 3 public functions lack docstrings (get_legacy_default_limits L223, get_legacy_project_limits L229, get_legacy_counts L235) | Scanner; pylint | pylint C0116 |
| LOW | M-2cfc377a77a4 | code-quality | `src/nova/limit/utils.py:33-33` | 2 public functions lack docstrings (use_unified_limits L33, registered_limits L47) | Scanner; pylint | pylint C0116 |
| LOW | M-d5c1e6e1f715 | code-quality | `src/nova/limit/utils.py:37-37` | Class IdentityClient lacks a docstring | Scanner; pylint | pylint C0115 |
| LOW | M-2a3e738cb927 | code-quality | `src/nova/servicegroup/api.py:37-37` | Class API lacks a docstring | Scanner; pylint | pylint C0115 |
| LOW | M-138304f5ea60 | code-quality | `src/nova/servicegroup/drivers/db.py:32-32` | Class DbDriver lacks a docstring | Scanner; pylint | pylint C0115 |
| LOW | M-bf793869ccd6 | code-quality | `src/nova/servicegroup/drivers/mc.py:38-38` | Class MemcachedDriver lacks a docstring | Scanner; pylint | pylint C0115 |

---

## 3. Remediation

| Class | Findings | Guidance |
|-------|:--------:|----------|
| excessive-complexity | 7 | Split the function into smaller functions with one purpose each, until it is below the agreed complexity threshold. |
| code-quality | 12 | Correct the reported construct following the language guidelines and the project coding standard. |
| error-handling / CWE-703 | 3 | Catch the narrowest exception that can occur, handle or propagate it with its details, and never discard an error silently. |
| bug-risk | 1 | Correct the construct so that it behaves as its name and documentation say, and cover it with a test. |
| code-duplication | 1 | Move the repeated logic into one shared function or module and call it from each place. |

---

## 4. Agent Studio analysis

**Finding counts:** Scanner: 24 · Agent Studio analysis (manual): 0

**Triage:** 72 candidates evaluated · 24 kept · 48 dropped

**Code Quality Reviewer verdict:** missing (no verdict.json found)

### Roles

| Stage | Status |
|-------|--------|
| Pre-stage (Fact Extractor / Verifier Critic) | ran |
| Code Quality Analyzer | ran |
| Code Quality Reviewer | missing |

### Finding detail

| ID | Title | Confidence | Rationale |
|----|-------|:----------:|-----------|
| M-eb91d80449c3 | _get_usage has maximum nesting depth 10, exceeding threshold of 4 | confirmed | lizard reports nesting=10 (threshold 4) in _get_usage. A depth of 10 is more than twice the threshold (2*4=8), making this a high-severity complexity finding. Flatten by extracting each deeply nested block into a dedicated helper function. |
| M-210abd4aa8a1 | enforce_db_limit has maximum nesting depth 5, exceeding threshold of 4 | confirmed | lizard reports nesting=5 (threshold 4) in enforce_db_limit (lines 148-195, 48 lines). The 5-level nesting makes the conditional logic hard to follow. Refactor the innermost nested block into a named helper function to flatten the structure. |
| M-bfbd8b7dfec1 | _get_usage has 13 branches, exceeding the threshold of 12 | confirmed | pylint R0912 reports 13 conditional branches in _get_usage, one above the threshold of 12. Combined with CCN=16 and nesting=10, this function is difficult to read and test. Extract distinct resource-class handling blocks into named helpers to reduce branch count. |
| M-93c9728fc5f5 | _get_usage has cyclomatic complexity 16, exceeding threshold of 15 | confirmed | lizard reports CCN=16 (threshold 15) for _get_usage (lines 45-113). Refactor distinct resource-class handling (orc.*, volume, quota) into separate strategy functions to bring complexity below the threshold. |
| M-ea0bc9437d05 | .strip() with multi-character string strips individual chars, not the whole substring | confirmed | str.strip(chars) removes any leading/trailing character that appears in the chars set, not the string as a whole prefix or suffix. If the intent is prefix/suffix removal, use str.removesuffix/removeprefix (Python 3.9+). If per-character stripping is correct, add a comment to document that intent. |
| M-00c927e09fcd | enforce_num_instances_and_resources has 7 arguments, exceeding the threshold of 5 | confirmed | pylint R0913/R0917 reports 7 parameters on enforce_num_instances_and_resources vs the threshold of 5, confirmed by the lizard params metric. Introduce a dataclass or named tuple to bundle related arguments (request_spec, min_count, max_count) and reduce the arity. |
| M-6be5ae5b8952 | enforce_num_instances_and_resources has 7 parameters, exceeding threshold of 6 | confirmed | lizard reports params=7 (threshold 6) for enforce_num_instances_and_resources (lines 152-212). Group request_spec, min_count, and max_count into a dataclass to reduce the argument count below the threshold. |
| M-f81890a836e6 | enforce_num_instances_and_resources has maximum nesting depth 7, exceeding threshold of 4 | confirmed | lizard reports nesting=7 (threshold 4) in enforce_num_instances_and_resources (lines 152-212). Extract the inner retry and exception-handling blocks into named helpers to reduce nesting depth. |
| M-99cc7c0a4fe1 | _identity_client has maximum nesting depth 6, exceeding threshold of 4 | confirmed | lizard reports nesting=6 (threshold 4) in _identity_client (lines 52-88). Extract the innermost conditional and error-handling blocks into helper functions to reduce nesting. |
| M-5d0fac719c61 | Global statement in _identity_client creates a mutable singleton without thread safety | confirmed | Line 53 uses 'global IDENTITY_CLIENT' for lazy singleton initialisation. In a concurrent environment two threads can both observe IDENTITY_CLIENT as None and each create a client; the second overwrites the first. Use a module-level lock or threading.local to guard the singleton creation. |
| M-aa4819b0836b | should_enforce has maximum nesting depth 7, exceeding threshold of 4 | confirmed | lizard reports nesting=7 (threshold 4) in should_enforce (lines 91-182), a 92-line business logic function with CCN=12. Flatten by extracting the per-limit-type classification loops into named helpers. |
| M-b2370611310b | Broad 'except Exception' in _report_state can silently swallow unexpected errors | confirmed | Line 117 catches all Exceptions during periodic service state reporting. Unexpected errors (network, DB failures) may only be logged and swallowed, so a misbehaving service can continue without its state being recorded. Narrow the except clause to known exception types or re-raise after logging. |
| M-a093f815104b | Duplicated _convert_keys_to_legacy_name and get_legacy_default_limits between limit/local.py and limit/placement.py | confirmed | pylint R0801 reports ~15 identical lines between limit/local.py:200-215 and limit/placement.py:215-229 (the _convert_keys_to_legacy_name helper and get_legacy_default_limits function). Extract these into a shared module (e.g. limit/utils.py) to prevent divergence. |
| M-3ebe9add5a3a | Broad 'except Exception' in _report_state can silently swallow unexpected errors | confirmed | Line 111 catches all Exceptions during periodic service state reporting. Unexpected errors may only be logged and swallowed, leaving service membership state stale. Narrow the except clause to known exception types or re-raise after logging. |
| M-5d7639b7de80 | 3 public methods of ConfKeyManager lack docstrings (create_key_pair L87, add_consumer L133, remove_consumer L138) | confirmed | create_key_pair, add_consumer, and remove_consumer are public interface methods with no docstrings; callers cannot determine expected behaviour or error conditions from the signature alone. Add a one-line docstring to each method explaining its purpose or that it raises NotImplementedError. |
| M-f2ed48b0e43f | Public function get_legacy_default_limits lacks a docstring | confirmed | get_legacy_default_limits is a public function with no docstring; callers cannot determine the structure of the returned dict or any caching behaviour from the signature alone. Add a one-line docstring describing the returned mapping. |
| M-29e6d401b413 | _get_enforcer's outer project_id parameter is unused; the closure shadows it with its own | confirmed | The project_id argument of _get_enforcer is never referenced in the function body; the nested callback already receives its own project_id from the Enforcer at call time. The dead parameter misleads callers into thinking they bind the enforcer to a specific project. Remove the parameter or document why it is intentionally ignored. |
| M-4d631c66594c | Exception raised without chaining; original ValueError context is lost | confirmed | Line 209 catches ValueError and re-raises exception.TooManyInstances without 'from exc', discarding the original traceback. Use 'raise exception.TooManyInstances(str(e)) from exc' to preserve the exception chain for easier debugging. |
| M-3569d2d92dde | 3 public functions lack docstrings (get_legacy_default_limits L223, get_legacy_project_limits L229, get_legacy_counts L235) | confirmed | get_legacy_default_limits, get_legacy_project_limits, and get_legacy_counts are public API functions with no docstrings. Add a one-line docstring to each describing the returned dict structure and any notable side effects such as registered-limits caching. |
| M-2cfc377a77a4 | 2 public functions lack docstrings (use_unified_limits L33, registered_limits L47) | confirmed | use_unified_limits (called from local.py and placement.py) and registered_limits (a method of IdentityClient) have no docstrings. Add a one-line docstring to each; for use_unified_limits, document its dependency on CONF.quota.driver. |
| M-d5c1e6e1f715 | Class IdentityClient lacks a docstring | confirmed | IdentityClient has no class docstring. Add a brief description explaining its role as a Keystone identity proxy and noting the connection, service_id, and region_id parameters. |
| M-2a3e738cb927 | Class API lacks a docstring | confirmed | The servicegroup API class has no class docstring despite being the primary public interface for service group management. Add a docstring describing the driver dispatch model and the INITIAL_REPORTING_DELAY behaviour. |
| M-138304f5ea60 | Class DbDriver lacks a docstring | confirmed | DbDriver is a concrete servicegroup driver with no class docstring. Add a brief description of the database-backed heartbeat mechanism and the _report_state callback. |
| M-bf793869ccd6 | Class MemcachedDriver lacks a docstring | confirmed | MemcachedDriver has no class docstring. Add a brief description of the memcached-backed heartbeat mechanism and the cache expiry/TTL behaviour. |

---

## 5. Component scorecard

### Production components

| Component | Files | Code lines | CRITICAL | HIGH | MEDIUM | LOW | INFO | Per 1k LOC |
|-----------|------:|----------:|:--------:|:----:|:------:|:---:|:----:|----------:|
| [limit](quality/limit.md) | 4 | 432 | — | 1 | 10 | 6 | — | 39.4 |
| [servicegroup](quality/servicegroup.md) | 6 | 220 | — | — | 3 | 3 | — | 27.3 |
| [keymgr](quality/keymgr.md) | 2 | 100 | — | — | — | 1 | — | 10.0 |

No test components in this batch.

---

## 6. Hotspots

### Top 10 functions by CCN (production)

| Rank | Function | File | Lines | CCN |
|-----:|----------|------|------:|----:|
| 1 | `_get_usage` | `src/nova/limit/placement.py` | 45–113 | 16 |
| 2 | `should_enforce` | `src/nova/limit/utils.py` | 91–182 | 12 |
| 3 | `enforce_num_instances_and_resources` | `src/nova/limit/placement.py` | 152–212 | 10 |
| 4 | `_identity_client` | `src/nova/limit/utils.py` | 52–88 | 9 |
| 5 | `enforce_db_limit` | `src/nova/limit/local.py` | 148–195 | 7 |
| 6 | `_report_state` | `src/nova/servicegroup/drivers/db.py` | 87–124 | 6 |
| 7 | `_get_deltas` | `src/nova/limit/placement.py` | 116–139 | 6 |
| 8 | `enforce_api_limit` | `src/nova/limit/local.py` | 118–145 | 6 |
| 9 | `updated_time` | `src/nova/servicegroup/drivers/mc.py` | 73–90 | 4 |
| 10 | `_report_state` | `src/nova/servicegroup/drivers/mc.py` | 92–117 | 4 |

### Top 5 largest production files by code lines (KB)

| Rank | File | Code lines |
|-----:|------|----------:|
| 1 | `src/nova/limit/placement.py` | 164 |
| 2 | `src/nova/limit/local.py` | 162 |
| 3 | `src/nova/limit/utils.py` | 96 |
| 4 | `src/nova/keymgr/conf_key_mgr.py` | 95 |
| 5 | `src/nova/servicegroup/drivers/db.py` | 78 |

---

## 7. Findings by category

| Category | Total | CRITICAL | HIGH | MEDIUM | LOW | INFO | Top 3 components |
|----------|------:|:--------:|:----:|:------:|:---:|:----:|-----------------|
| complexity | 7 | — | 1 | 6 | — | — | limit (7) |
| documentation | 8 | — | — | — | 8 | — | limit (4), servicegroup (3), keymgr (1) |
| maintainability | 4 | — | — | 3 | 1 | — | limit (4) |
| error-handling | 3 | — | — | 2 | 1 | — | servicegroup (2), limit (1) |
| bug-risk | 1 | — | — | 1 | — | — | limit (1) |
| duplication | 1 | — | — | 1 | — | — | servicegroup (1) |

---

## 8. Test code

No test components in this batch.

---

## 9. Analysis history

| Date | Files analysed | Files with findings | Findings |
|------|---------------:|--------------------:|---------:|
| 2026-11-26 | 12 | 7 | 24 |

---

## 10. Scope and tools

**Source folder:** `src/nova/` · **Branch:** `agent_workspace` · **Batch SHA:** `76db4114ac412837a25751b066b165cd1308d439`

| Tool | Status | Version | Configuration |
|------|--------|---------|---------------|
| ruff | OK | 0.17.6 | default |
| pylint | OK | 4.1.4 | default |
| cpd | OK | 7.7.0 | minimum-tokens 100 |
| lizard | OK | 1.26.1 | default |

**Files analysed:**

| File | Language | Status |
|------|----------|--------|
| `src/nova/keymgr/__init__.py` | Python | analysed |
| `src/nova/keymgr/conf_key_mgr.py` | Python | analysed |
| `src/nova/limit/__init__.py` | Python | analysed |
| `src/nova/limit/local.py` | Python | analysed |
| `src/nova/limit/placement.py` | Python | analysed |
| `src/nova/limit/utils.py` | Python | analysed |
| `src/nova/servicegroup/__init__.py` | Python | analysed |
| `src/nova/servicegroup/api.py` | Python | analysed |
| `src/nova/servicegroup/drivers/__init__.py` | Python | analysed |
| `src/nova/servicegroup/drivers/base.py` | Python | analysed |
| `src/nova/servicegroup/drivers/db.py` | Python | analysed |
| `src/nova/servicegroup/drivers/mc.py` | Python | analysed |

**Code Quality Reviewer verdict:** missing

**Suppressed rules and tool problems:** None (see `.aee/quality-warnings.md`).

---

## 11. Overlap with security findings

No files in this batch appear in the security findings log (all 12 files had `findingCount: 0` in the Security Log). No overlap to report.

<!-- quality-source:src/nova/ end -->
