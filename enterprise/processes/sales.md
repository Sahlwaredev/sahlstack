# Sales Team Process

Every sales/GTM engagement at a company using AgentForce enterprise teams follows this
process. The goal is a repeatable revenue system: evidence-based targeting, buyer-verified
pipeline, and a forecast a founder can defend — with humans owning every conversation,
price decision, and signature.

## Overview

```
                         ┌──────────────────────────────┐
                         │  Foundation                  │
                         │  company + sales docs        │
                         └──────────────┬───────────────┘
                                        │
          ┌───────────── build the system ─────────────┐
          ▼                    ▼                        ▼
      --icp  ───────────►  --playbook  ──────────►  --outbound
   (who we sell to)     (how we sell)          (how we start deals)
          │                    │                        │
          └────────────┬───────┴────────────────────────┘
                       │  run the system (recurring)
              ┌────────┴─────────┐
              ▼                  ▼
         --pipeline          --deal
      (weekly hygiene     (per-deal MEDDPICC
       + forecast)         + MAP + biz case)
                       │
                       ▼
        artifacts → docs/enterprise/sales/ (dated)
                       │
                       ▼
        human review PR: "docs: sales <mode> review package"
                       │
                       ▼
        external execution (humans: send, call, negotiate, sign)
```

## Phase 1 — Foundation

Two documents, created on the first `/sales` run and read on every run:

- `docs/enterprise/foundation.md` — company foundation: product, stage (team/revenue/
  funding), business model and pricing, target-customer hypothesis, geography, constraints.
  Shared by all enterprise teams.
- `docs/enterprise/sales/foundation.md` — sales foundation: GTM motion and ACV, deal
  evidence and where records live, current pipeline state, outbound infrastructure status,
  existing assets, quarterly targets.

Both carry a dated header and a `Last reviewed: <date>` line. **Refresh rule: any
foundation doc older than 90 days triggers a refresh offer at the start of the next
engagement.** Sales foundations go stale fast — motion, pricing, and targets change
quarterly at startup stage.

## Phase 2 — Engagements

| Mode | When to run it | What it produces | Prerequisite |
|------|----------------|------------------|--------------|
| `--icp` | Before anything else; re-run quarterly or after 10+ new wins/losses | ICP Definition Doc (or labeled Hypothesis): firmographics, triggers, buying committee, disqualify list, tiered account list | Foundation docs; closed-won/lost evidence (or explicit hypothesis mode) |
| `--playbook` | Once ICP exists; ALWAYS before hiring the first rep | Sales playbook: stages + exit criteria, MEDDPICC rubric, discovery guide, demo framework, objection library, battle cards, discount matrix | ICP doc |
| `--outbound` | Once ICP + positioning exist and there's capacity to take meetings | Infrastructure spec, signal-based plays, multi-channel sequences with copy, metrics contract | ICP doc; positioning one-liner (inherit from marketing) |
| `--pipeline` | Weekly once ≥5 live deals; always before a forecast is committed upward | Hygiene audit, MEDDPICC scorecard, evidence-based forecast re-bucketing, coverage math, top-risk actions | Deal data (CRM export or pasted list); stage definitions |
| `--deal` | Any material deal at stage 2+; mandatory before calling a deal "Commit" | MEDDPICC 0–3 score with quoted evidence, gap plan, buyer-facing MAP draft, business case draft | Deal history/notes from the human |

Prerequisites are enforced softly: the skill warns and offers to run the prerequisite
first, but never hard-blocks a founder who knows what they need.

## Phase 3 — Commit artifacts

All artifacts land in `docs/enterprise/sales/`:

```
docs/enterprise/sales/
├── foundation.md
├── INDEX.md                          # one line per artifact: date, mode, link, review gate
├── icp-definition-2026-07-06.md
├── sales-playbook-2026-07-06.md
├── outbound-system-2026-07-08.md
├── pipeline-review-2026-07-13.md
└── deal-review-acme-2026-07-14.md
```

The date in each filename and document header is the audit trail — it proves the work
happened and when. Do not remove or change these dates. Superseded artifacts stay in place;
the INDEX marks the current one. Every artifact opens with the standard header block
(generator, date, engagement mode, DRAFT status, review gate).

## Phase 4 — Human review & approval

Artifacts are committed on a branch and opened as a PR titled
`docs: sales <mode> review package`.

Review-gate legend (stated in every artifact header):

- **AI-final** — internal analysis a human may consume directly (hygiene sweeps,
  scoring tables).
- **Human review recommended** — the default for everything buyer-facing or
  decision-shaping: ICP, playbook, sequences, MAPs, business cases, forecasts.
- **Licensed professional required** — anything containing contract or legal-terms
  language goes to a qualified attorney before use. The sales team drafts work product,
  not legal advice.

**Nothing externally binding happens before the PR is approved** — no sequence is sent, no
MAP is shared with a buyer, no price is quoted from a new pricing artifact, no forecast is
communicated to investors.

## Phase 5 — External execution

Every engagement ends with a human to-do checklist. Standing pattern:

- ICP → human approves; both sales and marketing adopt the same doc.
- Playbook → founder validates talk tracks against a real call; new reps onboard from it.
- Sequences → human buys domains, sets SPF/DKIM/DMARC, warms mailboxes, loads the
  sequencer, sends from a real rep identity, owns the deliverability hard-stop.
- MAP → AE sends it to the buyer and confirms dates on a call.
- Business case → AE presents it to the economic buyer.
- Forecast → founder/CRO commits the number upward; the human owns that number.

What the team monitors afterwards (feeds the next engagement): reply/positive-reply rates
and SQOs per sequence, stage-conversion and staleness trends, forecast vs actual, win/loss
reasons — each review consumes the previous period's actuals.

## Operating cadence

- **Weekly:** `--pipeline` hygiene + forecast review (30–45 min equivalent); stalled deals
  get a `--deal` review scheduled.
- **Per deal:** `--deal` at stage 2+ for material deals; mandatory before any Commit call.
- **Monthly:** outbound metrics review against the kill criteria; sequences below floor are
  reworked or killed, never volume-boosted.
- **Quarterly:** ICP refresh from the latest closed-won/lost data; battle-card
  re-verification (any card >90 days old is stale); win-loss synthesis folded into the
  playbook; pricing/discount pattern review.
- **Before each sales hire:** playbook refresh — extract the current motion first; hire
  against the documented system.

## FAQ

**When do I actually need a human lawyer?**
The moment an artifact touches contract terms, order forms, DPAs, or negotiated redlines.
The team can draft and summarize; an attorney reviews before anything is sent or signed.

**Can I skip the review PR?**
Only for internal-only drafts (a hygiene sweep, an internal scoring table). Never for
anything buyer-facing (sequences, MAPs, business cases, quotes) or authority-facing
(forecasts to the board).

**We have almost no closed-won customers. Is `--icp` pointless?**
No — it runs in hypothesis mode: same structure, explicitly labeled, with written
validation criteria. That's still miles better than "we sell to everyone."

**Can the AI just send the outbound for us?**
No. It drafts sequences, infrastructure specs, and monitoring rules. A human configures
DNS, loads the tool, and sends from a real identity. Deliverability and identity are
human-owned by design.

**Our pipeline is in a spreadsheet, not a CRM. Can we still run `--pipeline`?**
Yes — paste or commit the sheet. The audit needs deal name, stage, amount, close date, and
last-activity date. The audit will likely recommend a CRM once deal count justifies it.

**When do we hire a sales rep?**
The process's opinion: after the founder's motion is documented in a playbook and working —
and then hire two, not one, so you can tell whether a miss is the rep or the system.
