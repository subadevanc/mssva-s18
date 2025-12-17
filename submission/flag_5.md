# Flag 5 – Unobserved Execution Path Activation

## Invariant
All execution paths leading to authorization decisions must be observable
via telemetry.

No hidden or dormant paths may influence decisions.

## Telemetry
Telemetry covered all known policy handlers and dispatch logic.
No authorization decisions occurred without corresponding telemetry.

## Observation
**Not Observed**

Every decision was preceded by visible policy execution.
No silent or hidden execution paths were detected.

## Security Impact
Hidden execution paths allow attackers to inject logic that produces
valid outputs while evading detection and auditing.

## Limitations
Only validates known entry points.
Completely novel logic injected outside observed paths may evade detection.
