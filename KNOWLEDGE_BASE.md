# Knowledge base

## Global

The `MAIN.md` file will contain instructions on how to read files from this
repository, and will get updated on RFC promotions etc.

## Editability
You MUST NOT edit any of these files, ever:
- Any README.md file
- The CUSTOM_INSTRUCTIONS.md file
- Any of PRODUCT_INTRO.md, DESIGN_INTRO.md, or TECH_INTRO.md
- Any file in the `.ai` directory
- Any file in the `.github` directory


## Product

### Structure
```
/product
- /rfc (the ongoing PRDs)
   - /rfc-<id>-<title> (folder including assets etc for this rfc)
      - /assets
      - PRODUCT_RFC.md
- /assets (assets for features/feedback etc)
- /features
   - /feature_1
      - KNOWN_FEEDBACK.md
      - METRICS.md
      - FEATURE.md
   - /feature_2
   - ...
- /feedback
   - SOURCES.md (feedback sources, might be updated by humans or agents)
   - TRIAGE.md (feedback that needs to be triaged into one or multiple features)
- /metrics
   - METRICS.md (list of interesting metrics and sources (mixpanel, dbs...))
   - KPIS.md (list of product KPIs, and relation to metrics - must be deterministic)
- ./INSTRUCTIONS.md (holds custom instructions to write PRDs, sync to Notion etc)
- ./PRODUCT.md (tl;dr for agents on how to find information in this folder)
- ./README.md (human readable, editable file)
```

## Design

### Structure
```
/design
- /rfc (the ongoing Designs)
   - /rfc-<id>-<title> (folder including assets etc for this rfc)
      - /assets
      - DESIGN_RFC.md
- /assets (assets for features/feedback etc)
- /features
   - /feature_1
      - SOURCE.md (source, figma, etc...)
      - DESIGN_CHOICES.md
   - /feature_2
   - ...
- /design-system
   - DESIGN_SYSTEM.md (design system sources, directions, custom instructions)
- ./INSTRUCTIONS.md (holds custom instructions to help design/review, sync to Figma etc)
- ./DESIGN.md (tl;dr for agents on how to find information in this folder)
- ./README.md (human readable, editable file)
```

## Tech

### Description

Holds the Tech knowledge base.
The knowledge base is mostly based on the entire code-base of the subdomain's system,
this is likely a combination of multiple repositories, multilpe technologies, front-end,
back-end, infra, etc.

The tech knowledge base will distill the information about the codebase in the /tech/codebase folder,
that will be split by features.

Any org-wide ADRs or guidelines should be stored in the GLOBAL_GUIDELINES.md file.

### Structure
```
/tech
- /rfc (the ongoing RFCs)
   - /rfc-<id>-<title> (folder including assets etc for this rfc)
      - /assets
      - TECH_RFC.md
- /architecture
   - /global (global system architecture, includes other teams, IAM, etc)
      - GLOBAL_ARCH.md
   - /domain (product-domain architecture, more specific and detailed than global)
      - /diagrams (architecture diagrams, must be updated with RFC promotion)
   - ARCHITECTURE.md (tl;dr of the architecture)
- /codebase
   - /features (holds the features and where they interact in the codebase)
      - FEATURE.md
   - /repos (holds the list of repos with descriptions of what they hold, ownership and interesting sections)
      - /repo_1
         - REPO.md
   - CODEBASE.md (references and sources to the codebase, used to explore the actual codebase)
- /data-model
   - DATA_MODEL.md ()
- /globals
   - PROVIDERS.md (list of providers the specs must use, eg: Stripe, Segment, FusionAuth, Okta... etc)
- ./GLOBAL_GUIDELINES.md (holds orgnaization-wide guidelines such as golden path, security, certifications...)
- ./INSTRUCTIONS.md (holds custom instructions to write RFCs)
- ./TECH.md (tl;dr for agents on how to find information in this folder)
- ./README.md (human readable, editable file)
```
