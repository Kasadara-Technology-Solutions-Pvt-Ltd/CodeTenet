# CodeTenet — Publishing Checklist

**Product:** CodeTenet  
**Publisher:** Kasadara Technology Solutions  
**Owner:** Kasadara  
**Repository:** https://github.com/Kasadara-Technology-Solutions-Pvt-Ltd/CodeTenet  
**Claude plugin:** `codetenet`  
**Skill:** `software-engineering`  
**Tagline:** *Principles first. Better code always.*

## Current status (15 November 2026)

- GitHub repository verified: public, default branch `main`, empty at time of check.
- Connected GitHub account has **read but not push** permission. Nothing has been uploaded.
- Plugin ZIP structure and JSON syntax are verified locally.
- Claude CLI validator and end-to-end plugin installation have **not** been run.
- No license has been selected or included. Do not distribute as an open-source project until authorized.
- Claude Directory submission/review has not occurred.

## Before release

- [ ] Obtain permission to push to the organization repository, or have an authorized maintainer upload repository files.
- [ ] Choose a company-approved license and add `LICENSE`. Verify rights to publish all included material.
- [ ] Review branding, publisher identity, security, confidentiality, and third-party attributions.
- [ ] Upload this ZIP's **CodeTenet folder contents**, not the folder itself, to the repo root.
- [ ] Run `claude plugin validate --strict .` in the repository root with a supported Claude Code CLI.
- [ ] Run `claude --plugin-dir .` and verify the `software-engineering` skill is discovered.
- [ ] Test at least feature implementation, debugging, security review, and architecture-choice scenarios from README.
- [ ] Verify all README instructions against the installed Claude Code CLI version.
- [ ] Tag the release as `v1.0.0` once accepted.
- [ ] Submit https://github.com/Kasadara-Technology-Solutions-Pvt-Ltd/CodeTenet through https://claude.ai/directory/manage and await review.

## Self-hosted marketplace install (after files are uploaded)

```bash
claude plugin marketplace add Kasadara-Technology-Solutions-Pvt-Ltd/CodeTenet
claude plugin install codetenet@kasadara-plugins
```

## Directory listing

**Name:** CodeTenet  
**Publisher:** Kasadara Technology Solutions  
**Description:** A comprehensive, language-agnostic software engineering skill that guides AI coding agents through architecture, implementation, debugging, refactoring, security, performance, testing, and code reviews using established engineering principles and laws.

The official Anthropic Directory and an independently hosted Claude Code marketplace are different distribution channels. No directory approval is implied by a valid manifest.
