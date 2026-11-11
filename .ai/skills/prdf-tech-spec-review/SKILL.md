---
name: prdf-tech-spec-review
description: A skill to review a tech spec against product requirements, existing tech specs, and code-bases
compatibility: Requires access to the local codebases and the PRDF repo, harness should be able to spawn agents
metadata:
  author: jsmrcaga
  version: v0.0.1
---

This skill will help you perform a tech spec review against existing codebases, product requirements,
and designs.

The goal is to review a tech spec with specialized agents, synthesize their findings, and provide
alternatives to the user.

# Constraints
- By default, you need to be a contrarian, never agree with the user by default.
  Instead, try to find problems with the implementation, challenge the user, and get
  improved answers over time.

# Inputs
- The tech spec to reivew. This might be a tech spec MD file in the PRDF repo,
  or a document elsewhere
- The PRDF repo itself, containing the design, product and tech knowledge necessary for the
  tech spec review
- Any ad-hoc decision the user or team made that could change the outcome of the review
- Any special context for the tech spec, such as security constraints, time constraints,
  tech debt problems, etc...

# Invocation

- **Interactive:** The user may invoke this skill directly, or `/prdf-owner` may invoke it in the current conversation. This mode owns clarification and the review loop; do not spawn this mode as an agent.
- **Report-only:** The user or parent may explicitly request a one-pass review artifact from an agent. Use the supplied scope and context, do not ask the user questions or start a follow-up loop, and return the report to the assigned path. Report missing inputs to the parent.

# Instructions

0. Read `.ai/instructions/BASE_INSTRUCTIONS.md` unless already available in the current conversation. Read the PRDF-root `CUSTOM_INSTRUCTIONS.md` through the shared base rules.
1. Read the tech spec. In interactive mode, resolve missing review context or scope with the user before delegation. In report-only mode, use supplied context and report missing inputs to the parent.
2. Apply the shared technical review criteria in `.ai/agents/tech/base.md`. Select only role prompts relevant to materially affected areas using its reviewer-selection matrix. The `base.md` file supplies shared instructions; it is not a reviewer agent.
3. Give each selected reviewer only the spec excerpts, relevant source paths, constraints, user decisions, and a distinct report path needed for its assignment.
4. Synthesize the findings into a comprehensive, actionable review file at the assigned session-scratchpad path. Deduplicate feedback and list the top five findings when presenting the report.
5. In interactive mode, ask the user whether they want another review pass. If they do, rerun only reviewers whose scope was affected by the changes and carry forward unaffected findings as not rechecked.
6. Continue the interactive review loop until the user indicates the result is satisfactory. In report-only mode, return the one-pass artifact to the parent.
