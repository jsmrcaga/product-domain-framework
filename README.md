<p align="center"><img src="./docs/assets/logo.png" height="150px"/></p>
<h1 align="center">Product-Domain Framework</h1>

This repo is a collection of LLM Agents and Skills to help
you and your team get better grasp on your product's domain.

PRDF is supposed to be your personal assistant and help you in
- Creating PRD and reviewing documents
- Distilling ideas and PRD into tech specs and reviewing them

This framework was inspired by Google's
[Elephant-Goldfish model](https://github.com/google/elephant-goldfish-model/tree/main),
and aims to extend it to get a product understanding, and simplifies it for teams to use.

<p align="center">
  <a href="#install">Install</a> &ensp;·&ensp;
  <a href="#quickstart">Quickstart</a> &ensp;·&ensp;
  <a href="#how-it-works">How it works</a>
</p>

# `tl;dr`
PRDF is a repo where you keep a version of your subdomain knowledge base.
It's meant for LLMs, not humans, to get an assistant for your team.

PRDF is not your source of truth, you keep using the tools you are used to,
and you need to keep PRDF up-to-date to fully exploit it.

Once bootstrapped, PRDF gives you an assistant to
- Write & Review Product Briefs and PRDs
   - Keeps tabs on edge cases, metrics, roadmaps, and user feedback
- Draft & ship for Product Design
   - Has an eye on System Designs, guidelines, user discovery
- Draft & Promote tech specs
   - Including actionable tasks for LLMs
   - And code review

# WIP
This project is wip. There is still much to do
- Product skills
- Tech skills
- Design skills

# Quickstart

## Install
- Clone this repo, and name it something related to your domain
- Ask Claude/Copilot/<your agent/> to install the skills
   - On Copilot you can also add the `.ai/skills` directory as a source using the `/skill` command

Always use the `/prdf-owner` skill as the agent you invoke.
Then ask it what you want to do, it will select the relevant skills for you

```sh
/prdf-owner let's do something
```

## First things first

You first need to bootstrap the repo. This should take around 1h per discipline.
Our suggestion is to
- start by bootstrapping Product
- boostrap Design and Tech afterwards
- Make a final pass to detect drift
- Send a Pull Request and review with your team

To start boostrapping, enter some basic info in either
`product/PRODUCT_INTRO.md` (or /tech or /design) and ask the
prdf-owner to help:
```sh
/prdf-owner let's bootstrap product
```

It should then guide you on bootstrapping, and spawn a few agents to
analyze your sources.

## Day-to-day usage

`/prdf-owner` should use you to the most adequate skill for your task,
but feel free to check what skills are available in `.ai/skills`.


```sh
/prdf-owner let's draft the tech specs for Feature X. My idea is a simple \
            queue with a worker process, i'm worried about the locking \
            mechanism in xyz though.
```

# Actions

You can perform any of these actions with the agents. Only one allowed at a time:
- Bootstrap: bootstrap the product, design, or tech sections.
   - You will have to provide information, sources, and answer questions. This MUST be first thing you do
- Edit: manually edit the knowledge base
   - Allows you to edit the knowledge base with something you learnt
- Draft: Draft an RFC for Product, Design or Tech
   - One of the most important pieces of the framework. Allows you to get an idea challenged and ready for human review
- Review: Review an RFC for Product, Design or Tech
   - Reviews a draft RFC with 0 context, and challenges everything it can
- Promote: Promote an RFC for product, design or tech
   - Moves an RFC from "Draft" to "Adopted" and moves the necessary pieces to their corresponding sections
- Implement: Implement a Product feature (tech), Analytics (Product) or Design (Design)
   - Performs the implementation steps of a spec with dedicated agents
- Query: needs an answer to a question pertaining to this subdomain
   - Checks the knowledge base (product/tech/design) and gets the answer
- Debug: the user might ask you to debug the Product-domain framework itself
   - For owners, allows debugging the framework to make it fit your workbase a bit better
   - This should only edit "user editable" files


# How it works
1. You start by defining your product's domain, how your product looks, the
   scope you are managing and the existing features.
2. With the help of one agent, you explore and define all the existing pieces
   of your domain. This will produce a "distilled" version that other agents can
   use, as well as documentation to help your team ask questions and prevent side-effects
   from new features and edge-cases.
3.
	1. Product teams can use another agent to spec new features, by taking into account usage,
       user feedback, ICP expansion etc.
   2. Tech teams can use agents to help spec the tech implementation, slicing and review for
       edge cases in the existing codebase
4. In the end, your team should have a repository with a distilled version of the team's knowledge,
   features in progress (design, product, tech) and a way to move forward efficiently.


> [!NOTE]
> This method is meant to _complement_ a human-first approach. Your team is expected to host
> workshops, review the PRDs, review the designs, review the tech specs before anything gets
> approved or sent into production.

# Conventions
* `README.md` files are for humans
* The folders `/product`, `/tech` and `/design` are meant to hold specifics of those areas
* Every folder has an `/rfc` folder for _in progress_ specs. Every RFC will be IDd with either a number, a date, or a version
   * Once approved, the RFC will be translated into the main repo

# Updates
Some of the files in this repo are not meant to be edited, since you
can pull from the original repo to update them.

# Usage

1. Clone this repo and rename it. It will become your knowledge base.
2. Install this repo in your workspace. The goal is to get the skills/agents into your preferred harness (Claude, Copilot, etc)
3. Then you will need to bootstrap this repo.
   Each discipline should bootstrap their own folder (design, product, tech).
   `Product` should be the first, since the other two will likely rely on it.
```sh
> /prd-bootstrap-product
```
```sh
> /prd-bootstrap-design
```
```sh
> /prd-bootstrap-tech
```
