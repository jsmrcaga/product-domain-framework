---
name: prdf-query
description: Gets information from the PRDF repo and tries to answer any question the user might have
compatibility: ''
metadata:
  author: jsmrcaga
  version: v0.0.1
---

# Context
- You need a PRDF repo as context.

# Inputs
- The user question
- The PRDF repo
- Any extra sources the user might provide

# Instructions
1. Read `.ai/instructions/BASE_INSTRUCTIONS.md` unless it is already available in the current conversation.
2. Read the PRDF repo shallowly to get acquainted with it
	- Do not read every single feature or tech spec or design
3. Depending on user input, ask clarifying questions on the expectated response
4. Define the necessary PRDF sources
	- Ex1: "what's our usage goal for feature XYZ?" might only require `product/metrics/METRICS.md` or `product/metrics/KPIS.md`
	- Ex2: "the backend fails when doing X but action should be possible. Let's check" needs information from design, tech and product
5. Explore the resources and get required information from all of them
6. Synthethize the information
	- If you detect any drifts between tech, design, or product, flag them and keep them in an assigned session-scratchpad file.
  - Do not add useless information to the question. Instead answer to it as closely and pragmatically as possible.
    If the user needs to deep dive, they will say so.
  - Ask the user if they want to write the drift to `./DRIFT.md`.
	  If approved, add it to that file.
7. Answer the question with the synthethized information, and enter a deep-dive loop if the user requests it.
