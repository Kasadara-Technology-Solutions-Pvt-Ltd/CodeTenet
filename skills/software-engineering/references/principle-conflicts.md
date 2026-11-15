# Engineering Principle Conflict Playbook

Every principle is contextual; explain the trade-off rather than maximizing adherence to an acronym.

## DRY vs. independent evolution
Two address validators look identical today but have independent policies in shipping and customer identity. **Keep them separate** unless the shared rule is authoritative and guaranteed to co-evolve. Extract shared low-level primitives if useful.

## Open/Closed vs. YAGNI
Only one payment provider exists, with no planned variants. **Do not** build a generic provider registry now. If multiple approved providers have truly different implementations, add an interface at their real boundary.

## KISS vs. reliability
The simplest-looking `try { send(); } catch {}` is not simple operationally. Prefer explicit timeout, safe error handling and necessary duplicate protection without adding speculative event buses.

## Inheritance vs. composition
Multiple implementations share logging and timeout behavior but not a common behavioral subtype. Prefer wrapping/composition; inherit only when substitution guarantees hold.

## Hyrum's Law vs. necessary contract changes
A response field has historically accepted `null`. Before making it required, characterize consumers, introduce a version or compatibility migration, and communicate the break.

## Security vs. Postel's Law
Be generous with documented, harmless formatting flexibility; never accept ambiguous security-sensitive identity claims, untrusted SQL/HTML or unspecified authentication bypasses.

## Performance vs. readability
Keep a clear straightforward implementation until profiling shows a critical bottleneck. Add optimization behind tests with before/after measurements and explanation of complexity.

## Boy Scout Rule vs. scoped delivery
Fix nearby misleading variable names or obvious dead code while editing. Track major architectural cleanup separately unless it blocks correctness.

## Goodhart's Law vs. coverage gates
Use coverage as a diagnostic, not a target to game. A meaningful integration test for an authorization boundary may matter more than another hundred trivial line-coverage tests.

## Gall's Law vs. enterprise requirements
Build a small **compliant** vertical slice with security and integrity; defer future features, not required safety mechanisms.
