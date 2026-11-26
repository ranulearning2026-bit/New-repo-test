# Quality: keymgr

[← Quality Report](../quality-report.md)

**Component root:** `src/nova/keymgr/`

## Overview

| Measure | Value |
|---------|------:|
| Files | 2 |
| Code lines | 100 |
| Findings | 1 |
| Findings per 1,000 LOC | 10.0 |

### Severity breakdown

| CRITICAL | HIGH | MEDIUM | LOW | INFO |
|:--------:|:----:|:------:|:---:|:----:|
| — | — | — | 1 | — |

### Class breakdown

| Class | Count |
|-------|------:|
| code-quality | 1 |

## Findings

| Severity | ID | Class / CWE | Location | Title | Sources and tools | Evidence |
|----------|----|-------------|----------|-------|-------------------|----------|
| LOW | M-5d7639b7de80 | code-quality | `conf_key_mgr.py:87-87` | 3 public methods of ConfKeyManager lack docstrings (create_key_pair L87, add_consumer L133, remove_consumer L138) | Scanner; pylint | pylint C0116 |
