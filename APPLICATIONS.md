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

## Proposed product experiments

- **Prediction-market research:** triage whether a retrieved article is relevant
  to the exact question and settlement rules, or whether two venue listings may
  refer to the same contract. Keep source review and market mapping under human
  control. Draft experiment proposals are in the `pre-market-layer` project;
  no integration has been made.
- **AnqorFlow billing/support:** evaluate bounded intent routing or support
  evidence matching using approved, de-identified examples. Jev would not issue
  refunds, change subscriptions, or send messages. No integration or evaluation
  has been made.

## General boundaries

Use code for arithmetic, permissions, account state, and actions. Use a
judgment model only to provide a structured suggestion with an uncertainty or
review path. Evaluate each use case on its own representative, held-out data.
Check language coverage, privacy terms, and data-processing requirements before
sending non-public content to a hosted service.
