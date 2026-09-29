# Jev experiments

Small, synthetic experiments with Jev (TypeSafe) for structured classification,
yes/no judgments, and rubric scoring. Python 3 standard library only.

12 synthetic cases, 18 judgments:

| Example | Primitive | Evaluation |
| --- | --- | --- |
| Support routing + human handoff | Choice + Noul in one request | Category accuracy, binary accuracy, Brier score |
| Claim verification against a supplied source | Choice | Supports / contradicts / unknown accuracy |
| Search relevance | Score with levels 0–2 | Mean absolute error and fraction within 0.5 of the target |

Cases include negation, missing information, a message attempting to override the classifier, unsupported claims, and a partially relevant passage. Labels are manually specified in `examples()` and excluded from requests.

## Run

```bash
cd jev-experiments
python3 evaluate.py --dry-run
python3 evaluate.py --ask-key
# Or use an existing TYPESAFE_API_KEY environment variable:
python3 evaluate.py
# Run just one example:
python3 evaluate.py --group claims
```

`--ask-key` reads the key without displaying it or saving it. Environment files are not loaded automatically. A live run sends the synthetic cases to TypeSafe and incurs API usage. The default model is pinned to `jev-1.13.0`; override with `--model`.

`compare_openrouter.py` also sends the synthetic cases to OpenRouter, incurs usage for each model request, and saves local raw responses. It is retained for reproducibility, but comparative results are not published as a ranking.

The live runner makes at most 12 sequential requests, with up to two retries for 429/529 errors. It writes local run artifacts under `results/`; these may include prompts, labels, and provider responses and are intentionally excluded from version control. Dry-run payloads are also local.

## Interpret results

Choice and Score answers below 0.8 confidence are marked for review. Noul answers between 0.2 and 0.8 are marked for review; binary accuracy uses a 0.5 decision boundary. These are illustrative thresholds, not tuned production policies. Review labels simulate routing; they do not contact anyone or perform actions.

Automatic coverage and accuracy describe only answers outside the review band. Score targets are subjective rubric anchors; the 0.5 tolerance is an exploratory choice. Brier score measures squared probability error (lower is better). Twelve handpicked cases cannot establish calibration, general accuracy, or production readiness. Latency includes network overhead and retries; it is not a controlled benchmark. Use held-out representative data before tuning prompts or thresholds.

## Limits

These are handpicked synthetic examples for integration exploration. They do not
establish production accuracy, calibration, safety, or a model ranking. Do not
send personal, customer, confidential, or account data without an approved data
handling review. See [APPLICATIONS.md](APPLICATIONS.md) for the product areas
considered so far and their current status.

## Documentation consulted

- https://docs.typesafe.ai/api
- https://docs.typesafe.ai/primitives/choice
- https://docs.typesafe.ai/primitives/noul
- https://docs.typesafe.ai/primitives/score
- https://docs.typesafe.ai/cookbooks/citation_check
- https://docs.typesafe.ai/models
