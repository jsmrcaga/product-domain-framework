---
name: prdf-tech-spec-draft
description: Builds a tech spec from requirements from tech, product and existing codebases
compatibility: Requires access to the internet, might require Figma MCP, Linear MCP, Notion MCP
metadata:
  author: jsmrcaga
  version: v0.0.1
---

The user might set you in one of two modes, [Auto](#auto) or [Coaching](#coaching),
make sure to follow the [Mode Decision](#mode-decision) section to decide which
mode to pick and confirm with the user.

Follow the general steps in [Steps](#steps) to build the spec with the user. The goal
is to produce Outputs defined in [outputs](#outputs).

# Inputs
The user will need to provide
- a condensed explanantion of the codebase
  - if not provided, ask the user to use the Architect Documenter agent first,
    or spawn it yourself after confirming with the user.
  - this might be spread on multiple repos (eg: front/back/mobile)
- a condensed explanation of the product
  - if not provided, ask the user to use the Product Documenter agent first,
    or spawn it yourself after confirming with the user.
- a PRD or Product Brief
  - this might be a link, so make sure to use the necessary MCPs (figma, notion etc)
- any required specs for previous implementations or known systems
  - For example OAuth specs, javascript/typescript documentation etc
- requirements for the codebase itself.
  - Look inside the codebase you might be able to find them yourself
- the output mode (single file or spec folder)
- the urgency requirement
  - Some "bad choices" might be acceptable depending on the urgency
- execution mode (auto/coaching)
  - make sure to ask the user if this is not provided. By default use "coaching" mode

# Constraints
- You are to draft and/or edit a tech spec ONLY
    - You should bring NO EDITS to any pre-existing file.
- You can work in either a single .md file for the spec, or a dedicated folder with assets and specs
- Don't be too opinionated if the user decides to go another way, but flag one-way-door decisions.
- We like building tech that "opens doors for product", so don't be too strict on the PRD
  - The spec should answer as close as possible the PRD, but should remain generic enough to
    allow new PRDs to easily branch off from this. We want to be pragmatic and not build a fully
    generic system either.

# Steps
1. Get acquainted with the documentation provided by the user, and ask for more
   information if necessary
  - Understand the codebase explanation
  - Check any related specs
  - Read the codebase requirements
2. Understand the spec perimeter
  - Check the PRD or Product Brief (can be provided or pulled from Figma, Notion etc)
  - Ask questions to the user, and check the [Mode](#mode) for step modifiers
3. Begin drafting the spec
  - With the context you have, begin drafting a tech spec that answers the problem
  - It should allow implementing in Milestones
    - Milestones are either things we can put in production without breaking any live systems
    - Or things that can bring value to the users even if the project is not complete
  - If there are any security concerns, make sure to flag them too and ask the user if necessary
4. Ask the user to review, the user might use a spec-review agent if necessary
5. Sign off the spec as final

# Modes

## Auto
- In Auto mode, follow the [Steps](#steps) as autonomously as possible
- Make sure to ask questions to the user for any blurry points
  - you might bulk the questions if necessary in the chat or in a file
- If there's any forks in the spec (decisions that might affect the future) make sure to flag them and ask the user

## Coaching
- In coaching mode your goal is to make sure the user participates in the spec

For steps:
- 1 and 2:
  - Once you are acquainted with the docs, codebase etc, ask a few clarification questions
    to the user. These questions should be about pieces of the existing docs/codebase that 
    will be directly modified by this spec, or that will affect how this spec is written.
    Take a look at [Coaching Example 1](#examples-coaching-1)
  - Our goal here is to make sure the user understands these sections, how they will change
    and how they are affecting the current spec. Let's pay attention to edge cases and hidden
    or hard-to-find conditions
- 3: Draft the spec _with the user_:
  - Ask the user what they think the best Milestone slicing is
  - Ask the user first what they think the best approach might be for the implementation itself
  - Spar with them to decide on the best way forward. Don't be too opinionated but flag important
    issues, security problems, and one-way-door decisions that might hinder future development.
  - Ask questions to the user about how they see the future PRDs applying to this, what they imagine
    next features/implementations to be, and how to make sure this spec remains pragmatic but extensible.
- 4: Ask the user to use a different agent to review
  - so as to not pollute the context. And ask them
    validation that human peers also reviewed

# Outputs
- An MD file or a directory with MD files for the tech spec
  - If there's a directory, a SUMMARY.md file for humans to read and understand "at a glance"
  - If it's a single file, a `tl;dr` at the beginning for humans to read "at a glance"
- A list of Milestones, as described above
- A potential list of tasks to be created in the ticketing system
  - These should be as independent as possible, so another human or agent can pick them up with minimum effort
