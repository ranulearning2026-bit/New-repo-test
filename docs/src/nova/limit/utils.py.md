# src/nova/limit/utils.py

## Overview

This file provides shared utilities for Nova's unified-limits enforcement layer. It exposes a `use_unified_limits()` predicate that checks whether the configured quota driver is the unified-limits backend, an `IdentityClient` dataclass-style wrapper around the OpenStack SDK identity connection (used to retrieve registered limits from Keystone), a lazy `_identity_client()` factory that builds and caches the `IdentityClient` singleton, and a `should_enforce()` function that inspects a `ProjectOverLimit` exception to determine whether the offending resource limits are real hard limits (versus soft limits or unconfigured resources) and returns a boolean accordingly. Lines: total 182, code 96, comment 61, blank 25.

## Defined Symbols

| name | kind | signature | visibility | returns | complexity | lines |
|---|---|---|---|---|---|---|
| `LOG` | constant | — | — | — | — | `src/nova/limit/utils.py:L26` |
| `CONF` | constant | — | — | — | — | `src/nova/limit/utils.py:L27` |
| `UNIFIED_LIMITS_DRIVER` | constant | — | — | — | — | `src/nova/limit/utils.py:L29` |
| `IDENTITY_CLIENT` | constant | — | — | — | — | `src/nova/limit/utils.py:L30` |
| `use_unified_limits` | function | `()` | — | `CONF.quota.driver == UNIFIED_LIMITS_DRIVER` (L34) | 1/2 | `src/nova/limit/utils.py:L33–L34` |
| `IdentityClient` | class | — | — | — | — | `src/nova/limit/utils.py:L37–L49` |
| `connection` | field | — | — | — | — | `src/nova/limit/utils.py:L38` |
| `service_id` | field | — | — | — | — | `src/nova/limit/utils.py:L39` |
| `region_id` | field | — | — | — | — | `src/nova/limit/utils.py:L40` |
| `__init__` | method | `(self, connection, service_id, region_id)` | — | — | 1/4 | `src/nova/limit/utils.py:L42–L45` |
| `registered_limits` | method | `(self)` | — | `list(self.connection.registered_limits(service_id=self.service_id, region_id=self.region_id))` (L48) | 1/3 | `src/nova/limit/utils.py:L47–L49` |
| `_identity_client` | function | `()` | — | `IDENTITY_CLIENT` (L88) | 9/31 | `src/nova/limit/utils.py:L52–L88` |
| `should_enforce` | function | `(exc: limit_exceptions.ProjectOverLimit) -> bool` | — | `True` (L107), `False` (L125), `True` (L153), `bool(enforced)` (L182) | 12/33 | `src/nova/limit/utils.py:L91–L182` |

## Dependencies

- `typing` as `ty` — no names imported (`src/nova/limit/utils.py:L15`)
- `openstack` — imports `proxy` (`src/nova/limit/utils.py:L18`)
- `oslo_limit` — imports `exception` as `limit_exceptions` (`src/nova/limit/utils.py:L20`)
- `oslo_log` — imports `log` as `logging` (`src/nova/limit/utils.py:L21`)
- `nova.conf` — no names imported (`src/nova/limit/utils.py:L23`)
- `nova` — imports `utils` as `nova_utils` (`src/nova/limit/utils.py:L24`)
