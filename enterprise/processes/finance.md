# Finance Team Process

Every finance engagement at a company using AgentForce enterprise teams follows this process.
The goal is board-grade numbers with a full audit trail: one canonical definition per metric,
every figure traceable to a source, and licensed-professional boundaries respected.

## Overview

```
┌────────────────┐    ┌──────────────────────────────────────────────┐
│  FOUNDATION    │    │  ENGAGEMENTS (natural order)                 │
│  company doc   │───▶│  --model ▶ --metrics ▶ --runway ▶            │
│  finance doc   │    │  (--pricing-study | --raise | --board)       │
│  (90-day       │    │  --finops: any time                          │
│   refresh)     │    └──────────────────┬───────────────────────────┘
└────────────────┘                       │ dated artifacts
                                         ▼
                     ┌──────────────────────────────────────────────┐
                     │  docs/enterprise/finance/<slug>-<date>.md    │
                     │  + INDEX.md                                  │
                     └──────────────────┬───────────────────────────┘
                                        │ PR: docs: finance <mode> review package
                                        ▼
                     ┌──────────────────────────────────────────────┐
                     │  HUMAN REVIEW & APPROVAL (review gates)      │
                     └──────────────────┬───────────────────────────┘
                                        │ approved
                                        ▼
                     ┌──────────────────────────────────────────────┐
                     │  EXTERNAL EXECUTION (humans only: build the  │
                     │  sheet, send the deck, engage CPA/appraiser, │
                     │  change billing, wire money)                 │
                     └──────────────────────────────────────────────┘
```

## Phase 1 — Foundation

Two documents anchor every engagement:

- `docs/enterprise/foundation.md` — company foundation: product, stage (team size,
  revenue/ARR, funding), business model and pricing today, target customer, geography and
  constraints.
- `docs/enterprise/finance/foundation.md` — finance foundation: cash, gross/net burn
  (3-month basis), billing system and contract mix, **the ARR definition in use**, accounting
  setup and last closed month, cap table location and SAFE stack, tax posture (entity, nexus
  states, R&D credit status), existing artifacts and reporting cadence.

Both carry a dated header and `Last reviewed: <date>`. **Refresh rule: any foundation doc
older than 90 days gets flagged at the start of a run and offered a refresh.** Stale cash and
burn numbers silently poison every downstream artifact — the refresh is not optional
housekeeping.

## Phase 2 — Engagements

| Mode | When to run it | What it produces | Prerequisite |
|------|----------------|------------------|--------------|
| `--model` | No operating model exists, or the old one no longer describes the business | Tab-by-tab model spec + assumptions CSV + sanity-check results | Foundation docs |
| `--metrics` | Monthly, and before any board/raise work | KPI page with canonical definitions, computations shown, benchmarks cited | Data source (billing export or model) |
| `--runway` | Monthly, and whenever cash strategy is in question | Burn/runway analysis, levers table, fundraise-by date | The three numbers, 3 months of actuals |
| `--pricing-study` | Realization is slipping, NRR is flat, or a packaging change is on the table | Pricing study memo: WTP research, packaging grid, revenue impact, migration plan | `--metrics` (soft); `/strategy --pricing` for the strategic layer |
| `--raise` | 9–12 months before zero-cash | Deck outline with content, data room gap checklist, SAFE dilution math, term-sheet comparison | `--model` + `--metrics` (soft) |
| `--board` | Quarterly (deck) and monthly (investor update) | Board deck draft, investor update draft, BvA package | Frozen budget for BvA; `--metrics` (soft) |
| `--finops` | Quarterly, or when the cloud bill jumps | Cloud cost audit with rightsizing recommendations and margin impact | Repo access; billing export improves it |

Prerequisites are enforced softly: the skill warns and offers the prerequisite mode first,
but never hard-blocks.

## Phase 3 — Commit artifacts

Artifacts land in `docs/enterprise/finance/`:

```
docs/enterprise/finance/
  foundation.md
  INDEX.md                                # one line per artifact: date, mode, link, review gate
  operating-model-spec-2026-07-06.md
  model-assumptions-2026-07-06.csv
  kpi-page-2026-07-06.md
  runway-analysis-2026-07-06.md
  board-pack-2026-Q3.md ...
```

**The date in each filename and document header is the audit trail — it proves the work
happened and when. Do not remove or change these dates.** Superseded artifacts stay in place;
INDEX.md marks them superseded and links the replacement.

## Phase 4 — Human review & approval

Open a PR titled `docs: finance <mode> review package` containing the artifacts and the
INDEX.md update.

Review-gate legend (every artifact header carries one):

- **AI-final** — usable as-is (internal KPI pages, FinOps audit reports).
- **Human review recommended** — a founder/operator reads and owns it before use (model spec,
  runway analysis, board deck, pricing memo).
- **Licensed professional required (<which>)** — CPA/EA (tax positions, rev-rec policy,
  accounting policy memos), independent auditor (anything labeled reviewed/audited),
  qualified appraiser (409A inputs), securities attorney (financing documents).

**Nothing externally binding — sending a deck, publishing prices, filing anything, signing
anything — happens until the PR is approved.**

## Phase 5 — External execution

The handoff summary in every engagement ends with a human to-do checklist. Typical items and
where they execute:

- Build the spreadsheet from the model spec; confirm the balance-sheet check row is zero →
  Excel/Sheets. The team maintains the spec; the human owns the live file.
- Approve budget, option grants, 409A engagement → board meeting (fiduciary, human only).
- Engage CPA for filings, R&D credit, sales-tax registrations → the team's tax calendar and
  data packages go with them.
- Send the investor update / board pack (48–72h before the meeting) → email.
- Apply pricing changes → billing system (Stripe/Chargebee), with the migration comms plan.
- Execute rightsizing → cloud console, after reliability trade-offs are accepted.
- Wires, signatories, insurance → humans, always.

Afterwards the team monitors: BvA against the frozen budget monthly, runway monthly,
pricing-change churn/win-rate triggers per the memo's rollback section, cloud bill vs. the
FinOps estimate.

## Operating cadence

- **Monthly** (within 10 business days of close): close-quality check → `--metrics` refresh →
  BvA → investor update draft → runway re-check.
- **Quarterly**: board pack (`--board`), `--finops` audit, benchmark refresh on the KPI page.
- **Annually** (Oct–Dec): annual plan — bottoms-up budget via `--model` refresh, board
  approval freezes the budget for next year's BvA.
- **Event-driven**: `--raise` at 9–12 months of runway; 409A data package after any material
  event; `--pricing-study` when realization or NRR says so.

## FAQ

**When do I actually need a human CPA?**
Tax filings and positions, R&D credit certification, rev-rec policy decisions, audit/review
opinions, and any accounting policy memo before it governs real books. The team drafts the
package; the CPA signs. For equity: 409A needs an independent qualified appraiser; financing
docs need a securities attorney.

**Can I skip the review PR?**
Only for internal-only drafts (a KPI page you alone read). Never for anything
investor-facing, board-facing, customer-facing (pricing), or authority-facing (tax).

**The model and the billing system disagree on ARR. Which wins?**
The billing system is the source of truth for actuals; the model must tie to it. If they
diverge, that's a `--metrics` reconciliation engagement, not a judgment call.

**Can the budget be updated mid-year so BvA looks better?**
No. The budget is frozen at board approval; the rolling forecast is the living view.
Re-baselining the budget is forecast theater and the skill will refuse.

**How current are the benchmarks in these artifacts?**
Encoded frameworks are stable; numeric benchmarks are refreshed via WebSearch at run time and
cited with source + year. If an artifact is older than a quarter, re-verify its benchmarks
before reusing them.

**Do I really need the downside case?**
Yes. The downside case (churn up + sales down + collections slow, simultaneously) produces
the zero-cash date you plan hiring and fundraising around. "Base minus 10%" is not a plan.
