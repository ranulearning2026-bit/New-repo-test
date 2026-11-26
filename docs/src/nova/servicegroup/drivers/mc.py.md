# src/nova/servicegroup/drivers/mc.py

## Overview

This file implements `MemcachedDriver`, a servicegroup driver that uses a Memcached cache as the primary liveness store. It inherits from `base.Driver`. On `join`, it sets up a loopingcall that periodically calls `_report_state`, which writes the current UTC timestamp to Memcached under a key derived from the service's hostname and binary name. `is_up` reads that key and compares the stored timestamp against the configured `down_after_inactive_secs` threshold. `updated_time` returns the Memcached timestamp when present, falling back to the database's `updated_at` field. Lines: total 117, code 70, comment 27, blank 20.

## Defined Symbols

| name | kind | signature | visibility | returns | complexity | lines |
|---|---|---|---|---|---|---|
| `CONF` | constant | — | — | — | — | `src/nova/servicegroup/drivers/mc.py:L32` |
| `LOG` | constant | — | — | — | — | `src/nova/servicegroup/drivers/mc.py:L35` |
| `MemcachedDriver` | class | — | — | — | — | `src/nova/servicegroup/drivers/mc.py:L38–L117` |
| `__init__` | method | `(self, *args, **kwargs)` | — | — | 1/3 | `src/nova/servicegroup/drivers/mc.py:L40–L42` |
| `join` | method | `(self, member_id, group_id, service=None)` | — | — | 3/15 | `src/nova/servicegroup/drivers/mc.py:L44–L60` |
| `is_up` | method | `(self, service_ref)` | — | `is_up` (L71) | 2/6 | `src/nova/servicegroup/drivers/mc.py:L62–L71` |
| `updated_time` | method | `(self, service_ref)` | — | `updated_time_in_mc` (L88), `updated_time_in_db` (L90) | 4/11 | `src/nova/servicegroup/drivers/mc.py:L73–L90` |
| `_report_state` | method | `(self, service)` | — | — | 4/18 | `src/nova/servicegroup/drivers/mc.py:L92–L117` |

## Dependencies

- `datetime` — no names imported (`src/nova/servicegroup/drivers/mc.py:L20`)
- `oslo_log` — imports `log` as `logging` (`src/nova/servicegroup/drivers/mc.py:L22`)
- `oslo_utils` — imports `timeutils` (`src/nova/servicegroup/drivers/mc.py:L23`)
- `nova` — imports `cache_utils` (`src/nova/servicegroup/drivers/mc.py:L25`)
- `nova.conf` — no names imported (`src/nova/servicegroup/drivers/mc.py:L26`)
- `nova.i18n` — imports `_` (`src/nova/servicegroup/drivers/mc.py:L27`)
- `nova.servicegroup` — imports `api` (`src/nova/servicegroup/drivers/mc.py:L28`)
- `nova.servicegroup.drivers` — imports `base` (`src/nova/servicegroup/drivers/mc.py:L29`)
