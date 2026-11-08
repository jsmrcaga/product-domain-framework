---
name: prdf-product-bootstrap
description: This skill helps bootstrapping the necessary information for subsequent agents and humans to get answers about the product and built a comprehensive and almost-exhaustive knowledge base about the particular subdomain they want.
compatibility: Requires the rest of product-domain skills
metadata:
  author: jsmrcaga
  version: v0.0.1
---

This skill aims to build the initial knowledge base for `/product`.

It will use some other skills in different ways in order to do so, and
will require a lot of input from the user.


# Inputs
> Inputs in brackets are optional

- Base description: a base description of the entire product and the sub-domain
	we are interested in
- [Online visitable product pages/app:] the app itself, or the landing page for the product
- Existing PRDs, Product Briefs, designs of the product
- Clear state of what exists, what has been deprecated, and what is planned
- Existing roadmap
- Sources for metrics
- Existing KPIs


# Instructions

- Go through all the steps outlined below:
	- Clarification points
	- Validation
	- Delegation
	- Consolidation & Bootstrapping

## Clarification points

- Start by asking the user clarification questions on the product
	- The file /product/OUT_OF_SCOPE.md is used to store product information
    from other bounded contexts
- Ask the user to fill the PRODUCT_INTRO.md file. They have a choice to skip it
	- If they agree, wait for them to fill it up and continue once they approve
- Ask the user for a way to log-in to the actual product, and how to explore the app and the landing page
- Ask the user to provide any sources that could have product knowledge, for example
	- Notion documents
	- Discovery PDFs
	- Presentations
	- Roadmaps
- Ask the user about the existing KPIs, metrics and their sources

## Validation
- Validate you have enough information to go on, otherwise ask the user for more information
- Keep the questions simple, and ask one question at a time to keep the user engaged
- Once you have enough information write:
	- a `tl;dr` section on the `/product/PRODUCT.md` file
    This section should contain the synthesis of what the product subdomain is, any dependencies etc.
  - For all features you discovered, add the corresponding features in the `product/features` folder,
    respecting the format defined in the `KNOWLEDGE_BASE.md` file (FEATURE.md is used to describe the feature. Follow the template in product/assets/templates).
  - If there is information about KPIs, and product metrics, add them to the corresponding `/product/metrics/*` files.
  - If there is enough information on user feedback, add it to the corresponding `/product/feedback/*` files.
- Now move to [Delegation](#delegation)

## Delegation
- Read the necessary skills for delegation to run, and make sure you have enough information
  to trigger them autonomously. We are assuming they will not be able to ask the user questions, so it's
  on you to gather the necessary information.

- Spawn agents behind the scenes to
	- Explore live product. Use the `/prdf-product-discovery` skill, adding a prompt to indicate
	  that this is a comprehensive discovery, and the agent should explore all areas of the sub-domain.
	  The agent should report back with its findings in a temporary file.
	- Explore existing PRDs using the `/prdf-product-discovery` skill. Add a prompt to use the existing data
		and prevent any live discovery.
		The agent should report back with its findings in a temporary file.

## Consolidation & Bootstrapping
- Your job now is to consolidate all the reported data from the agents in memory.
- From this data write any /product files following the knowledge base and templates
