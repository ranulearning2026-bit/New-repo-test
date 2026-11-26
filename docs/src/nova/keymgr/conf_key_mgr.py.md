# src/nova/keymgr/conf\_key\_mgr.py

## Overview

This file implements `ConfKeyManager`, a key-manager backend that derives a single fixed symmetric AES key from Nova's configuration file rather than delegating to an external key-management service. It inherits from the Castellan `key_manager.KeyManager` interface and provides create, store, get, delete, and consumer-registration operations, all of which either return the same static key ID or raise `Forbidden`/`NotImplementedError` to signal that mutating operations are not supported in this configuration-based backend. Lines: total 141, code 95, comment 14, blank 32.

## Defined Symbols

| name | kind | signature | visibility | returns | complexity | lines |
|---|---|---|---|---|---|---|
| `CONF` | constant | — | — | — | — | `src/nova/keymgr/conf_key_mgr.py:L45` |
| `LOG` | constant | — | — | — | — | `src/nova/keymgr/conf_key_mgr.py:L46` |
| `ConfKeyManager` | class | — | — | — | — | `src/nova/keymgr/conf_key_mgr.py:L49–L141` |
| `__init__` | method | `(self, configuration)` | — | — | 3/10 | `src/nova/keymgr/conf_key_mgr.py:L57–L69` |
| `_get_key` | method | `(self)` | — | `key.SymmetricKey('AES', len(key_bytes) * 8, key_bytes)` (L73) | 1/3 | `src/nova/keymgr/conf_key_mgr.py:L71–L73` |
| `create_key` | method | `(self, context, algorithm, length, **kwargs)` | — | `self.key_id` (L85) | 2/4 | `src/nova/keymgr/conf_key_mgr.py:L75–L85` |
| `create_key_pair` | method | `(self, context, **kwargs)` | — | — | 1/3 | `src/nova/keymgr/conf_key_mgr.py:L87–L89` |
| `store` | method | `(self, context, managed_object, **kwargs)` | — | `self.key_id` (L100) | 3/7 | `src/nova/keymgr/conf_key_mgr.py:L91–L100` |
| `get` | method | `(self, context, managed_object_id)` | — | `self._get_key()` (L115) | 3/6 | `src/nova/keymgr/conf_key_mgr.py:L102–L115` |
| `delete` | method | `(self, context, managed_object_id)` | — | — | 3/7 | `src/nova/keymgr/conf_key_mgr.py:L117–L131` |
| `add_consumer` | method | `(self, context, managed_object_id, consumer_data)` | — | — | 1/4 | `src/nova/keymgr/conf_key_mgr.py:L133–L136` |
| `remove_consumer` | method | `(self, context, managed_object_id, consumer_data)` | — | — | 1/4 | `src/nova/keymgr/conf_key_mgr.py:L138–L141` |

## Dependencies

- `binascii` — no names imported (`src/nova/keymgr/conf_key_mgr.py:L34`)
- `castellan.common.objects` — imports `symmetric_key` as `key` (`src/nova/keymgr/conf_key_mgr.py:L36`)
- `castellan.key_manager` — imports `key_manager` (`src/nova/keymgr/conf_key_mgr.py:L37`)
- `oslo_log` — imports `log` as `logging` (`src/nova/keymgr/conf_key_mgr.py:L38`)
- `nova.conf` — no names imported (`src/nova/keymgr/conf_key_mgr.py:L40`)
- `nova` — imports `exception` (`src/nova/keymgr/conf_key_mgr.py:L41`)
- `nova.i18n` — imports `_` (`src/nova/keymgr/conf_key_mgr.py:L42`)
