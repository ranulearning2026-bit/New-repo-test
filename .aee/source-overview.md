Batch: 76db4114ac412837a25751b066b165cd1308d439
Updated: 2026-11-26T09:45:45Z
Source folder: src/nova/

## Totals

| Metric | Value |
|--------|------:|
| Tracked files | 12 |
| Source files (extractable) | 12 |
| OTHER files | 0 |
| UNKNOWN files | 0 |
| Total code lines (source) | 752 |
| Total comment lines (source) | 245 |
| Total blank lines (source) | 182 |
| Source files without `loc` | 0 |
| Change (files) vs. prev batch | +12 |
| Change (code lines) vs. prev batch | +752 |

## Lines of Code by Language

| Language | Files | Code | Comments | Blanks | % of Code |
|----------|------:|-----:|---------:|-------:|----------:|
| Python | 12 | 752 | 245 | 182 | 100.0% |
| **Total** | **12** | **752** | **245** | **182** | **100%** |

## Lines of Code by Component

| Component | Files | Code | Comments | Blanks | % of Code |
|-----------|------:|-----:|---------:|-------:|----------:|
| limit | 4 | 432 | 127 | 98 | 57.4% |
| servicegroup | 6 | 220 | 104 | 57 | 29.3% |
| keymgr | 2 | 100 | 14 | 27 | 13.3% |
| **Total** | **12** | **752** | **245** | **182** | **100%** |

### Code Lines per Language by Component

| Component | Python |
|-----------|-------:|
| limit | 432 |
| servicegroup | 220 |
| keymgr | 100 |

## Folder Structure

Source files only, two directory levels below `src/nova/`.

```
src/nova/
  keymgr/  100 lines, 2 files
    (top-level modules)  100 lines, 2 files
  limit/  432 lines, 4 files
    (top-level modules)  432 lines, 4 files
  servicegroup/  220 lines, 6 files
    (top-level modules)  55 lines, 2 files
    drivers/  165 lines, 4 files
```

## Growth History

| Batch | Date | Source Files | Code Lines | Change |
|-------|------|-------------:|-----------:|-------:|
| 76db4114 | 2026-11-26 | 12 | 752 | +752 |

## Notes

- **LOC** figures come from tokei output stored in the `loc` field of `.aee/intake.jsonl`. Source files without a `loc` entry are counted in file totals but excluded from all line counts.
- **Components** come from `.aee/components.json`.
