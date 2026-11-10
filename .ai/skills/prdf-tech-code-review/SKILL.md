---
name: prdf-tech-code-review
description: A skill to review recent changes to a codebase, comparing against product requirements, tech specs, and existing notions
compatibility: Might require access to GitHub/GitLab/Bitbucket, local codebase and ticketing tools like Linear. A local browser MCP might be required for front-end reviews.
metadata:
  author: jsmrcaga
  version: v0.0.1
---

This skill will help you perform code review against existing tech specs, product requirements,
designs and codebase.

The goal is to review some recent code changes, locally, and provide input to the user
on how to better approach the changes.

# Execution modes
This skill should always be executed either manually by the user, or from the /prdf-owner
main skill.
If not, context will be missing, so exit with an error.
In both cases, an execution mode of "coaching" or "auto" will be provided. Default to "coaching"

# Inputs

- The context of the changes (PRD, Tech Spec, curent Ticket)
- The user will provide the repository in which the changes have been made, the branch against
	which to compare, and/or the relevant commits.
- The user should provide any important information such as guidelines, ad-hoc decisions, ADRs, or any
	that might change the outcome of the review.
- If this review is intended as a partial-review (meaning, the changes are not for an entire
	ticket or job), the user should be explicit about it and provide context
- The review might include multiple codebases (for example, Back-end and front-end)
- The execution mode, "auto" or "coaching". Default to "coaching".

# Instructions

0. Read `../../instructions/BASE_INSTRUCTIONS.md` and `./CUSTOM_INSTRUCTIONS.md`
1. Read the context of the review
	- If there is a ticket, read the ticket
	- For any PRD or Tech Spec also try to find it in the PRDF repo
2. Ask the user any clarifying questions, such as
	- Missing context for the review
	- If the review is partial (eg 1 commit ready but 3 planned...)
	- If the review should include or exclude any specific focus (such as security, pragmatism, )
	- What the review is about (infra, app code, DX...)
3. With that information, decide which agents to spawn. You should always spawn _at least one_.
	 Every agent should write back their review in a temporary file (thanks to their harness temp file
	 tool) and communicate the file back to you.
	 You can find the agents and their prompts in `./agents`. This is the list
	 - Security Expert
	 - Codebase Architect
	 - Infrastructure Architect
	 - Domain Expert
4. Once all agents have reported back, synthesize the findings into a separate review file.
   This file should deduplicate any feedback from the agents, and make it actionable for the user.
   If the execution mode is "auto":
		- The synthesized document should include tasks that will be picked up by an LLM
   If the execution mode is "coaching":
		- The synthesized file should present findings so that a human might read, learn and
			understand the problems and solutions. Don't be too verbose, the readers are engineers.
5. Present the file to the user.
<!-- 6. If the execution mode was "auto", confirm the file with the user and spawn implementation agents.
   Use the .ai/agents/tech/implementer.md agent. Spawn as many agents as there are repositories.
   These agents should follow:
   - any guidelines provided
   - the tech spec, ticket, PRD, design...
   - the repo guidelines itself
 -->
