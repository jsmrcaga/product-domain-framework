# Product Instructions

## Folder structure

- /assets
	- Any assets used for describe features or feedback, such as diagrams, screenshots...
- /metrics
	- /KPIS.md: the KPIs defined with the user. They require a short name, a source, a justification, a target, a "current value" (dated) and a strategy to improve
	- /METRICS.md: any metrics used to measure the feature. They require a name, source, justification.
- /feedback
	- /SOURCES.md: contains the places where feedback can be found (eg: intercom, slack...)
	- /TRIAGE.md: any recently discovered feedback not added to the /features yet
- /features: will contain multiple folders for every feature
	- /<featurename>
      - KNOWN_FEEDBACK.md: triaged feedback from the /feedback section.
      - METRICS.md: Specific metrics used to measure this feature, with current values, targets, names, justification
      - FEATURE.md: the description of the feature itself, edge cases, variations, target users etc...

# Actions

For all actions:
- read the `PRODUCT.md` document, if empty fallback to the `./PRODUCT_INTRO.md` document

## Bootstrap
- Use the `prdf-product-bootstrap` skill directly.

## Edit
- Use the `prdf-edit` skill directly.
- Do not spawn a separate agent

## Draft
- Use the `prdf-product-prd-draft` skill

## Review
- NOT IMPLEMENTED YET

## Promote
- NOT IMPLEMENTED YET

## Implement
- NOT IMPLEMENTED YET

## Debug
- NOT APPLICABLE HERE
