---
name: prdf-product-discovery
description: Builds a knowledge base for a given product or product-subdomain, using pre-existing knowledge, code-bases and user input.
compatibility: Requires access to the internet, might require Figma MCP, Linear MCP, Notion MCP, and a local browser MCP
metadata:
  author: jsmrcaga
  version: v0.0.1
---

This skill will help you perform product discovery on a given set of areas.
It might be used to perform product discovery to bootstrap a knowledge base,
to research competitors, to understand dependencies, or to improve metrics & KPIs.

# Execution mode
This skill might be executed as either
- An autonomous agent, in which case questions to the user _might not_ be possible.
- Directly from the user. In this case, human-agent sparring is not only encouraged, but also expected.

# Inputs
- Mandatory: The product description and the necessary subdomain (eg: SEPA Transfers on a NeoBank such as N26)
- The user may provide any existing sources, such as presentations, documents, notion pages, landing pages, PDFs etc
- The user may also provide a landing page or groups of pages, and a login/password set to try the product live from a browser
- Any existing user feedback, feature requests etc
- Use the task prompt to determine which sources and discovery modes are in scope. Bootstrap mode does not
  exclude relevant repository data; existing-PRD-only tasks must not perform live product exploration.

# Instructions
- Follow `.ai/instructions/BASE_INSTRUCTIONS.md` from the PRDF repository root unless it is already available in the current conversation.
- Ensure `product/INSTRUCTIONS.md`, `product/PRODUCT.md`, and `product/PRODUCT_INTRO.md` have been read and are available in context; reuse the owner's reads rather than rereading them. Do not treat unfilled template placeholders as facts.
- When running directly with the user, ask for the inputs mentioned above without insisting. When running as a delegated agent, use the provided context and report missing inputs to the parent rather than asking the user.
- When delegated, return the discovery report at the session-scratchpad path assigned by the parent. When invoked directly without an assigned path, return the report in the conversation unless the harness provides a scratchpad.
- Depending on the available sources for discovery, follow one or multiple of the following steps:

## From sources
- Check access to the required sources, either via web, or MCPs
- If the execution mode is autonomous, avoid asking the user any questions
- Visit the sources provided by the user and narrow down your search to the required subdomain
  - From those sources note any features or feature groups, the variations, sub-features and side-effects in the discovery report
  - Note known dependencies on other features, teams, systems, or prerequisites; distinguish confirmed dependencies from unknown or unstated ones
  - Note any customer groups you manage to find, and feature variations they are tied to in the discovery report
- If you find any KPIs or metrics mentioned, note them in the discovery report too

## Live discovery
- For live discovery, you will require access to a live browser so you can act as the user
- Visit the sources mentioned by the user, impersonate a user, explore the apps and note down your findings
  - As in "From sources", note features, dependencies, inconsistencies, and bugs in the discovery report
