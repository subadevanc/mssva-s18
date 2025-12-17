# MSSVA-S18: Binary Integrity & Control-Flow Telemetry

## Overview

This submission evaluates the runtime execution integrity of the
`authz_bridge` authorization service using **user-space telemetry only**.

The binary on disk is assumed trusted and produces correct output.
The goal is to determine whether execution at runtime can still be trusted
under a stealthy attacker capable of influencing memory or control flow.

No source modification, recompilation, kernel instrumentation, or crash-based
signals were used.

---

## Telemetry Approach Summary

Telemetry was implemented using **LD_PRELOAD-based runtime interception**
to observe execution of security-critical functions:

- `get_policy`
- `default_policy`
- `audit_policy`

This allowed validation of:
- Control-flow order
- Runtime function resolution
- Policy handler integrity
- Absence of hidden execution paths

---

## Flag Summary

| Flag | Description                                   | Status        |
|------|-----------------------------------------------|---------------|
| Flag 1 | Unauthorized Policy Handler Execution       | Not Observed  |
| Flag 2 | Return Address Integrity Violation           | Not Observed  |
| Flag 3 | Runtime Function Resolution Tampering        | Not Observed  |
| Flag 4 | Non-Linear Control Transfer Abuse            | Not Observed  |
| Flag 5 | Unobserved Execution Path Activation         | Not Observed  |

Each flag is documented individually with invariants, telemetry, and impact.
