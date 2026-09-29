# Where Jev may fit

This is a high-level map of product ideas discussed during the experiments. It
does not claim that Jev has been integrated into any of these products.

## Explored with synthetic examples

- **Support routing:** choose a support category and detect an explicit or
  indirect request for a human. This is the subject of the runnable synthetic
  example in this repository.
- **Claim checking:** compare a claim with a supplied passage and return
  supports, contradicts, or unknown. Also covered by the synthetic example.
- **Search relevance:** score whether a passage answers a query. Also covered by
  the synthetic example.

These examples establish only that the API integration and evaluation harness
work on the included cases.

## General use-case patterns

The following are candidate patterns, not claims of measured performance or
recommendations to enable them in production. Each should be tested against a
representative, independently labeled dataset for its own domain.

| Pattern | Possible judgment | Keep deterministic or human-controlled |
| --- | --- | --- |
| Request triage | Route a message to a bounded category; detect when a person is requested | Account lookup, escalation delivery, and customer-facing actions |
| Evidence matching | Decide whether a supplied excerpt supports, contradicts, or leaves a statement unresolved | Source selection, citations, and final approval |
| Search and retrieval | Rank whether a candidate result answers a query or matches a stated scope | Retrieval, access controls, and result disclosure |
| Duplicate detection | Judge whether two records likely refer to the same underlying item | Canonical IDs, merges, and deletion |
| Form and document review | Flag missing, inconsistent, or out-of-scope information against a rubric | Required-field validation, policy enforcement, and acceptance |
| Content quality review | Check whether generated text follows a brief, tone guide, or required structure | Factual verification, publication, and legal or safety approval |
| Conversation handoff | Detect unresolved intent, low confidence, or a request for escalation | Handoff execution and service-level commitments |
| Feedback and survey analysis | Group comments by topic or sentiment and identify ambiguous responses | Statistical reporting, personnel decisions, and individual outcomes |

Start with shadow evaluation or human review. Keep the judgment bounded to the
provided context, define an abstain/review path, and measure false positives,
false negatives, latency, and cost before relying on outputs. Avoid sending
personal or confidential content until data handling is approved.

## General boundaries

Use code for arithmetic, permissions, account state, and actions. Use a
judgment model only to provide a structured suggestion with an uncertainty or
review path. Evaluate each use case on its own representative, held-out data.
Check language coverage, privacy terms, and data-processing requirements before
sending non-public content to a hosted service.
