---
name: prdf-debug
description: This skill debugs the prdf (product-domain framework) itself, checking for blind spots, syntax errors, and potential contradictions
compatibility: ''
metadata:
  author: jsmrcaga
  version: v0.0.1
---

This skill is meant to help you debug the PRDF itself.
This can happen in 2 ways
1. The user is building/improving the repo for their own use
2. The user is trying to make the repo work in their use-case

# Context
- You need a PRDF repo as context.

# Inputs
- The expected debugging mode (building/improving or work in their use-case)
- The debugging expectation from the user
	- They might be looking to debug a specific scenario or skill
	- If the user is the main author of PRDF you can accept broad scope, otherwise
	- DO NOT ACCEPT broad expectations or empty inputs, force the user to choose
	  a narrow scope to debug. Incremetally wins the race.


# Instructions
Read `.ai/instructions/BASE_INSTRUCTIONS.md` from the PRDF repository root unless it is already available in the current conversation.

1. Read the PRDF repo shallowly to get acquainted with it
	- Do not read every single feature or tech spec or design
	- List the files, check the custom files (CUSTOM_INSTRUCTIONS, xxx_INTRO.md files...)
2. Depending on user input, ask clarifying questions on the debugging expectation
3. Sparring with the user, dig into the problem
	- Check the expectation and make a proposal
	- Get into a feedback loop with the user until they accept the edit or change
4. Spawn a fresh agent
	- Do not pass unrelated conversation history. Give the agent the original request, the bounded skill/files under review, relevant source paths or excerpts, applicable constraints and user decisions, and the expected report format.
	- The agent should have no recollection of unrelated conversation.
	- Ask it to check the current implementation of the PRDF against the user request
5. With the agent's feedback, go back to step 3. Only loop 2 times maximum.
