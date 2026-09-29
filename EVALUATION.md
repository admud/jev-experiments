# Exploratory evaluation note

On September 20, 2026, the 12 synthetic cases produced 18 judgments across
support routing, claim verification, and search relevance. Jev matched all
handwritten expected labels and score anchors in that run. This is a plumbing
check on a tiny, handpicked set, not evidence of general accuracy or calibration.

The set includes straightforward examples and a few edge cases, but it does not
represent real users, languages, production class balance, or adversarial
coverage. The review thresholds are illustrative and were not tuned on held-out
data. No reviewer-blinded evaluation was performed.

An exploratory comparison with general models through OpenRouter was also run
on the same small set. Those runs had different timing, routing, and response
failure conditions. They are not a controlled benchmark and should not be used
to rank providers or estimate future production cost. The public repository
does not include raw requests, responses, provider metadata, or account-level
usage captures. Re-run the scripts with your own credentials if you want to
inspect current behavior.

Before any product use, create a representative, independently labeled,
held-out dataset; define the cost of false positives and review cases; evaluate
provider failures and repeatability; and review data handling for the specific
application.
