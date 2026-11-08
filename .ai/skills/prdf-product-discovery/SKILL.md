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
- The product discovery, if not in bootstrap mode, should also include existing data in its product-domain-framework repo

# Instructions
- Follow the `../../instructions/BASE_INSTRUCTIONS.md` instructions
- Read the `product/INSTRUCTIONS.md` file, the `product/PRODUCT_INTRO.md` file, the `product/PRODUCT.md` file togather moreo context
- Prompt the user for the inputs mentioned above, do not insist, but ask the question so that the user feels compelled to give those sources
- Your output will be a temporary discovery file in markdown format, the user might ask to re-format it later or push it to another tool.
- Depending on the available sources for discovery, follow one or multiple of the following steps:

## From sources
- Check access to the required sources, either via web, or MCPs
- If the execution mode is autonomous, avoid asking the user any questions
- Visit the sources provided by the user and narrow down your search to the required subdomain
  - From those sources note any features or feature groups, the variations, sub-features and side-effects in the temp discovery file
  - Note any customer groups you manage to find, and feature variations they are tied to in the temp discovery file
- If you find any KPIs or metrics mentioned, note them down on the temporary discovery file too

## Live discovery
- For live discovery, you will require access to a live browser so you can act as the user
- Visit the sources mentioned by the user, impersonate a user, explore the apps and note down your findings
  - As in "From sources", note down features, dependencies you find, inconsistencies and bugs
