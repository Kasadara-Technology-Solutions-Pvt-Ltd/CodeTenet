# Scenario Playbooks — Applying the Skill

These are patterns for agent reasoning, **not** commands to add framework layers. Each scenario includes what to inspect, what to implement, and how to verify.

## 1. New business feature
**Situation:** Add discount eligibility to an order service.
- Inspect existing price/eligibility policies and acceptance criteria; identify one authoritative business rule (DRY).
- Introduce a focused pure calculation/policy, not a rules engine with hypothetical extension points (KISS/YAGNI).
- Enforce authorization and data consistency at real boundaries.
- Verify eligible/ineligible, thresholds, missing data, policy version and regression behavior.
**Avoid:** duplicating discounts in API, UI and background worker.

## 2. Fix a production bug
**Situation:** A double-submit creates duplicate invoices.
- Reproduce with a test; inspect retries, unique keys and transaction behavior (Murphy's Law).
- Fix with a suitable durable idempotency key/constraint and transaction contract.
- Verify concurrent duplicates, retried requests, partial failures and audit outcomes.
**Avoid:** masking the symptom by disabling the button only.

## 3. Refactor legacy code safely
**Situation:** A 1,000-line service is difficult to maintain.
- Characterize current observable behavior and external callers (Hyrum's Law).
- Extract cohesive responsibilities incrementally; keep behavior and API stable (Gall's Law).
- Introduce justifiable seams; measure churn and run regression tests after each slice.
**Avoid:** replacing the entire module with a speculative plugin framework.

## 4. Design a REST API
**Situation:** Create a CRUD API for client accounts.
- Define request/response schemas, validation, error semantics, pagination and authorization.
- Separate external DTOs from persistence representation where contracts may evolve.
- Protect database invariants and ensure sensitive diagnostics are redacted.
- Test 401/403, 404/409, invalid payloads, concurrent updates and contract compatibility.
**Avoid:** binding untrusted external input directly to database entities without control.

## 5. Build a reusable library
**Situation:** Publish a zero-dependency TypeScript utility package.
- Define small stable exports, platform support, versioning and behavior for null/invalid inputs.
- Prefer native standard library APIs; add generic abstractions only with real use cases.
- Test varied primitive/object collections, boundary cases, immutable semantics and packaging/type declarations.
- Check tree-shaking/runtime compatibility and published artifacts, not just development tests.
**Avoid:** introducing framework-specific dependencies into a framework-neutral core.

## 6. Integrate a message broker and database
**Situation:** A worker consumes events and writes records.
- Define at-least-once delivery expectations, durable identity, ordering, partition failure and retry limits (distributed computing fallacies).
- Make effects idempotent and preserve transaction boundaries; specify poison-message handling.
- Test duplicate delivery, crash after commit, broker timeout and reprocessing.
**Avoid:** promising exactly-once outcomes without examining both broker and business side effects.

## 7. Database schema migration
**Situation:** Add a mandatory field to an existing high-volume table.
- Inspect current data and mixed-version application compatibility (Hyrum's Law).
- Plan expand/backfill/validate/contract steps, indexing/locking and recovery.
- Verify legacy rows, new writes during rollout and rerun safety.
**Avoid:** one destructive migration that fails on existing null rows.

## 8. Security hardening
**Situation:** A user can read another tenant's report by guessing an ID.
- Map the authorization boundary and resource ownership; test denied access and logging.
- Enforce tenant/resource authorization server-side and minimize disclosure.
- Test direct-object access, privilege escalation and cross-tenant caching.
**Avoid:** hiding the report link only in the UI.

## 9. Performance regression
**Situation:** Search response times increased after a release.
- Establish a baseline and inspect query plans, allocations and upstream latency.
- Identify true bottleneck before caching/parallelism (Amdahl's Law, premature optimization).
- Compare realistic load, median/tail latency, resource usage and correctness.
**Avoid:** rewriting the search subsystem with speculative caches before profiling.

## 10. Long-running background service
**Situation:** A Windows/Linux worker must run indefinitely.
- Inspect lifetime, cancellation, exception policy, connection disposal, queue growth and restart semantics.
- Use bounded work and safe shutdown; protect against duplicate triggers and stale leases.
- Test fault/retry paths, memory stability and graceful stop.
**Avoid:** an infinite loop without cancellation, backpressure or error strategy.

## 11. Architectural review
**Situation:** Team proposes replacing a monolith with microservices.
- Identify deployment, ownership and scaling requirements; test concrete pain points (Conway's Law).
- Compare modular monolith, selective service extraction and full decomposition.
- Record ADR with operational cost, network failure modes and migration plan (Gall's Law, leaky abstractions).
**Avoid:** treating microservices as a default maturity badge.

## 12. Pull request review / AI code evaluation
**Situation:** Review a generated feature with tests reportedly passing.
- Inspect real diff, acceptance criteria, risk boundaries and changed contracts.
- Independently run relevant tests when possible; verify claimed outcomes and look for missing negative tests.
- Report severity, file/line evidence, suggested fix and unverified claims (Goodhart's Law).
**Avoid:** approving due solely to formatting, high coverage or confident prose.
