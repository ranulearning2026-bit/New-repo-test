# Component Dependency Matrix

> Source: Link Graph `fileEdges` (`.aee/link-graph.json`). Cell values are the sum of `count` over all `fileEdges` with that `(fromComponent, toComponent)` pair.
> Security Chains (`aee/security-chains.json`): 0 chains, 0 confirmed taint hops; no cells are bolded.

## N×N File-Edge Count Matrix

Rows = referencing component, columns = providing component. Diagonal cells are within-component (not counted here).

| From ↓ / To → | keymgr | limit | servicegroup |
|---|---:|---:|---:|
| **keymgr** | — | 0 | 0 |
| **limit** | 0 | — | 0 |
| **servicegroup** | 0 | 0 | — |

All cross-component cells are **0**: no cross-component file edges were found in the link graph. The three components have no statically-detectable import or call dependencies on each other.

> A zero count means no edge was found in the static analysis, not that there is no coupling. Dynamic dispatch, message-bus calls, and RPC are not captured by file-edge analysis.

## Cross-Component Seams

| Component pair | Kind | Literal |
|---|---|---|
| (none) | — | — |

No cross-component seams were recorded in the link graph (Link Summary: 0 seams of all kinds).
