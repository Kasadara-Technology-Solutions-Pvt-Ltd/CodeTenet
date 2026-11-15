# Testing, Verification and Evidence Standard

## Default verification sequence
1. Read acceptance criteria and characterize existing behavior.
2. Identify high-risk scenarios: authorization, money/data integrity, concurrency, persistence, compatibility, external I/O and failover.
3. Add targeted unit tests for pure decision logic and regressions; integration tests for meaningful boundaries; E2E for critical workflows.
4. Run available formatter, lint/static checks, build/type checks, focused tests, broader suite and security checks appropriate to impact.
5. Inspect the actual output, diff and telemetry; distinguish passed, failed, skipped and unable-to-run checks.

## Scenario matrix
| Feature area | Minimum questions to test |
|---|---|
| Input processing | valid, missing, malformed, boundary, encoding, oversized, malicious |
| Authentication/authorization | missing identity, incorrect role/scope, object ownership, expired credentials |
| Data mutations | success, duplicate, conflict, rollback, concurrency, transaction failure |
| External calls | timeout, malformed response, rate limit, retry exhaustion, cancellation |
| Scheduled/long-running work | graceful shutdown, resume, duplicate trigger, memory/resource bounds |
| APIs | status/error contract, serialization, version compatibility, pagination |
| Performance | baseline, representative load, latency distribution, resource budget |
| Migrations | old data, rollback/recovery, mixed app versions, index and lock impact |
| Privacy | secrets and PII absent from logs, traces and error responses |

## Testing principles
- Prefer deterministic test fixtures; control time, randomness and external failures.
- Assert observable outcomes, contracts and invariants, not internal call counts unless specifically relevant.
- Reproduce a bug with a regression test when feasible.
- Watch for the pesticide paradox: expand test approaches when defects repeatedly escape.
- High coverage is not proof of correctness (Goodhart's Law). Look for meaningful assertions, mutation/property tests where valuable, and integration evidence.
- Do not claim compilation, test success, security scanning or benchmarks unless performed; explicitly name limitations.

## Evidence ledger template
```markdown
| Check | Command or method | Result | Evidence/notes |
|---|---|---|---|
| Format/lint | [command] | PASS/FAIL/NOT RUN | [summary] |
| Build/types | [command] | PASS/FAIL/NOT RUN | [summary] |
| Unit/integration | [command] | PASS/FAIL/NOT RUN | [counts or blocker] |
| Security | [tool/method] | PASS/FAIL/NOT RUN | [findings] |
| Performance | [benchmark] | PASS/FAIL/NOT RUN | [baseline/delta] |
```
