# Dependency Analysis Summary

**Repository:** ranulearning2026-bit/New-repo-test  
**Branch:** agent_workspace  
**Analysis date:** 2026-11-26

## Manifest Inventory

No dependency manifest files (`pom.xml`, `requirements.txt`, `package.json`, `go.mod`) were found anywhere in the repository at any directory depth. The repository contains Nova (Python) source files referenced via KB records (`.aee/kb/`), but no dependency manifests are committed to the repository.

| Manifest | Ecosystem | Component | Dependencies | Unpinned |
|----------|-----------|-----------|-------------|---------|
| *(none)* | — | — | — | — |

## Advisory Matches

No advisory matches — no manifests to scan.

## Unpinned Dependencies

No unpinned dependencies — no manifests found.

## Notes

- **Scanners run:**
  - `osv-scanner` v1.9.2 — completed successfully, found no dependency manifests, results: `[]`
  - `trivy` v0.76.1 — completed successfully, found no dependency manifests, no vulnerabilities reported
- **No manifests found:** The repository (`New-repo-test`, branch `agent_workspace`) contains only pipeline artifacts, KB records, and documentation. No `pom.xml`, `requirements.txt`, `package.json`, or `go.mod` files are present in the working tree or in any git branch. The Nova Python source files are only available as KB records under `.aee/kb/src/nova/` and are not checked out as actual source files in the working tree.
- **Advisory scan status:** Both scanners completed successfully. The empty results accurately reflect zero manifests — this is not a scanner failure.
- **Transitive advisories:** None — scanners reported no packages at all.
