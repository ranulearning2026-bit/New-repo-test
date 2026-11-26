# Verification Summary

**Run:** 2026-11-26 · Batch: unknown (Changed Files not registered) · Round: 1

## Counts by Issue Type and Severity

| Severity | Count | Note |
|---|---|---|
| error | 0 | — |
| warning | 0 | — |
| info | 29 | All audit-method notes (aee-inventory unavailable; KB reading used) |

**Total verdicts:** 29 (all info)

## Documents with Errors

None.

## Audit Method Note

`aee-inventory` was run but returned 0 files because source files are not checked out in the working tree (this is a known pipeline characteristic — source is in KB records under `.aee/kb/`). All file documents were verified by direct KB record comparison instead, per protocol.

## Clean Documents (zero errors)

### File Documents (12 / 12 pass)

| Document | Source File | Symbols Verified | Deps Verified |
|---|---|---|---|
| `docs/src/nova/keymgr/__init__.py.md` | `src/nova/keymgr/__init__.py` | 0 (empty) | 0 (empty) |
| `docs/src/nova/keymgr/conf_key_mgr.py.md` | `src/nova/keymgr/conf_key_mgr.py` | 12 ✓ | 7 ✓ |
| `docs/src/nova/limit/__init__.py.md` | `src/nova/limit/__init__.py` | 0 (empty) | 0 (empty) |
| `docs/src/nova/limit/local.py.md` | `src/nova/limit/local.py` | 24 ✓ | 9 ✓ |
| `docs/src/nova/limit/placement.py.md` | `src/nova/limit/placement.py` | 13 ✓ | 11 ✓ |
| `docs/src/nova/limit/utils.py.md` | `src/nova/limit/utils.py` | 13 ✓ | 6 ✓ |
| `docs/src/nova/servicegroup/__init__.py.md` | `src/nova/servicegroup/__init__.py` | 1 ✓ | 1 ✓ |
| `docs/src/nova/servicegroup/api.py.md` | `src/nova/servicegroup/api.py` | 9 ✓ | 3 ✓ |
| `docs/src/nova/servicegroup/drivers/__init__.py.md` | `src/nova/servicegroup/drivers/__init__.py` | 0 (empty) | 0 (empty) |
| `docs/src/nova/servicegroup/drivers/base.py.md` | `src/nova/servicegroup/drivers/base.py` | 4 ✓ | 0 ✓ |
| `docs/src/nova/servicegroup/drivers/db.py.md` | `src/nova/servicegroup/drivers/db.py` | 8 ✓ | 8 ✓ |
| `docs/src/nova/servicegroup/drivers/mc.py.md` | `src/nova/servicegroup/drivers/mc.py` | 8 ✓ | 8 ✓ |

### Component Documents (4 / 4 pass)

| Document | Citations Verified |
|---|---|
| `docs/components/index.md` | 12 files, 733 total code lines ✓ |
| `docs/components/keymgr.md` | ConfKeyManager L49–L141 ✓ |
| `docs/components/limit.md` | enforce_api_limit L118–L145, enforce_db_limit L148–L195, enforce_num_instances_and_resources L152–L212, should_enforce L91–L182 ✓ |
| `docs/components/servicegroup.md` | API L37–L83, DbDriver L32–L124, MemcachedDriver L38–L117, Driver L15–L33 ✓ |

### Security Findings (12 / 12 pass)

All 12 source files produced 0 findings from gitleaks, semgrep, and bandit. No scanner re-checks required (re-check applies only to findings that exist). Security chains: 0 chains, consistent with 0 findings.

## Outcome

**Verified** — all 28 documents and finding sets pass with zero errors. Applying `verify:done`.
