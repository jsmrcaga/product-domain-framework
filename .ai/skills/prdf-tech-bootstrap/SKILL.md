---
name: prdf-tech-bootstrap
description: A skill to start the /tech section of a PRDF repo, gets necessary info from user, crafts diagrams and documents decisions and architecture
compatibility: Might require access to GitHub/GitLab/Bitbucket, local codebase too. Might require access to Notion, Figma and other MCP servers
metadata:
  author: jsmrcaga
  version: v0.0.1
---

This skill will allow you to build the initial knowledge base for `/tech`

It will reuse other skills (provided by PRDF or not) in different ways in
order to fill the /tech section, and will require a lot of input and
back-and-forths with the user.

# Inputs

- Existing docs: The user will need to provide, if any:
	- List of interesting repos, and if they are available locally (+ local path)
	- List of existing documentation and tech specs, and their sources (Notion, Figma etc)
- Architecture: The user should provide
	- Existing Diagrams or descritpion of global architecture (including the subdomain)
	- How the subdomain interacts with the global architecture
	- Any dependencies between this subdomain and "siblings" or "closest" subdomains
- Data model
	- The user should provide information about the data model. This can either be a direct
	  DB connection for you to explore with a list of tables (or all) , or an extraction of the necessary tables.
- The PRDF repo should already have the Product bootstrapped that you'll use as input/context
- The user should provide any guidelines such as certifications (eg: ISO27001), security, golden-paths etc.


# Instructions

Run this workflow in the user-facing conversation; it owns the clarification, validation, feedback, and confirmation gates. Do not spawn the bootstrap skill itself as an agent.

1. Read `.ai/instructions/BASE_INSTRUCTIONS.md` unless already available in the current conversation. Reuse supplied Tech context and relevant Product requirements; read only missing sources needed for this bootstrap.
2. Ask the user any clarification questions to get info necessary to bootstrap, look at the [Inputs](#inputs) section
	- Gather the inputs needed for the available discovery work; do not request unrelated context.
3. After gathering and validating the user-provided context, delegate only the discovery work supported by available sources.
	- Launch codebase discovery using `/prdf-tech-discovery` when a relevant codebase is available.
	- Launch documentation discovery using `/prdf-tech-discovery` when relevant documentation sources were provided.
	- Assign each agent a distinct report path in the session scratchpad.
4. Synthesize the information into the assigned session-scratchpad file.
	- If any drifts are detected between the sources, flag them to the user
	- Combine the sources into that assigned scratchpad file, combining by area such as
		- Features
		- Data models
		- Architecture
		- Repos
		- Dependencies
		- Technologies
		- Infra
		- etc.
5. Summarize your findings and confirm with the user, enter a feedback loop for any questions
   or gray areas you may still have. This is the time to solve any drifts as well, and to check
   if any sources have been missed. Once you get answers/new sources, go back to 3 or 4.
6. Confirm with the user and start a few agents to write to the `/tech` folder of the PRDF repo, following the
   CUSTOM_INSTRUCTIONS and templates if needed.
	- Assign an agent to write only the relevant `/tech/codebase` files, including features, repos, and `CODEBASE.md`.
	- Assign an agent to write only the `/tech/architecture` section, following the structure described in the PRDF-root `KNOWLEDGE_BASE.md`.
		- Any diagrams should be built following either CUSTOM_INSTRUCTIONS or the "Building diagrams" below
	- Assign an agent to write only the `/tech/data-model` section.
	- Do not start these knowledge-base edits until the user confirms the synthesized findings.

# Detecting Drift
Once everything's validated and written down, check the `/product` and `/design` sections
of the PRDF repo and compare with the `/tech` section. You can spawn agents to
do so if necessary.

Our goal is ONLY _to find_ any drift between these sections to flag them to the user, validate
and write to DRIFT.md. This will allow them to figure out _how_ to fix the drift, but this
IS NOT our goal here.

# Building diagrams
<!-- Use the `/prdf-diagram` skill -->
- Use mermaid to build architecture diagrams
- Choose between diagram type for
	- DB models
	- User flow
