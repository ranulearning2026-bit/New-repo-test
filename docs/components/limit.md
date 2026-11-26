# Component: limit

## Overview

_Purpose not yet written._
4 files (33.3% of 12 source files), 422 code lines (57.6% of 733 total).

## File Inventory

### (top-level)/

| File | Code Lines | Top CCN |
|---|---:|---:|
| `__init__.py` | 0 | — |
| `local.py` | 162 | 7 |
| `placement.py` | 164 | 16 |
| `utils.py` | 96 | 12 |

**Top 5 Functions by CCN**

| Function | Kind | CCN | File | Line Range |
|---|---|---:|---|---|
| `_get_usage` | function | 16 | `placement.py` | L45–L113 |
| `should_enforce` | function | 12 | `utils.py` | L91–L182 |
| `enforce_num_instances_and_resources` | function | 10 | `placement.py` | L152–L212 |
| `_identity_client` | function | 9 | `utils.py` | L52–L88 |
| `enforce_db_limit` | function | 7 | `local.py` | L148–L195 |

## Defined Symbols

Total: 50 (imports not counted)

| Kind | Count |
|---|---:|
| constant | 22 |
| function | 22 |
| field | 3 |
| method | 2 |
| class | 1 |

## External Dependencies

| Package | Kind | Files Importing |
|---|---|---:|
| `oslo_limit` | third-party | 3 |
| `oslo_log` | third-party | 3 |
| `typing` | stdlib | 2 |
| `functools` | stdlib | 1 |
| `openstack` | third-party | 1 |
| `os_resource_classes` | third-party | 1 |

## Side Effects

None recorded. The deterministic Fact Extractor does not extract side effects, so this is not evidence that there are none.

## Component Diagram

```mermaid
graph LR
  h["limit"]
  f1["__init__.py"]
  f2["local.py"]
  f3["placement.py"]
  f4["utils.py"]
  f2 -->|"3"| f4
  f3 -->|"3"| f4
```

## Call Flow

> Static call flow of resolved cross-file calls. Not a data flow: no parameters, no taint, no sanitisation.

### Summary

- Files: 4; symbols in call edges: 5
- Cross-file calls: 4 inside the component, 0 to other components, 0 from other components
- Boundary calls: none

### Entry points

Symbols no other symbol of this component calls (or that other components call).

| Entry | Reaches | Called from other components |
|---|---|---|
| limit/local.py::enforce_api_limit | 2 | 0 |
| limit/placement.py::_get_usage | 1 | 0 |
| limit/placement.py::enforce_num_instances_and_resources | 1 | 0 |

### File-level graph

Dashed border: called from another component. Dotted edge: calls into an external module.

```mermaid
flowchart LR
  n1["limit/local.py"]
  n2["limit/placement.py"]
  n3["limit/utils.py"]
  n1 -->|"2"| n3
  n2 -->|"2"| n3
  classDef entry stroke-width:3px
  classDef exposed stroke-width:3px,stroke-dasharray:2 2
  classDef neighbour stroke-dasharray:4 3
  classDef boundary stroke-dasharray:1 3
```

### Symbol-level graph

Files are boxes; thick border: entry point reaching two or more symbols. Boundary calls are attributed to the file.

```mermaid
flowchart LR
  subgraph f1["limit/local.py"]
    n1["enforce_api_limit"]:::entry
  end
  subgraph f2["limit/placement.py"]
    n2["_get_usage"]
    n3["enforce_num_instances_and_resources"]
  end
  subgraph f3["limit/utils.py"]
    n4["should_enforce"]
    n5["use_unified_limits"]
  end
  n1 --> n4
  n1 --> n5
  n2 --> n5
  n3 --> n4
  classDef entry stroke-width:3px
  classDef exposed stroke-width:3px,stroke-dasharray:2 2
  classDef neighbour stroke-dasharray:4 3
  classDef boundary stroke-dasharray:1 3
```

### Sequences

The 1 entry point(s) reaching the most symbols, depth 3, messages ordered by call-site line.

#### limit/local.py::enforce_api_limit

```mermaid
sequenceDiagram
  participant Caller
  participant P1 as limit/local.py
  participant P2 as limit/utils.py
  Caller->>P1: enforce_api_limit
  P1->>P2: use_unified_limits
  P1->>P2: should_enforce
```

## Cross-Component Interfaces

No cross-component file edges.

No cross-component seams recorded in the link graph.

A missing edge means no edge was found, never that there is no coupling (dynamic dispatch, calls on local variables and generated clients are not seen).
