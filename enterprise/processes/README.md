# Enterprise Team Processes

One process document per team — the enterprise analogue of a development process doc
(discovery → artifacts → review PR → execution), adapted to each business domain.

The **company-level** process — which order to run the teams for a new product, what a
single-team engagement looks like, the change-propagation matrix, and what triggers a
board pass — lives one level up in [../PROCESS.md](../PROCESS.md). This directory is the
per-team detail beneath it.

Every process shares the same skeleton:

```
Foundation docs → Engagement modes (natural order) → Dated artifacts in docs/enterprise/<team>/
        → Human review PR ("docs: <team> <mode> review package") → External execution → Cadence
```

And the same three iron rules:

1. **Dated artifacts are the audit trail.** Every artifact filename and header carries the
   date it was produced. Do not remove or change these dates — they prove what was known and
   reviewed, and when.
2. **Nothing externally binding ships before the review PR is approved.** Drafts can iterate
   freely on a branch; sending, signing, filing, or publishing anything customer- or
   authority-facing waits for human approval of the review package.
3. **Review gates are explicit.** Every artifact is classified `AI-final`,
   `Human review recommended`, or `Licensed professional required (attorney / CPA / broker /
   auditor)` — and the classification is printed on the artifact itself.

| Process | Team skill |
|---------|-----------|
| [strategy.md](strategy.md) | `/strategy` |
| [marketing.md](marketing.md) | `/marketing` |
| [sales.md](sales.md) | `/sales` |
| [legal.md](legal.md) | `/legal` |
| [compliance.md](compliance.md) | `/compliance` |
| [finance.md](finance.md) | `/finance` |
| [people.md](people.md) | `/people` |
| [customer-success.md](customer-success.md) | `/customer-success` |
| [bizops.md](bizops.md) | `/bizops` |

`/exec-review` has no process doc of its own: it is the review gate the other processes call
for cross-domain plans, and the natural final step before a review PR is opened.
