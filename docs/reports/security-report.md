# Security Report

| Field | Value |
|---|---|
| Batch | `76db411` |
| Commit | `76db4114ac412837a25751b066b165cd1308d439` |
| Branch | `agent_workspace` |
| Generated | 2026-11-26T12:05:17Z |
| Layout | inline (0 findings) |
| Verification | passed |
| Sources | Security Log, Security Chains, Security Chains Summary, Verification Summary, Verification Report, Changed Files, Dependency Advisories, Dependency Inventory, License Inventory, Infrastructure Findings |

Batch `76db411` · sources: Security Log, Security Chains, Verification Summary, Verification Report

---

## 1. Executive Summary

| Metric | Value |
|---|---|
| Files analysed | 12 (3 empty) |
| Files with findings | 0 |
| Total findings | 0 |
| Critical | 0 |
| High | 0 |
| Medium | 0 |
| Low | 0 |
| Informational | 0 |
| Confirmed confidence | 0 |
| Findings by agent analysis (manual) | 0 |
| Findings by gitleaks | 0 |
| Findings by semgrep | 0 |
| Findings by bandit | 0 |
| Verified | 0 |
| Flagged | 0 |
| Disputed | 0 |
| Chains confirmed | 0 |
| Chains partial | 0 |
| Chains terminated | 0 |
| Verification result | passed (0 errors, 0 warnings, 0 info) |

0 findings, shown inline.

12 files were analysed across 3 components (keymgr, limit, servicegroup); 3 were empty Python package initialisers (`__init__.py`). All three scanners (gitleaks, semgrep, bandit) ran on all 12 files and produced zero findings. No manual findings were submitted. There is no dominant OWASP category and no confirmed chain exists.

**Key results:** No critical or high findings.

---

## 2. Scope and Method

| Item | Detail |
|---|---|
| Analysis kind | Static only |
| gitleaks | 12 files |
| semgrep | 12 files |
| bandit | 12 files |
| Manual review | 0 findings |
| Coverage | 12 / 12 files (100%) |
| Files skipped (content changed) | 0 |
| Scanner failures | None |

Scanner versions: bandit 1.9.4, gitleaks 8.21.2, semgrep 1.186.0. All scanners completed without error.

### Pipeline Roles

| Role | State | Outputs | Problems |
|---|---|---|---|
| Repo Checker | ran | Changed Files (12 files, 0 skipped) | - |
| Security Analyzer | ran | Security Log, 12 findings files (0 with findings) | - |
| Cross-File Security Correlator | ran | Security Chains, Security Chains Summary | - |
| Verifier Critic | ran | Verification Summary, Verification Report (0 verdicts) | - |

---

## 3. Findings

No security findings were identified in this batch. All 12 files (9 with code, 3 empty initialisers) were analysed by gitleaks, semgrep and bandit. Zero candidates were raised by any scanner or by manual review.

**Languages analysed:** Python  
**Files with code:** 9 (keymgr: 1, limit: 3, servicegroup: 5)  
**Empty files:** 3 (`src/nova/keymgr/__init__.py`, `src/nova/limit/__init__.py`, `src/nova/servicegroup/drivers/__init__.py`)  
**Code lines analysed:** 752

| ID | Severity | Confidence | Component | File | Lines | OWASP | CWE | Tools | Verification | Title |
|---|---|---|---|---|---|---|---|---|---|---|
| *(none)* | | | | | | | | | | |

### 3.x Findings by Class

No findings — no OWASP categories or CWEs present.

### 3.y Remediation by Class

No findings — no CWEs to address. The guidance below is generic and taken from the pipeline remediation reference; it is not specific to this codebase.

No CWE-specific guidance applies to this batch.

---

## 4. Taint Chains

**Confirmed chains:** None.

**Partial chains:** None.

**Terminated chains:** None.

No taint sources were identified (zero findings), so no chain tracing was performed.

**Evaluated findings (excluded taint sources):**

| File | Lines | Confidence | Disposition | Reason |
|---|---|---|---|---|
| *(none)* | | | | |

---

## 5. Component View

No component has findings. All 3 components (keymgr, limit, servicegroup) are clean.

| Component | Files | Code lines | Findings | Chains |
|---|---|---|---|---|
| keymgr | 2 | 100 | 0 | 0 |
| limit | 4 | 432 | 0 | 0 |
| servicegroup | 6 | 220 | 0 | 0 |

3 components have no findings; none had a file missing from the batch (all 12 files were analysed).

**Trust boundaries:** No confirmed or partial chains cross component boundaries. 0 cross-component seams were identified in the Link Graph (21 unresolved imports remain from external/standard-library references, which is expected for Python application code).

---

## 6. Supply Chain and Infrastructure

### Dependency Advisories

Artifact **Dependency Advisories** resolved. 0 records. Scanned by osv-scanner v1.9.2 and trivy v0.76.1. No dependency manifest files (`pom.xml`, `requirements.txt`, `package.json`, `go.mod`) were found in the repository; the Nova source is not committed as actual files, only as KB records.

| Package | Ecosystem | Severity | CVE | Description |
|---|---|---|---|---|
| *(none)* | | | | |

### Dependency Inventory

Artifact **Dependency Inventory** resolved. 0 records. No manifests found; nothing to inventory.

### License Inventory

Artifact **License Inventory** resolved. 0 records. No `LICENSE*` or `NOTICE*` files and no bundled third-party components were detected. `productLicense` is `null`. Trivy v0.76.1 scanned the repository root; source files are not checked out in the working tree.

| Component | License | Conflict | Attribution Gap |
|---|---|---|---|
| *(none)* | | | |

### Infrastructure Findings

Artifact **Infrastructure Findings** resolved. 0 records. No infrastructure-as-code files (Dockerfiles, Terraform, Kubernetes manifests) are present in this repository. All infrastructure scanners (checkov, trivy, gitleaks) targeted `/src`, which does not exist in the working tree; hadolint was not run (no Dockerfiles found).

| File | Severity | Rule | Description |
|---|---|---|---|
| *(none)* | | | |

---

## 7. Limitations and Unresolved Items

**Static-analysis blind spots** (from Security Chains Summary): With zero findings, no chain tracing was possible. The scanner suite (gitleaks, semgrep, bandit) performs static analysis only; runtime behaviour, dynamic taint paths, and authentication/authorisation logic are not covered.

**Coverage gap:** 0 files were left unanalysed. All 12 files in the batch were processed by all three scanners.

**Unresolved imports (Link Graph):** 21 unresolved import references. These are expected for Python standard-library and external package imports that are not checked out in the working tree. No internal cross-component seams were missed by this.

**Findings with `needs_cross_file` confidence:** 0 (no findings at all).

**Verification errors:** None. The Verification Report contains 0 entries; no finding or chain was disputed.

**Verification warnings:** None.

---

*(Section 8 — Evidence and traceability — is omitted: no findings to trace.)*
