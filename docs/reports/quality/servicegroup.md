# Quality: servicegroup

[← Quality Report](../quality-report.md)

**Component root:** `src/nova/servicegroup/`

## Overview

| Measure | Value |
|---------|------:|
| Files | 6 |
| Code lines | 220 |
| Findings | 6 |
| Findings per 1,000 LOC | 27.3 |

### Severity breakdown

| CRITICAL | HIGH | MEDIUM | LOW | INFO |
|:--------:|:----:|:------:|:---:|:----:|
| — | — | 3 | 3 | — |

### Class breakdown

| Class | Count |
|-------|------:|
| error-handling / CWE-703 | 2 |
| code-quality | 3 |
| code-duplication | 1 |

## Findings

| Severity | ID | Class / CWE | Location | Title | Sources and tools | Evidence |
|----------|----|-------------|----------|-------|-------------------|----------|
| MEDIUM | M-b2370611310b | error-handling / CWE-703 | `drivers/db.py:117-117` | Broad 'except Exception' in _report_state can silently swallow unexpected errors | Scanner; pylint | pylint W0718 |
| MEDIUM | M-a093f815104b | code-duplication | `drivers/mc.py:1-1` | Duplicated _convert_keys_to_legacy_name and get_legacy_default_limits between limit/local.py and limit/placement.py | Scanner; pylint | pylint R0801 |
| MEDIUM | M-3ebe9add5a3a | error-handling / CWE-703 | `drivers/mc.py:111-111` | Broad 'except Exception' in _report_state can silently swallow unexpected errors | Scanner; pylint,ruff | pylint,ruff W0718 |
| LOW | M-2a3e738cb927 | code-quality | `api.py:37-37` | Class API lacks a docstring | Scanner; pylint | pylint C0115 |
| LOW | M-138304f5ea60 | code-quality | `drivers/db.py:32-32` | Class DbDriver lacks a docstring | Scanner; pylint | pylint C0115 |
| LOW | M-bf793869ccd6 | code-quality | `drivers/mc.py:38-38` | Class MemcachedDriver lacks a docstring | Scanner; pylint | pylint C0115 |
