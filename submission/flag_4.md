# Flag 4 – Non-Linear Control Transfer Abuse

## Invariant
Authorization logic must follow a linear control path:
request → policy selection → policy evaluation → response.

Non-linear jumps (e.g., longjmp abuse) must not bypass policy checks.

## Telemetry
Control-flow order was validated by:
- Observing mandatory function execution
- Ensuring no skipped policy evaluation steps

## Observation
**Not Observed**

No requests bypassed policy evaluation.
Execution remained sequential and predictable.

## Security Impact
Non-linear control transfers can silently skip authorization logic,
allowing privilege escalation without observable failures.

## Limitations
Does not directly instrument setjmp/longjmp usage.
Detects effects rather than mechanisms.
