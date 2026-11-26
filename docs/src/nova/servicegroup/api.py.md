# src/nova/servicegroup/api.py

## Overview

This file implements the `API` class, the public facade for Nova's service-group subsystem. On construction it dynamically loads the configured servicegroup driver (selected by name from a lookup table of driver class strings via `oslo_utils.importutils`) and stores it as `self._driver`. It exposes three operations — `join` (register a member in a group), `service_is_up` (check whether a service is considered live), and `get_updated_time` (retrieve the last heartbeat timestamp) — each of which delegates to the loaded driver. Lines: total 83, code 47, comment 19, blank 17.

## Defined Symbols

| name | kind | signature | visibility | returns | complexity | lines |
|---|---|---|---|---|---|---|
| `LOG` | constant | — | — | — | — | `src/nova/servicegroup/api.py:L24` |
| `_driver_name_class_mapping` | variable | — | — | — | — | `src/nova/servicegroup/api.py:L26–L29` |
| `CONF` | constant | — | — | — | — | `src/nova/servicegroup/api.py:L31` |
| `INITIAL_REPORTING_DELAY` | constant | — | — | — | — | `src/nova/servicegroup/api.py:L34` |
| `API` | class | — | — | — | — | `src/nova/servicegroup/api.py:L37–L83` |
| `__init__` | method | `(self, *args, **kwargs)` | — | — | 2/16 | `src/nova/servicegroup/api.py:L39–L61` |
| `join` | method | `(self, member, group, service=None)` | — | `self._driver.join(member, group, service)` (L70) | 1/2 | `src/nova/servicegroup/api.py:L63–L70` |
| `service_is_up` | method | `(self, member)` | — | `False` (L77), `self._driver.is_up(member)` (L79) | 2/4 | `src/nova/servicegroup/api.py:L72–L79` |
| `get_updated_time` | method | `(self, member)` | — | `self._driver.updated_time(member)` (L83) | 1/2 | `src/nova/servicegroup/api.py:L81–L83` |

## Dependencies

- `oslo_log` — imports `log` as `logging` (`src/nova/servicegroup/api.py:L19`)
- `oslo_utils` — imports `importutils` (`src/nova/servicegroup/api.py:L20`)
- `nova.conf` — no names imported (`src/nova/servicegroup/api.py:L22`)
