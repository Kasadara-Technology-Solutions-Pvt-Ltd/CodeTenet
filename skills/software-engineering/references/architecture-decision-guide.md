# Architecture and Engineering Laws - Decision Guide

## Context-first decision procedure
1. Identify functional requirements, constraints and observable compatibility contracts.
2. Draw boundaries (caller, domain, persistence, external dependencies, identity, operations) and ownership.
3. List credible failure and change scenarios, not hypothetical everything-can-change possibilities.
4. Prefer a working vertical slice (Gall's Law); make complexity pay for itself.
5. Compare two or three viable choices with explicit pros, costs, failure modes, migration and verification needs.
6. Record the chosen option and conditions that would trigger reconsideration.

## Laws and concrete implications
| Concept | Practical architectural implication | Misuse to avoid |
|---|---|---|
| Gall's Law | Grow from a working, testable slice | Shipping insecure or incomplete behavior as a permanent shortcut |
| Hyrum's Law | Preserve observable quirks until versioning/migration resolves consumers | Treating all accidental behavior as permanent forever |
| Leaky Abstractions | Expose unavoidable failure/latency/transaction semantics | Promising that a wrapper eliminates all infrastructure behavior |
| Conway's Law | Match deployable boundaries to real ownership where practical | Inventing microservices for nonexistent teams |
| Tesler's Law | Put unavoidable complexity in an explicit suitable layer | Moving complexity into invisible magic |
| Second-System Effect | Scope rewrites tightly; migrate incrementally | Rebuilding every feature with extra abstraction |
| Distributed Computing Fallacies | Budget for latency, partitions, retries and failure | Assuming an internal service call cannot fail |
| CAP Theorem | Define partition trade-offs for replicated data systems | Saying all systems must just 'pick two' in normal operation |
| Goodhart's Law | Optimize for user and system outcomes, not only proxy metrics | Declaring high coverage equal to correctness |
| Amdahl's Law | Profile serial bottlenecks before parallelization | Assuming more workers mean linear speedup |
| Occam's Razor | Prefer simplest model compatible with evidence | Omitting required security and error handling |
| Boy Scout Rule | Improve adjacent code safely during changed work | Unrelated rewrites disguised as cleanup |
| Brooks's Law | Account for coordination overhead in delivery plans | Assuming extra staffing fixes schedule risk instantly |
| Sunk Cost Fallacy | Reassess poor choices based on future cost | Keeping risky design just because it exists |

## Architecture Decision Record template
```markdown
# ADR: [Decision]
Status: Proposed | Accepted | Superseded
Date: YYYY-MM-DD
Context: [What problem, measured demand, constraints and existing contracts?]
Decision drivers: [Correctness, security, maintainability, cost, performance, operations]
Options considered:
- Option A: benefits / costs / failure modes
- Option B: benefits / costs / failure modes
Decision: [Chosen option and why]
Consequences: [Compatibility, migration, operational cost, risks]
Evidence: [Tests, observed constraints, metrics]
Revisit when: [Concrete new condition]
```

## Layering test
A boundary is justified when it manages an independent responsibility, unstable dependency, security/trust concern, cohesive domain policy or independent deployment/ownership. Avoid defaulting to controllers -> interfaces -> services -> managers -> factories -> repositories for every tiny operation.

## Change-safety checklist
- External callers and stored data mapped
- Backward compatibility preserved or versioned
- Failure paths and partial states designed
- Migration/backfill/rollback accounted for
- Observability and operational ownership clear
- Tests can falsify architecture assumptions
