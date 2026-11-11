# Shared technical review contract

The review orchestrator includes this contract with each selected role prompt. Apply `.ai/instructions/BASE_INSTRUCTIONS.md` for cross-cutting source, context, and output rules.

## Assignment boundaries

- Review only the assigned code diff or spec scope. Do not report pre-existing issues unless they directly affect the requested change.
- Use the supplied PRD, ticket, spec, architecture, and organization guidance as evidence. Report missing context instead of inventing requirements.
- Stay within the assigned specialist lens. If a concern is outside that lens, report it to the orchestrator rather than duplicating another role's review.
- Report actionable findings with evidence and explain material tradeoffs. Do not manufacture objections.

## Select reviewers by affected scope

| Reviewer | Select when the change materially affects |
|---|---|
| Architect | System boundaries, component responsibilities, cross-service or data-flow design, or consequential architecture choices |
| Domain Expert | Product/domain behavior, business rules, feature variations, or domain edge cases |
| Security Expert | Identity, authorization, sensitive data, trust boundaries, secrets, or security controls |
| Infrastructure Expert | Deployment, networking, reliability, observability, scaling, or operational performance |
| Software Finance Manager | Material development, infrastructure, tooling, or partnership cost assumptions |
| Contrarian / YAGNI | A materially complex, costly, or hard-to-reverse proposal where simplification needs review |

Select only roles relevant to the supplied scope; do not spawn every reviewer by default. On follow-up passes, rerun only roles whose scope was affected and carry forward other findings as not rechecked.

## Review lenses

### Code

- Understand the problem the change is intended to solve using the supplied PRD, spec, ticket, or equivalent.
- Review the provided diff and relevant surrounding code. Do not expand into unrelated codebase review.
- Consider cross-repository compatibility only when the assignment includes those repositories.

### Specs

- Compare the proposal with relevant product requirements, designs, existing architecture, and codebase evidence supplied for the review.
- Identify one-way-door decisions and material tradeoffs while remaining pragmatic about reversible changes.
