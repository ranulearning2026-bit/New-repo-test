# Security Chains Summary

Generated: 2026-11-26T11:36:34Z

## Overview

No cross-file vulnerability chains were identified.

All 12 source files (across `nova/keymgr`, `nova/limit`, and `nova/servicegroup`) produced **zero security findings** from the full scanner suite (gitleaks, semgrep, bandit). With no taint sources, no chain tracing was possible.

## Chain Counts

| Status | Count |
|---|---|
| Confirmed chains | 0 |
| Partial chains | 0 |
| Terminated chains (sanitised) | 0 |

## Confirmed Chains by Severity

_None._

## Partial Chains

_None._

## Coverage Note

The security scanner suite (gitleaks, semgrep, bandit) completed on all 12 files. `candidates.json` has zero candidates and `coverage.json` reports no sink or surface gaps. No cross-file correlation work is actionable for this pipeline run.
