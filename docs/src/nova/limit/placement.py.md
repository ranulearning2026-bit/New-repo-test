# src/nova/limit/placement.py

## Overview

This file implements Nova's placement-based resource-limit enforcement. It queries the Placement API for per-project resource usage and enforces those counts against Keystone unified limits. The main public entry point is `enforce_num_instances_and_resources`, which recursively decrements `max_count` until a satisfying allocation is found or raises `TooManyInstances`. Supporting functions build the resource deltas from a `RequestSpec`, retrieve an oslo.limit `Enforcer` bound to placement usage callbacks, and provide legacy-name translation helpers (`_convert_keys_to_legacy_name`, `get_legacy_default_limits`, `get_legacy_project_limits`, `get_legacy_counts`) for backward compatibility with the quota API. Lines: total 239, code 164, comment 33, blank 42.

## Defined Symbols

| name | kind | signature | visibility | returns | complexity | lines |
|---|---|---|---|---|---|---|
| `LOG` | constant | — | — | — | — | `src/nova/limit/placement.py:L28` |
| `CONF` | constant | — | — | — | — | `src/nova/limit/placement.py:L29` |
| `LEGACY_LIMITS` | constant | — | — | — | — | `src/nova/limit/placement.py:L31–L35` |
| `_get_placement_usages` | function | `(context: 'nova.context.RequestContext', project_id: str) -> dict[str, int]` | — | `report.report_client_singleton().get_usages_counts_for_limits(context, project_id)` (L41) | 1/5 | `src/nova/limit/placement.py:L38–L42` |
| `_get_usage` | function | `(context: 'nova.context.RequestContext', project_id: str, resource_names: list[str]) -> dict[str, int]` | — | `resource_counts` (L113) | 16/45 | `src/nova/limit/placement.py:L45–L113` |
| `_get_deltas` | function | `(request_spec: 'objects.RequestSpec', count: int) -> dict[str, int]` | — | `deltas` (L139) | 6/16 | `src/nova/limit/placement.py:L116–L139` |
| `_get_enforcer` | function | `(context: 'nova.context.RequestContext', project_id: str) -> limit.Enforcer` | — | `limit.Enforcer(callback)` (L149) | 1/5 | `src/nova/limit/placement.py:L142–L149` |
| `callback` | function | `(project_id, resource_names)` | — | `_get_usage(context, project_id, resource_names)` (L147) | 1/2 | `src/nova/limit/placement.py:L146–L147` |
| `enforce_num_instances_and_resources` | function | `(context: 'nova.context.RequestContext', project_id: str, request_spec: 'objects.RequestSpec', min_count: int, max_count: int, enforcer: limit.Enforcer \| None=None, delta_updates: dict[str, int] \| None=None) -> int` | — | `max_count` (L181), `enforce_num_instances_and_resources(...)` (L203), `max_count` (L212) | 10/33 | `src/nova/limit/placement.py:L152–L212` |
| `_convert_keys_to_legacy_name` | function | `(new_dict)` | — | `legacy` (L220) | 3/5 | `src/nova/limit/placement.py:L215–L220` |
| `get_legacy_default_limits` | function | `()` | — | `_convert_keys_to_legacy_name(dict(new_limits))` (L226) | 1/4 | `src/nova/limit/placement.py:L223–L226` |
| `get_legacy_project_limits` | function | `(project_id)` | — | `_convert_keys_to_legacy_name(dict(new_limits))` (L232) | 1/4 | `src/nova/limit/placement.py:L229–L232` |
| `get_legacy_counts` | function | `(context, project_id)` | — | `_convert_keys_to_legacy_name(new_usage)` (L239) | 1/5 | `src/nova/limit/placement.py:L235–L239` |

## Dependencies

- `os_resource_classes` as `orc` — no names imported (`src/nova/limit/placement.py:L15`)
- `oslo_limit` — imports `exception` as `limit_exceptions` (`src/nova/limit/placement.py:L16`)
- `oslo_limit` — imports `limit` (`src/nova/limit/placement.py:L17`)
- `oslo_log` — imports `log` as `logging` (`src/nova/limit/placement.py:L18`)
- `nova.conf` — no names imported (`src/nova/limit/placement.py:L20`)
- `nova` — imports `exception` (`src/nova/limit/placement.py:L21`)
- `nova.limit` — imports `utils` as `limit_utils` (`src/nova/limit/placement.py:L22`)
- `nova` — imports `objects` (`src/nova/limit/placement.py:L23`)
- `nova` — imports `quota` (`src/nova/limit/placement.py:L24`)
- `nova.scheduler.client` — imports `report` (`src/nova/limit/placement.py:L25`)
- `nova.scheduler` — imports `utils` (`src/nova/limit/placement.py:L26`)
