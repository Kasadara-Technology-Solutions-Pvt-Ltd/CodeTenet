# Detailed Enterprise Programming Standards

> This document complements `../SKILL.md`. Apply requirements proportionately to the risk and the actual repository. **MUST** is a default production requirement, **SHOULD** is recommended; record justified deviations.

## 1. Language and repository conventions
- Follow established naming, layout, formatting, import organization and lint/type-check rules. Prefer standard idioms over creating a parallel house style.
- Use explicit, meaningful names that communicate domain intent, type, scope and units (`timeoutSeconds`, not `timeout`). Distinguish commands, queries, pure computations, and mutating operations.
- Use narrow modules with cohesive responsibilities; keep public APIs intentional. Avoid arbitrary maximum lines/functions per class and blanket interface-per-class policies.
- Make side effects, mutability, ownership, nullable values, exceptions and asynchronous behavior evident in contracts.
- Preserve existing wire formats and source/binary compatibility where promised. Use semantic versioning or an explicit compatibility strategy when needed.
- No hidden globals, magic service locators, surprising implicit I/O or undocumented thread affinity.

## 2. Functions and types
- One cohesive task per function; use early returns to manage complexity without concealing required work.
- Validate untrusted boundary inputs, then rely on explicitly enforced internal invariants. Avoid redundant validation at every internal layer.
- Model domain concepts with types that prevent invalid states where practical; avoid object bags and ambiguous string/number identifiers when mistakes matter.
- Choose a return/error strategy consistently (exceptions versus result values); do not mix silent `null`, fabricated success and thrown errors unpredictably.
- Keep parameters intelligible; group genuinely related values into a value object, not a generic options bucket with unrelated settings.
- Use pure functions for transformations whenever feasible; make I/O orchestration separate from core decisions.

## 3. Readability, comments, documentation
- Favor simple control flow, predictable defaults and explicit intent over clever compact syntax.
- Comments should explain why, subtle invariants, external constraints, security reasoning and nonobvious workarounds; remove stale explanations.
- Document public contracts, expected errors, thread-safety constraints, configuration, migrations and operational impacts where relevant.
- Do not duplicate implementation details in documentation that will quickly drift; link to authoritative schemas or generated interface docs where appropriate.

## 4. Dependencies and abstractions
- Prefer platform capabilities and already approved libraries when fit for purpose. Evaluate licenses, supply-chain security, maintenance, runtime cost and size for additions.
- An interface or design pattern needs actual variation, a boundary, contract value, or a testability benefit-not merely a SOLID label.
- Deduplicate shared business *knowledge*. Do not couple unrelated features solely to remove repeated syntax.
- Favor composition for reusable behavior; inheritance only when the subtype truly honors base-class contracts.
- Avoid speculative plugin systems, broad configuration matrices and placeholder extension points.

## 5. Validation, error handling and resilience
- Define success, invalid request, authorization failure, dependency failure, timeout, cancellation, duplicate, conflict and partial failure semantics as relevant.
- Validate data at trust boundaries. Use structured, sanitized external error messages and preserve safe internal diagnostic context.
- Never swallow errors or log-and-continue after compromised state. Catch exceptions where they can be meaningfully mapped, recovered, or enriched.
- Use bounded retries with backoff/jitter only for transient faults; combine with timeouts, cancellation and idempotency where side effects occur.
- Explicitly own and dispose resources, handles, connections, subscriptions, buffers and locks; support graceful shutdown in workers.
- Avoid unsupported assumptions about encoding, integer overflow, floating-point precision, currency, clock, timezone and culture.

## 6. APIs and integration contracts
- Specify request and response shapes, validation, allowed transitions, error codes, authorization and compatibility/versioning rules.
- Do not expose persistence models as public wire contracts by accident. Prefer explicit DTO or schema mappings where external evolution matters.
- Define pagination limits, filtering/sorting semantics, concurrency tokens, partial updates and idempotency keys when relevant.
- Do not assume networks are instant, reliable or secure; implement defensive timeouts, retries, rate limiting and observable errors.
- Treat duplicate deliveries, reordering, eventual consistency, partial writes and clock skew explicitly in distributed integrations.

## 7. Database and transaction rules
- Enforce meaningful uniqueness, foreign keys, checks, constraints and transactional invariants in the right storage layer.
- Specify isolation/locking assumptions, conflict detection, transaction scope and retry behavior where correctness depends on them.
- Ensure migrations are reviewed for data loss, compatibility with rolling releases, downtime and rollback/recovery.
- Prefer targeted projections and indexes justified by access patterns; inspect query plans for performance changes.
- Protect dynamic queries against injection; use parameterization and vetted query construction.
- Do not default to elaborate messaging/outbox/event sourcing unless requirements and failure modes warrant them.

## 8. Security and privacy
- Treat every external payload, identity claim, file path, deserialized object and environment value as untrusted at appropriate boundaries.
- Authenticate and authorize at each protected operation; enforce least privilege and default denial.
- Prevent injection through parameterization, contextual escaping/encoding and safe serialization. Validate upload sizes/types and avoid unsafe path use.
- Keep secrets in approved stores/configuration mechanisms; never hardcode them or expose them through logs, errors, URLs or test output.
- Use supported vetted crypto and TLS, not custom algorithms; follow current platform security guidance.
- Redact or minimize PII, tokens, credentials, sensitive headers/body fields and security-related identifiers in telemetry.
- Consider abuse, DoS/resource exhaustion, replay, rate limits, dependency/supply-chain vulnerabilities and audit requirements.

## 9. Concurrency and long-running processing
- Prefer local immutable state and clear ownership. Document thread-safety of shared services, caches, and registries.
- Use cancellation propagation, asynchronous I/O, safe lifecycle management and bounded processing queues.
- Do not assume atomicity across database, message broker and external API; document consistency and duplicate-work handling.
- Choose synchronization primitives deliberately; test contention, deadlock, lost updates and race conditions when plausible.
- Add backpressure/resource budgets for workloads with unbounded inputs or throughput.

## 10. Performance and scale
- Choose algorithms/data structures for expected size and complexity; fix obvious N+1 behavior and unbounded allocations.
- Use pagination, streaming, batching and caching where they solve observed bottlenecks and do not compromise correctness.
- Profile realistic datasets; establish a baseline and compare changes. Do not claim performance improvements without measurements.
- Consider Amdahl's Law before parallelism: serial portions and contention limit gains. Consider scale-out cost and operational complexity.

## 11. Testing and operational readiness
- Write tests for meaningful behavioral changes and regressions, including edge cases and failure paths; prefer behavior-based assertions to private implementation checks.
- Add integration tests for real database, serialization, authentication and network boundaries as risk demands.
- Never infer success from coverage percentage alone. Run checks and report actual commands/results, or describe verification not performed.
- Use structured, privacy-safe logs and correlation IDs; traces/metrics must answer operational questions rather than create noise or high cardinality.
- Validate configuration, startup, readiness, shutdown, observability, migration, and recovery for production-impacting changes.

## 12. Review-oriented prompts
1. What single invariant or behavior must be preserved?
2. Which callers, stored values and external clients could depend on this change (Hyrum's Law)?
3. Is this true shared knowledge or accidental code similarity (DRY vs coupling)?
4. Is each new dependency, abstraction and configuration option demonstrably necessary (YAGNI)?
5. Which error, duplicate, cancellation or concurrency case could cause data loss?
6. Are security, privacy and access control covered at the relevant boundary?
7. Which claims are proven by actual tests, traces, queries, measurements or other evidence?
