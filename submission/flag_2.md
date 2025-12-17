# Flag 2 – Return Address Integrity Violation

## Invariant
Functions must return to their legitimate callers without control-flow
redirection or return-oriented manipulation.

## Telemetry
Indirect validation via:
- Observed function entry/exit ordering
- Absence of duplicated or skipped function invocations

Unexpected returns would manifest as missing or reordered telemetry events.

## Observation
**Not Observed**

All intercepted functions returned control to expected callers.
Execution order remained linear and consistent across requests.

## Security Impact
Return address corruption enables ROP-style attacks that preserve output
while fully compromising execution integrity.

## Limitations
Does not provide instruction-level return address validation.
Relies on higher-level control-flow consistency.
