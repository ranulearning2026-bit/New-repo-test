# src/nova/servicegroup/drivers/base.py

## Overview

This file defines `Driver`, the abstract base class for Nova servicegroup driver implementations. It declares three abstract methods — `join`, `is_up`, and `updated_time` — each of which raises `NotImplementedError`, requiring concrete subclasses to supply working implementations. Lines: total 33, code 15, comment 12, blank 6.

## Defined Symbols

| name | kind | signature | visibility | returns | complexity | lines |
|---|---|---|---|---|---|---|
| `Driver` | class | — | — | — | — | `src/nova/servicegroup/drivers/base.py:L15–L33` |
| `join` | method | `(self, member, group, service=None)` | — | — | 1/2 | `src/nova/servicegroup/drivers/base.py:L18–L25` |
| `is_up` | method | `(self, member)` | — | — | 1/2 | `src/nova/servicegroup/drivers/base.py:L27–L29` |
| `updated_time` | method | `(self, service_ref)` | — | — | 1/2 | `src/nova/servicegroup/drivers/base.py:L31–L33` |

## Dependencies

None.
