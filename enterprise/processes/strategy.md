# Strategy Team Process

Every strategy engagement at a company using AgentForce enterprise teams follows this
process. The goal is decisions a board member could interrogate: where to play, how to
charge, and how to grow — each backed by dated evidence, with the rejected options
named.

## Overview

```
                          ┌────────────────────────────────────────────┐
                          │      /strategy engagement pipeline         │
                          └────────────────────────────────────────────┘

  docs/enterprise/foundation.md            (company foundation — shared, all teams)
  docs/enterprise/strategy/foundation.md   (competitors, category, pricing, motion today)
          │
          ▼
  ┌───────────────┐   ┌───────────────┐   ┌───────────────┐   ┌───────────────┐
  │  --landscape  │──▶│   --market    │──▶│   --pricing   │──▶│   --growth    │
  │ competitor map│   │ category+TAM  │   │ value metric, │   │ motion, north │
  │ dossiers,     │   │ bottom-up,    │   │ tiers, price  │   │ star tree,    │
  │ watch list    │   │ trends        │   │ positioning   │   │ AARRR leaks   │
  └───────────────┘   └───────────────┘   └───────────────┘   └───────────────┘
          │                   │                   │                   │
          └───────────────────┴────────┬──────────┴───────────────────┘
                                       ▼
                    dated artifacts in docs/enterprise/strategy/
                                       ▼
                 PR: "docs: strategy <mode> review package" (human review)
                                       ▼
              external execution: founder decides; handoffs to
              /marketing (positioning), /finance (WTP study), /sales (battle cards)
```

Each mode cites the ones before it. Prerequisites are soft: `/strategy` warns and
offers to run the missing prerequisite, but never hard-blocks.

## Phase 1 — Foundation

Two docs, created on first run, reused by every engagement:

- `docs/enterprise/foundation.md` — company-wide: product, stage (team/revenue/funding),
  business model and pricing today, target customer hypothesis, geography and
  constraints. Shared with all enterprise teams.
- `docs/enterprise/strategy/foundation.md` — strategy baseline: named competitors
  (including "do nothing"/DIY), current category framing, pricing today, growth motion
  today, instrumented metrics, strategy history (pivots, prior pricing changes).

Both carry a dated header and a `Last reviewed: <date>` line. **Refresh rule:** if a
foundation doc is >90 days old at the start of any engagement, the skill notes it and
offers a refresh before proceeding. Competitive facts inside artifacts follow the same
90-day staleness flag (HIGH-threat competitors: 30 days, per the watch list).

## Phase 2 — Engagements

| Mode | When to run it | What it produces | Prerequisite |
|------|----------------|------------------|--------------|
| `--landscape` | First, and whenever a watch-list trigger fires or a deal is lost to a competitor | `competitive-landscape-<date>.md` (map, dossiers, watch list); optional `teardown-<competitor>-<date>.md` | Foundation only |
| `--market` | Before positioning work, fundraising, or any category/naming decision | `market-category-tam-<date>.md` (category decision, bottom-up TAM/SAM/SOM, trends) | `--landscape` (soft) |
| `--pricing` | Before first pricing, and every 6–12 months after (startups systematically underprice) | `pricing-strategy-<date>.md` (value metric, tiers, positioning, discount policy, WTP study spec) | `--market` (soft) |
| `--growth` | Before scaling any acquisition spend, and quarterly to re-run the leak analysis | `growth-model-<date>.md` (motion, north-star tree, AARRR leaks with plays, efficiency gates) | `--pricing` (soft) |

Every engagement runs the same internal phases: foundation check → mode selection →
discovery → execution → adversarial consultant review (Amir) → quality gates + verdict →
persist and hand off. The consultant review is never skipped.

## Phase 3 — Commit artifacts

All artifacts live in `docs/enterprise/strategy/` with dated filenames:

```
docs/enterprise/strategy/
├── foundation.md
├── INDEX.md                              (one line per artifact: date, mode, link, gate)
├── competitive-landscape-2026-07-06.md
├── teardown-<competitor>-2026-07-06.md
├── market-category-tam-2026-07-12.md
├── pricing-strategy-2026-07-20.md
└── growth-model-2026-08-01.md
```

The date in each filename and document header is the audit trail — it proves the work
happened and when. Do not remove or change these dates. A re-run produces a NEW dated
file; it never overwrites a prior one. INDEX.md is updated on every engagement.

## Phase 4 — Human review & approval

- Commit artifacts on a branch and open a PR titled
  `docs: strategy <mode> review package`.
- Review-gate legend (each artifact declares one in its header):
  - **AI-final** — facts sourced and dated; no decision embedded (landscape default).
  - **Human review recommended** — commits money or direction; founder reads and
    approves (market, pricing, growth default).
  - **Licensed professional required** — rare for strategy; e.g. pricing mechanics with
    legal exposure (price discrimination, MFN clauses) route to an attorney.
- Nothing externally binding — publishing a pricing page, committing a growth target to
  investors, announcing a category — happens until the PR is approved.

## Phase 5 — External execution

The PR merge unlocks the human to-do checklist each artifact ends with. Standard routing:

- Category decision + competitive alternatives → `/marketing` positioning canvas;
  pricing page copy → `/marketing`.
- WTP study spec → `/finance --pricing-study` (Van Westendorp / Gabor-Granger execution and
  revenue-impact model).
- Competitor dossiers → `/sales` battle cards (with last-verified dates carried over).
- Pricing page publish, price-change announcements, investor commitments → humans only.
- Afterwards the team monitors: watch-list re-check dates, the north-star tree's
  instrumentation plays, and pricing exception logs — each feeds the next engagement.

## Operating cadence

- **Monthly (30 min):** watch-list sweep — re-check HIGH-threat competitors; fire any
  triggered re-research.
- **Quarterly:** re-run `--growth` leak analysis against fresh funnel numbers; review
  the discount exception log.
- **Every 6–12 months:** `--pricing` revisit (calendar it at each pricing artifact's
  creation).
- **Event-driven:** competitor ships a fence feature, changes price, or raises →
  scoped `--landscape` re-run; lost deal to a competitor → dossier update; category
  confusion in 3+ sales conversations → `--market` re-run.

## FAQ

**When do I actually need a human strategy consultant?**
When the decision is a bet-the-company one-way door: a pivot, a category creation with
years of education spend, or a pricing change touching most of your ARR. `/strategy`
gives you the evidence pack and a recommendation; a human advisor adds pattern-matching
on your specific investors, market relationships, and risk appetite.

**Can I skip the review PR?**
Only for internal-only drafts (a scratch TAM estimate, an exploratory teardown). Never
for anything customer- or investor-facing: pricing changes, category announcements,
growth targets. Those are binding once spoken.

**Can the AI just set our prices?**
No. It designs the pricing strategy, runs the underpricing math, and writes the study
spec. A human approves the numbers and presses publish. Price changes are hard to
reverse with customers.

**The landscape is 4 months old — is it still usable?**
No fact older than 90 days should drive a decision. Run the watch-list sweep first
(fast), then re-run `--landscape` scoped to the competitors that changed.

**Why is the TAM smaller than the analyst report says?**
Because it is bottom-up: countable buyers × realistic price. That is the number
sophisticated investors trust. Cite the analyst top-down figure only as a labeled
cross-check.

**Do I have to run the modes in order?**
The order (landscape → market → pricing → growth) exists because each cites the last.
The skill warns and offers, but if you need pricing today, run `--pricing` — the gaps
get flagged in the artifact rather than silently ignored.
