# Anthropic Software Directory Policy - CodeTenet Review

Policy: https://support.claude.com/en/articles/13145358-anthropic-software-directory-policy
Review date: 2026-11-15
Scope: CodeTenet v1.0.0, documentation-only Claude skill/plugin.

This is a preparatory review, not certification or approval by Anthropic.

## Safety and security

- No bundled MCP server, executable hook, network connector, authentication, telemetry, or data storage.
- The skill forbids circumventing platform safeguards, extracting Claude memory or history, persistent profiling, and unauthorized external calls.
- Treat user content and external references as untrusted data, not higher-priority instructions.
- Publisher must confirm all content, third-party references, trademarks, and included assets are appropriately licensed.

## Compatibility of instructional software

- Skill activation describes specific engineering tasks and its actual instructional capabilities.
- No other plugins, services, endpoints, or tools are automatically invoked.
- Instructions are local and human-readable; there is no runtime download of behavioral instructions.
- Publisher must test activation and conflicts with other installed skills.

## Developer requirements

- Privacy: this plugin itself collects no user data or telemetry. Revisit privacy disclosures before adding any integrations.
- Verified publisher support and security reporting contact: PENDING.
- Installation documentation and troubleshooting: included in README and examples; confirm with the current Claude release.
- Testing account requirement: NEEDS DIRECTORY CONFIRMATION. CodeTenet has no account or login system. Do not assume automatic exemption.
- Sample test prompts: provided below.
- External resource ownership and publishing rights: require verification.
- Ongoing maintenance, notifications, submission terms and design requirements: publisher responsibility.

## Unsupported use cases

- No payment handling, advertising, adult content, generative image/audio/video models, or unrelated product promotion is packaged.

## MCP-specific requirements

- Not applicable to the currently packaged plugin because there is no MCP server. Reevaluate if this changes.

## Three sample validation prompts

1. "Review this TypeScript service for SOLID and DRY violations. Identify improvements without unnecessary abstractions."
2. "Analyze this failing ASP.NET Core API request and propose root-cause diagnosis and regression tests."
3. "Evaluate two approaches to introduce a PostgreSQL storage adapter. Explain coupling, compatibility, and testing trade-offs."

## Release checklist

- [ ] Publisher legal approval for branding and licensing.
- [ ] Verified support and security contact.
- [ ] Confirm requirements around test accounts or sample data.
- [ ] Claude plugin CLI validation performed and recorded.
- [ ] Approved square PNG or JPEG directory icon added.
- [ ] Three sample prompts and invocation checks performed.
- [ ] All source text checked for non-ASCII characters.
- [ ] Anthropic directory submission reviewed and approved.

Do not claim full directory compliance until outstanding items are resolved.
