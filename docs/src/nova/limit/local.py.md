# src/nova/limit/local.py

## Overview

This file implements Nova's local (non-placement) resource-limit enforcement layer. It defines two sets of limit identifiers — API-level limits (server metadata items, injected files, key pairs, server groups, server group members) and DB-level limits — and provides functions to check usage, enforce limits via the oslo.limit `Enforcer`, and translate between internal resource names and the legacy quota API names. `enforce_api_limit` guards stateless counts checked in the API layer; `enforce_db_limit` guards database-backed resources such as key pairs and server groups, using per-entity callback functions collected in `DB_COUNT_FUNCTION`. Lines: total 236, code 162, comment 33, blank 41.

## Defined Symbols

| name | kind | signature | visibility | returns | complexity | lines |
|---|---|---|---|---|---|---|
| `LOG` | constant | — | — | — | — | `src/nova/limit/local.py:L27` |
| `CONF` | constant | — | — | — | — | `src/nova/limit/local.py:L28` |
| `SERVER_METADATA_ITEMS` | constant | — | — | — | — | `src/nova/limit/local.py:L32` |
| `INJECTED_FILES` | constant | — | — | — | — | `src/nova/limit/local.py:L33` |
| `INJECTED_FILES_CONTENT` | constant | — | — | — | — | `src/nova/limit/local.py:L34` |
| `INJECTED_FILES_PATH` | constant | — | — | — | — | `src/nova/limit/local.py:L35` |
| `API_LIMITS` | constant | — | — | — | — | `src/nova/limit/local.py:L36–L41` |
| `KEY_PAIRS` | constant | — | — | — | — | `src/nova/limit/local.py:L45` |
| `SERVER_GROUPS` | constant | — | — | — | — | `src/nova/limit/local.py:L46` |
| `SERVER_GROUP_MEMBERS` | constant | — | — | — | — | `src/nova/limit/local.py:L47` |
| `DB_LIMITS` | constant | — | — | — | — | `src/nova/limit/local.py:L48–L52` |
| `UNIFIED_LIMITS_DRIVER` | constant | — | — | — | — | `src/nova/limit/local.py:L55` |
| `EXCEPTIONS` | constant | — | — | — | — | `src/nova/limit/local.py:L60–L68` |
| `LEGACY_LIMITS` | constant | — | — | — | — | `src/nova/limit/local.py:L71–L79` |
| `get_in_use` | function | `(context: 'nova.context.RequestContext', project_id: str) -> dict[str, int]` | — | `_convert_keys_to_legacy_name(usages)` (L106) | 1/14 | `src/nova/limit/local.py:L82–L106` |
| `always_zero_usage` | function | `(project_id: str, resource_names: list[str]) -> dict[str, int]` | — | `{resource_name: 0 for resource_name in resource_names}` (L115) | 2/4 | `src/nova/limit/local.py:L109–L115` |
| `enforce_api_limit` | function | `(entity_type: str, count: int) -> None` | — | (L125) | 6/18 | `src/nova/limit/local.py:L118–L145` |
| `enforce_db_limit` | function | `(context: 'nova.context.RequestContext', entity_type: str, entity_scope: ty.Any, delta: int) -> None` | — | (L170) | 7/27 | `src/nova/limit/local.py:L148–L195` |
| `_convert_keys_to_legacy_name` | function | `(new_dict: dict[str, int]) -> dict[str, int]` | — | `legacy` (L205) | 3/7 | `src/nova/limit/local.py:L198–L205` |
| `get_legacy_default_limits` | function | `() -> dict[str, int]` | — | `_convert_keys_to_legacy_name(dict(new_limits))` (L212) | 1/4 | `src/nova/limit/local.py:L208–L212` |
| `_keypair_count` | function | `(context, user_id, *args)` | — | `{'server_key_pairs': count}` (L217) | 1/3 | `src/nova/limit/local.py:L215–L217` |
| `_server_group_count` | function | `(context, project_id, *args)` | — | `{'server_groups': raw_counts['project']['server_groups']}` (L222) | 1/3 | `src/nova/limit/local.py:L220–L222` |
| `_server_group_members_count` | function | `(context, server_group_uuid, *args)` | — | `{'server_group_members': len(server_group.members)}` (L229) | 1/4 | `src/nova/limit/local.py:L225–L229` |
| `DB_COUNT_FUNCTION` | constant | — | — | — | — | `src/nova/limit/local.py:L232–L236` |

## Dependencies

- `functools` — no names imported (`src/nova/limit/local.py:L15`)
- `typing` as `ty` — no names imported (`src/nova/limit/local.py:L16`)
- `oslo_limit` — imports `exception` as `limit_exceptions` (`src/nova/limit/local.py:L18`)
- `oslo_limit` — imports `limit` (`src/nova/limit/local.py:L19`)
- `oslo_log` — imports `log` as `logging` (`src/nova/limit/local.py:L20`)
- `nova.conf` — no names imported (`src/nova/limit/local.py:L22`)
- `nova` — imports `exception` (`src/nova/limit/local.py:L23`)
- `nova.limit` — imports `utils` as `nova_limit_utils` (`src/nova/limit/local.py:L24`)
- `nova` — imports `objects` (`src/nova/limit/local.py:L25`)
