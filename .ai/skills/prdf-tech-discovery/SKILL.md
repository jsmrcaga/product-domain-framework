---
name: prdf-tech-discovery
description: A skill to perform discovery on a collection of code-bases/repositories and tech sources
compatibility: Might require access to GitHub/GitLab/Bitbucket, local codebase too. Might require access to Notion, Figma and other MCP servers
metadata:
  author: jsmrcaga
  version: v0.0.1
---

This skill will allow you to gather information about a tech system from
a list of sources provided by the user or parent agent.

This skill is still WIP.

# Inputs

- The product subdomain we are interested in
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
- The user should provide any guidelines such as certifications (eg: ISO27001), security, golden-paths etc.
- Some extra information and context about the product and dependencies might be provided

# Instructions

0. Read `.ai/instructions/BASE_INSTRUCTIONS.md` unless already available in the current conversation. Use the user/parent-provided scope and follow its source-handling, context-handoff, and report-output rules.
1. When working directly with the user, clarify missing scope or source information. When delegated, do not ask the user; report missing inputs to the parent.
2. Divide the work by source type:
	- Architecture & diagrams
	- Codebase
	- Data model (record it with the architecture or codebase findings)
	- RFCs/specs
3. Start with architecture and diagrams, then codebase, then RFCs/specs when provided.
4. When delegated, write the report to the assigned path and communicate that path and any unavailable sources to the parent. When invoked directly without an assigned path, return the report in the conversation unless the harness provides a scratchpad.

# Architecture & Diagrams
- Visit all sources for architecture
- Craft a synthesized version making sure to flag
	- What is "global arch" (IAM, clouds/hosting, permissions/roles)
	- Direct dependencies of our subdomain
	- Data models and interactions relevant to the subdomain
	- Add more detail into everything related to our subdomain

# Codebase
- Start by listing all codebases you need to visit
- Try to match them to the architecture you found above, and
  plan a visit that will save you time. Otherwise, plan to visit them in an order
  provided by the user
- For each codebase
	- Traverse the codebase BFS (breadth-first search), checking the "domain" each folder belongs to
	- Check the files and mark the general domain they pertain to, keep a tab
	- For every folder that is directly owned by our subdomain, add information
	  about the features, variations and edge-cases you find.
	- From the tabs you kept, keep a record of the dependencies to our subdomain

# RFCs/Specs
- Visit all RFC and Spec sources
- Read them, and map them back to Architecture & Codebase findings
- Add any missing information, and flag any drift
