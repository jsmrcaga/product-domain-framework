---
name: prdf-add-skill
description: This skill helps the agent add new skills to the PRDF repo, either generic (OSS) or under specific subdomain usage
compatibility: ''
metadata:
  author: jsmrcaga
  version: v0.0.1
---

This skill is meant to help you add an LLM skill to the PRDF repo.
This can happen in 2 ways
1. The OSS maintainer is adding a new generic skill for PRDF users to use (Generic)
2. The PRDF user wants to add a skill for their own use in PRDF (User-skill)

# Context / Inputs
- You need a PRDF repo as context
- You need to know which of the 2 modes the user is targeting

# Skill constraints

## PRDF Generic Skill
- All generic PRDF skills must follow these guidelines
	- No sycophancy (usually passed by /prdf-owner)
	- Token economics: Skills should try to read as little as possible, and reuse context as much as possible
	- Execution modes: either Interactive or Autonomous (both are possible)
	- Skills are Artifact First: output is always written down in files, either user file-system or sketchpad

- The skill should have either of these modes (both are acceptable)
	- Agent autonomous mode
		- So that `/prdf-owner` can trigger it as an agent
	- User-facing interactive mode
		- If the user requires the LLM to ask questions and spar

	-> If both are selected, the skill must have specific instructions
		 on how to handle agent mode.

- The skill must reference the BASE_INSTRUCTIONS and CUSTOM_INSTRUCTIONS file by adding
	`- Read `.ai/instructions/BASE_INSTRUCTIONS.md` from the PRDF repository root and follow it.`
	in its instructions

## PRDF User-Skill
- The skill should use the PRDF repo, so add instructions on how to read the repo
- The skill MUST be invocable by `/prdf-owner` so the owner can pass required context
- The skill MUST pass the non-redudancy and token-finance checks of this repo, reusing
	context, passing context to agents etc.

# Instructions
1. Get user input on the type of skill they are building
2. Ask the user what the skill is meant to do
	- Depending on this, get any "Compatibilty" necessities to add
	- Get info about any extra context the skill might need
3. With that information start drafting the skill in your sketchpad
	- Spar with the user, ask questions for clarification
	- Try to get the skill to be as lean as possible, we prefer specific easy-to-test jobs
	- Enter a feedback loop with the user
4. Check that the skill follows the guidelines in [Skill Constraints](#skill-constraints)
5. Once you've reached an acceptable skill description:
	- If the skill is Autonomous
		- Ask the user to run it on a separate agent pane to test
	- If the skill is Agentic
		- Run it in this chat pane and report back
6. Write the skill to the repo. It can have any name the user decides, and can omit the `prdf-` prefix
