# Code Review and Verification Checklist

Use selectively based on change scope and risk. Do not invent evidence of completed checks.

## Requirements and design
- [ ] Acceptance criteria are implemented without speculative features.
- [ ] Relevant invariants, behavior, and contracts are identified.
- [ ] SRP, DRY, KISS, and YAGNI are balanced pragmatically.
- [ ] Modules have cohesive responsibilities and limited coupling.
- [ ] Existing conventions and compatibility contracts are respected.

## Correctness and security
- [ ] Inputs are validated at trust boundaries.
- [ ] Authorization and least privilege are enforced where applicable.
- [ ] Secrets and private data are not exposed in code or diagnostics.
- [ ] Errors, timeouts, cancellation, and cleanup are handled.
- [ ] Retry, idempotency, consistency, and concurrency risks are reviewed.

## Quality and operations
- [ ] New behavior and regressions have meaningful tests.
- [ ] Build, lint, and tests were run where possible; actual outcomes reported.
- [ ] Performance claims have evidence where material.
- [ ] Observability is useful without exposing sensitive data.
- [ ] Documentation, migration, deployment, and rollback needs are addressed.
- [ ] Unrelated code and unnecessary dependencies were not added.

## Reviewer prompts
1. Is this the smallest correct solution?
2. Which assumptions may be wrong, and how were they verified?
3. Does an abstraction solve known variability or only hypothetical needs?
4. Could an error or duplicate request corrupt state?
5. What might external callers implicitly rely on (Hyrum's Law)?
6. Are metrics measuring outcomes rather than encouraging proxy optimization (Goodhart's Law)?
7. What remains unverified?
