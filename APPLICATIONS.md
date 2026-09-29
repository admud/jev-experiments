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
  control. No integration has been made.
- **Subscription support:** evaluate bounded intent routing or support evidence
  matching using approved, de-identified examples. Jev would not issue refunds,
  change subscriptions, or send messages. No integration or evaluation has been
  made.

## Faith and reference assistant (anonymized)

Jev has been integrated into a reference assistant behind per-feature flags
that default off. The judgment layer fails open and does not write answers.
Merged work covers cache matching, front-door triage, multilingual verdict
checks, reference-library question checks and passage selection, greeting and
gibberish triage, and relevance ordering for keyword-search results.

Separate follow-up experiments explored offline relevance judgments,
end-to-end answer flow, latency, passage selection, and source-library routing.
Those experiments are on an unmerged development branch and are not part of the
merged integration. Treat their results as exploratory: datasets and runs are
small, latency and cost depend on the environment, and one comparison found a
Jev-only speculative writer less reliable than no-Jev and hybrid approaches.

In one limited 13-question passage-selection comparison, Jev and the existing
selector chose the same passages 82% of the time; median selection time was
0.4 s for Jev and 2.5 s for the existing selector. This does not establish
general quality or production readiness. Enabling the integration sends user
questions and draft text to the hosted provider, so data-handling settings
should be reviewed before enabling any feature.

## General boundaries

Use code for arithmetic, permissions, account state, and actions. Use a
judgment model only to provide a structured suggestion with an uncertainty or
review path. Evaluate each use case on its own representative, held-out data.
Check language coverage, privacy terms, and data-processing requirements before
sending non-public content to a hosted service.
