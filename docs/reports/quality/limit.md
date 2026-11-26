# Quality: limit

[← Quality Report](../quality-report.md)

**Component root:** `src/nova/limit/`

## Overview

| Measure | Value |
|---------|------:|
| Files | 4 |
| Code lines | 432 |
| Findings | 17 |
| Findings per 1,000 LOC | 39.4 |

### Severity breakdown

| CRITICAL | HIGH | MEDIUM | LOW | INFO |
|:--------:|:----:|:------:|:---:|:----:|
| — | 1 | 10 | 6 | — |

### Class breakdown

| Class | Count |
|-------|------:|
| excessive-complexity | 7 |
| code-quality | 8 |
| error-handling / CWE-703 | 1 |
| bug-risk | 1 |

## Findings

| Severity | ID | Class / CWE | Location | Title | Sources and tools | Evidence |
|----------|----|-------------|----------|-------|-------------------|----------|
| HIGH | M-eb91d80449c3 | excessive-complexity | `placement.py:45-113` | _get_usage has maximum nesting depth 10, exceeding threshold of 4 | Scanner; lizard | lizard nesting |
| MEDIUM | M-210abd4aa8a1 | excessive-complexity | `local.py:148-195` | enforce_db_limit has maximum nesting depth 5, exceeding threshold of 4 | Scanner; lizard | lizard nesting |
| MEDIUM | M-bfbd8b7dfec1 | excessive-complexity | `placement.py:45-45` | _get_usage has 13 branches, exceeding the threshold of 12 | Scanner; pylint | pylint R0912 |
| MEDIUM | M-93c9728fc5f5 | excessive-complexity | `placement.py:45-113` | _get_usage has cyclomatic complexity 16, exceeding threshold of 15 | Scanner; lizard | lizard ccn |
| MEDIUM | M-ea0bc9437d05 | bug-risk | `placement.py:68-68` | .strip() with multi-character string strips individual chars, not the whole substring | Scanner; ruff | ruff B005 |
| MEDIUM | M-00c927e09fcd | code-quality | `placement.py:152-152` | enforce_num_instances_and_resources has 7 arguments, exceeding the threshold of 5 | Scanner; pylint | pylint R0913 |
| MEDIUM | M-6be5ae5b8952 | code-quality | `placement.py:152-212` | enforce_num_instances_and_resources has 7 parameters, exceeding threshold of 6 | Scanner; lizard | lizard params |
| MEDIUM | M-f81890a836e6 | excessive-complexity | `placement.py:152-212` | enforce_num_instances_and_resources has maximum nesting depth 7, exceeding threshold of 4 | Scanner; lizard | lizard nesting |
| MEDIUM | M-99cc7c0a4fe1 | excessive-complexity | `utils.py:52-88` | _identity_client has maximum nesting depth 6, exceeding threshold of 4 | Scanner; lizard | lizard nesting |
| MEDIUM | M-5d0fac719c61 | code-quality | `utils.py:53-53` | Global statement in _identity_client creates a mutable singleton without thread safety | Scanner; pylint | pylint W0603 |
| MEDIUM | M-aa4819b0836b | excessive-complexity | `utils.py:91-182` | should_enforce has maximum nesting depth 7, exceeding threshold of 4 | Scanner; lizard | lizard nesting |
| LOW | M-f2ed48b0e43f | code-quality | `local.py:208-208` | Public function get_legacy_default_limits lacks a docstring | Scanner; pylint | pylint C0116 |
| LOW | M-29e6d401b413 | code-quality | `placement.py:143-143` | _get_enforcer's outer project_id parameter is unused; the closure shadows it with its own | Scanner; pylint | pylint W0613 |
| LOW | M-4d631c66594c | error-handling / CWE-703 | `placement.py:209-209` | Exception raised without chaining; original ValueError context is lost | Scanner; pylint | pylint W0707 |
| LOW | M-3569d2d92dde | code-quality | `placement.py:223-223` | 3 public functions lack docstrings (get_legacy_default_limits L223, get_legacy_project_limits L229, get_legacy_counts L235) | Scanner; pylint | pylint C0116 |
| LOW | M-2cfc377a77a4 | code-quality | `utils.py:33-33` | 2 public functions lack docstrings (use_unified_limits L33, registered_limits L47) | Scanner; pylint | pylint C0116 |
| LOW | M-d5c1e6e1f715 | code-quality | `utils.py:37-37` | Class IdentityClient lacks a docstring | Scanner; pylint | pylint C0115 |
