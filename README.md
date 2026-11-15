# CodeTenet - Claude Plugin by Kasadara

**Publisher: Kasadara Technology Solutions** 
**Version: 1.0.0** 
#### Documentation-only plugin 
#### No MCP servers, hooks, executables, network access, or runtime dependencies.

**Principles first. Better code always.**


## Text and formatting policy

CodeTenet uses only characters available on a standard US QWERTY keyboard for authored text. Documentation, generated advice, code comments, release notes, and examples must use printable ASCII (plus line breaks and tabs). Avoid emoji, smart quotes, Unicode arrows, mathematical symbols, and box-drawing characters. Preserve technical meaning while substituting plain-text equivalents. Do not alter identifiers or data values just to satisfy typography rules; use ASCII escape sequences where technically appropriate.

A unified, language-agnostic engineering assistant skill for requirements analysis, architecture, feature delivery, debugging, legacy refactoring, reliability, security, performance, APIs, testing and code reviews.

## What's in this repository

```text
.claude-plugin/plugin.json                # Claude Code plugin metadata
skills/software-engineering/SKILL.md    # Main agent instructions
skills/software-engineering/references/ # 5 detailed references
skills/software-engineering/examples/   # Agent task template and 12 scenario playbooks
README.md                                 # Installation, scenario examples, publication
PUBLISHING.md                             # Directory launch checklist
```

## Repository and release status

**Official repository:** https://github.com/Kasadara-Technology-Solutions-Pvt-Ltd/CodeTenet  
**GitHub owner:** Kasadara-Technology-Solutions-Pvt-Ltd  
**Plugin identifier:** `codetenet`  
**Skill identifier:** `software-engineering`  
**Tagline:** Principles first. Better code always.

The public CodeTenet repository hosts the published skill. Claude Directory listing, local CLI validation, publisher contact, icon selection, and license compliance review remain independent release steps.

## Try locally before publication

```bash
claude plugin validate --strict .
claude --plugin-dir .
```

In Claude Code, run the skill by name (for example `/codetenet:software-engineering`) or ask Claude to apply enterprise engineering principles while working on a task. Confirm command discovery in your locally installed Claude Code version.

## Publish to Anthropic's Claude Plugin Directory

1. Upload the **contents** of this directory to the existing [CodeTenet GitHub repository](https://github.com/Kasadara-Technology-Solutions-Pvt-Ltd/CodeTenet) root.
2. Have an authorized Kasadara representative choose and include an explicit open-source or proprietary **LICENSE**. Ensure the material is yours to license. No license has been chosen on your behalf.
3. Verify the publisher name and add real `homepage` and `repository` metadata to `.claude-plugin/plugin.json`; use your actual values.
4. Review each skill and reference for confidential or copied material. Keep links and attributions appropriate.
5. Run `claude plugin validate --strict .`, inspect warnings, and do an end-to-end test.
6. Open https://claude.ai/directory/manage with an eligible paid Claude account, submit the GitHub repository, and follow the portal validation/review workflow.
7. Once approved, publish through the portal. Submission is **not** automatic; approval is **not** guaranteed.

See [PUBLISHING.md](PUBLISHING.md) for a release checklist and suggested directory listing text.

## Usage scenarios

Use this skill when you need:

- **Build a feature:** "Add pagination and sorting to this API, preserving response compatibility. Include edge cases and automated tests."
- **Investigate a defect:** "Diagnose why this Windows service hangs after several hours; identify root cause before patching and validate shutdown."
- **Refactor:** "Reduce duplication in these services without coupling unrelated domain rules. Keep the external behavior unchanged."
- **Architecture:** "Compare a modular monolith and microservices for our actual constraints; explicitly discuss operational cost, change boundaries and reversibility."
- **Security review:** "Audit authorization and logging paths; identify sensitive fields leaked to telemetry and propose fixes."
- **Database migration:** "Add a nonnullable field to a populated table with a safe rollout, backfill, rollback plan and tests."
- **Performance:** "Profile this endpoint before changing its implementation; report actual measurements and regression checks."
- **Distributed messaging:** "Design duplicate-safe message handling with idempotency and clear failure recovery."
- **Testing:** "Design risk-based unit, integration and contract tests for this API without chasing a vanity coverage score."
- **Code review:** "Review this PR for correctness, security, concurrency, compatibility and unnecessary abstractions; prioritize findings by severity."

The original unified skill README and the full 12-scenario playbooks are preserved below.

---

## Extended guide and examples

# Enterprise Programming & Software Engineering - Unified AI Skill

A **single comprehensive, language-agnostic skill** merging the *Enterprise Programming Guide* and *Enterprise Software Engineering* into a practical autonomous coding standard. The primary `SKILL.md` defines behavior; companion references deepen implementation, architecture, verification, and trade-off decisions. This is an original synthesis of coding principles and engineering laws, not a verbatim reproduction of source articles.

## What's included

```text
skills/software-engineering/
 SKILL.md                                 # Core AI instructions + YAML frontmatter
 references/
    programming-standards.md            # Detailed coding and operational rules
    architecture-decision-guide.md      # Laws, boundaries and ADR template
    testing-verification.md             # Test matrices and evidence requirements
    principle-conflicts.md              # Trade-off decisions with examples
    code-review-checklist.md            # Concise review gate
 examples/
     scenario-playbooks.md               # 12 scenario walkthroughs
     agent-task-template.md              # Reusable request template
```

## Installation

**Claude Code - project-level:**

```bash
mkdir -p .claude/skills
cp -R skills/software-engineering .claude/skills/
```

**Claude Code - user-level:**

```bash
mkdir -p ~/.claude/skills
cp -R skills/software-engineering ~/.claude/skills/
```

On Windows, copy the folder into `%USERPROFILE%\.claude\skills\` for global scope, or `.claude\skills\` inside a repository for project scope. Keep the directory structure intact. Claude Code can use the skill description to discover it, and you can explicitly ask the agent to use `software-engineering`.

**Other coding agents:** Point the agent's supported instructions or skills mechanism to `SKILL.md`; make the `references/` and `examples/` files accessible. Adapt frontmatter or path conventions to that agent's format if necessary.

## How the skill behaves

1. **Discover:** Read requirements, existing code, test/configuration conventions, boundaries and contracts.
2. **Design:** Select the smallest correct and secure approach, applying SOLID, DRY, KISS, YAGNI and relevant engineering laws with context.
3. **Implement:** Make focused changes; keep invariants, failure cases and privacy/security intact.
4. **Verify:** Run appropriate build, lint, tests and risk checks; report real evidence, never fabricated success.
5. **Report:** State changes, key decisions, actual verification and unresolved risks.

The agent reads `SKILL.md` first and uses supporting files selectively. No single law is a substitute for judgment. The skill does not force additional dependencies, cloud services, abstract classes, or architecture patterns.

## Example prompts for different scenarios

Each example can be pasted into an AI coding agent. The corresponding detailed workflow is in `examples/scenario-playbooks.md`.

### Scenario 1 - Implement a new feature

> Use the enterprise programming and software engineering skill. Add an order discount eligibility rule. First locate existing price and promotion policies and tests. Implement the smallest cohesive change without duplicating business knowledge. Cover thresholds, invalid inputs and regressions; report tests you actually ran.

**What good looks like:** One authoritative discount rule, explicit behavior, tests, no speculative rules engine. Relevant principles: SRP, DRY, KISS, YAGNI.

### Scenario 2 - Debug a duplicate-processing bug

> Use the skill to investigate why resubmitted invoice requests sometimes create duplicates. Reproduce the failure, inspect retry and transaction behavior, fix the root cause and verify concurrency and partial-failure scenarios. Preserve current external API contracts.

**What good looks like:** Durable idempotency/uniqueness where needed, a reproducing regression test and no UI-only workaround. Relevant laws: Murphy's Law, Hyrum's Law.

### Scenario 3 - Refactor a complex legacy module

> Apply the skill to refactor the existing large service for maintainability only. Establish characterization tests, identify cohesive responsibilities, preserve public behavior and extract changes incrementally. Avoid new packages or large-scale redesign without a concrete need.

**What good looks like:** Small reviewable changes with preserved behavior. Relevant laws: Gall's Law, Hyrum's Law, Boy Scout Rule.

### Scenario 4 - Create an enterprise REST API

> Design and implement a REST API for client accounts using the repository's existing stack. Define request/response contracts, authorization, validation, conflicts, pagination, migration impact, safe errors and tests. Do not add architecture layers merely to demonstrate SOLID.

**What good looks like:** Stable documented contracts, access control and consistent state transitions. Relevant principles: SRP, DIP, Law of Demeter, least astonishment.

### Scenario 5 - Publish a framework-neutral utility library

> Build a reusable zero-runtime-dependency TypeScript library. Identify required APIs, public contract, packaging/typings and failure semantics. Favor standard library functions, avoid speculative plugins and verify browser/Node compatibility and package output.

**What good looks like:** Clear small exports, tests, stable types and no framework lock-in. Relevant principles: KISS, YAGNI, composition.

### Scenario 6 - Design a distributed worker

> Implement an event consumer that writes to a relational database. Document duplicate delivery, ordering, partial failures, transaction scope, retries, cancellation and idempotency. Test crash-after-commit and replay paths. Don't promise exactly-once behavior without proof.

**What good looks like:** Recoverable state changes with defined failure semantics. Relevant laws: distributed computing fallacies, leaky abstractions, Murphy's Law.

### Scenario 7 - Safely migrate a database

> Add a new required field to an existing production table. Inspect old records and application compatibility, propose a phased expand/backfill/contract migration, consider locking and rollback, then create the changes and migration tests.

**What good looks like:** Safe mixed-version rollout with existing data protected. Relevant laws: Hyrum's Law, unintended consequences.

### Scenario 8 - Address a security vulnerability

> Review report access authorization for cross-tenant data exposure. Trace trust boundaries, fix resource-level authorization on the server, check cache isolation and add denied-access tests. Do not log sensitive data or rely on hiding UI links.

**What good looks like:** Explicit access checks and negative tests. Relevant priorities: least privilege, defense in depth, security before convenience.

### Scenario 9 - Investigate slow performance

> Diagnose slow search endpoints. Capture a baseline using realistic workloads, inspect queries and allocations, identify the actual bottleneck and implement the minimum justified improvement. Compare before/after metrics and test correctness.

**What good looks like:** Measured improvement and a reason for any added complexity. Relevant laws: Amdahl's Law, premature optimization, Goodhart's Law.

### Scenario 10 - Review an always-on background service

> Analyze this continuously running service for cancellation, exception propagation, infinite loops, resource leaks, unbounded queues, safe restart and duplicate operations. Provide concrete findings, fixes and test scenarios.

**What good looks like:** Safe lifecycle management, bounded resource use and clear recovery behavior. Relevant laws: Murphy's Law, leaky abstractions.

### Scenario 11 - Evaluate a proposed microservices rewrite

> Compare a modular monolith, selective extraction and full microservice migration for this system. Use documented load, independent deployment needs, team ownership and failure risks. Produce an ADR with trade-offs and a migration strategy; do not equate complexity with enterprise quality.

**What good looks like:** Evidence-based architecture choice. Relevant laws: Conway's Law, Gall's Law, Second-System Effect.

### Scenario 12 - Perform a high-quality code review

> Review this pull request against the enterprise programming skill. Prioritize correctness, security, data integrity, compatibility, concurrency and test quality. Give actionable findings with locations and severity. Distinguish checks you actually executed from claims in the PR description.

**What good looks like:** Risk-ordered, evidence-backed findings rather than style-only criticism. Relevant laws: Goodhart's Law, Kernighan's Law, Hyrum's Law.

## Choosing which reference to read

| User task | Main supporting file(s) |
|---|---|
| Implement a feature, library, API or worker | `programming-standards.md`, `testing-verification.md` |
| Plan architecture, integration, service boundaries | `architecture-decision-guide.md`, `principle-conflicts.md` |
| Debug or refactor legacy code | `programming-standards.md`, `testing-verification.md` |
| Review a pull request | `code-review-checklist.md`, `testing-verification.md` |
| Decide between competing patterns | `principle-conflicts.md`, `architecture-decision-guide.md` |
| Need an agent handoff prompt | `examples/agent-task-template.md` |

## Sources and attribution
- https://lawsofsoftwareengineering.com/

These are background references; this package consolidates and extends the ideas into original operational instructions. The examples are illustrative; adapt them to your repository's constraints. Source websites' content is not redistributed.


## Kasadara-branded self-hosted marketplace (optional)

This package includes `.claude-plugin/marketplace.json` for optional GitHub-based distribution. After publishing the repository, users can run:

```bash
claude plugin marketplace add Kasadara-Technology-Solutions-Pvt-Ltd/codetenet
claude plugin install codetenet@kasadara-plugins
```

The public GitHub repository exists, but must contain the plugin files before installation. The official Claude Directory submission does not require a separate marketplace.

## Anthropic directory policy

See [DIRECTORY_POLICY_COMPLIANCE.md](DIRECTORY_POLICY_COMPLIANCE.md) for documented safety and security measures, sample review prompts, and outstanding publisher verification items. The plugin itself has no bundled MCP servers, hooks, telemetry, account system, or automatic external network calls. The publisher must confirm ownership and submission compliance before claiming directory approval.
