# Customer Success Team Process

Every customer success and support engagement at a company using AgentForce enterprise teams follows this process. The goal is retention you can prove: SLAs the team actually meets, health scores that actually predict churn, and playbooks that actually fire — with a human touching only what genuinely requires a human.

## Overview

```
┌────────────┐   ┌──────────────────────────────────────────────┐   ┌───────────┐
│ FOUNDATION │   │ ENGAGEMENTS (natural order)                  │   │ ARTIFACTS │
│ company +  │──▶│ --support ─▶ --knowledge ─▶ --health ─┐      │──▶│ dated .md │
│ CS team    │   │ --onboarding ──────────────▶ --qbr  ◀─┘      │   │ + INDEX   │
│ docs       │   │ --voc (any time; better after --support)     │   │           │
└────────────┘   └──────────────────────────────────────────────┘   └─────┬─────┘
                                                                          │
                 ┌────────────────────────────┐   ┌──────────────────────▼──────┐
                 │ EXTERNAL EXECUTION         │◀──│ HUMAN REVIEW PR             │
                 │ humans send/deliver/sign;  │   │ docs: customer-success      │
                 │ team monitors metrics      │   │ <mode> review package       │
                 └────────────────────────────┘   └─────────────────────────────┘
```

## Phase 1 — Foundation

Two foundation docs anchor every engagement:

- `docs/enterprise/foundation.md` — company-wide: product, stage (team size, ARR, funding), business model and pricing, target customer, geography and constraints.
- `docs/enterprise/customer-success/foundation.md` — CS baseline: who does CS today, channels and daily contact volume, customer book and segmentation, existing SLA commitments, tooling, known retention numbers (churn/NRR/GRR or "unknown"), top ticket drivers.

Both carry a dated header and a `Last reviewed: <date>` line. **Refresh rule: any foundation doc older than 90 days gets flagged at the start of the next engagement and offered a refresh.** Stage changes (funding round, first enterprise deal, support volume crossing 50 tickets/day) warrant an immediate refresh — they change which artifacts are right-sized.

## Phase 2 — Engagements

| Mode | When to run it | What it produces | Prerequisite |
|------|----------------|------------------|--------------|
| `--support` | Before the first enterprise deal demands SLAs; when response times are unmeasured; when escalation = "Slack the founder" | Support playbook, SLA policy, escalation matrix, macro library (incl. the six hard cases) | Foundation only |
| `--knowledge` | Same questions repeating; hero-based support (bus-factor 1); before hiring more agents | KB architecture, KCS v6 program, content gap analysis, 5–10 seed articles from real product docs | `--support` recommended (ticket taxonomy seeds the gap analysis) |
| `--health` | Churn happening or renewals approaching; any book >~10 paying customers | Health score model spec (back-tested), driver-specific save-play library, churn post-mortem system | Foundation; usage instrumentation helps |
| `--onboarding` | New customers stalling; "onboarded" currently means "kickoff call happened" | Onboarding program with instrumented first-value milestone, stage gates, stall play, handoff record | Foundation only |
| `--qbr` | Top accounts have renewal dates and no outcome narrative | QBR/EBR deck structure (≤30% product rule), touch-model segmentation, renewal pipeline with forecast categories, renewal briefs | `--health` recommended (the risks slide needs a score) |
| `--voc` | Quarterly, or when product asks "what do customers actually want" | Revenue-weighted product feedback report with closed-loop notification list | Foundation; better after `--support` (theme taxonomy) |

Natural order for a company starting from zero: `--support` → `--knowledge` → `--health` → `--onboarding` → `--qbr`, with `--voc` on a quarterly loop. Prerequisites are soft — the skill warns and proceeds.

## Phase 3 — Commit artifacts

All artifacts land in `docs/enterprise/customer-success/`:

```
docs/enterprise/customer-success/
├── foundation.md
├── INDEX.md                       # one line per artifact: date, mode, link, review gate
├── support-playbook-2026-07-06.md
├── sla-policy-2026-07-06.md
├── health-score-model-2026-07-13.md
└── ...
```

Every artifact filename and header carries its generation date. **The date in each filename and document header is the audit trail — it proves the work happened and when. Do not remove or change these dates.** Superseding an artifact means writing a new dated file, not editing the old one; INDEX.md marks the old one superseded.

## Phase 4 — Human review & approval

1. Commit the engagement's artifacts on a branch and open a PR titled `docs: customer-success <mode> review package`.
2. Review gates (each artifact's header declares one):
   - **AI-final** — usable as-is with sampled QA: macro drafts, KB seed articles, internal reports.
   - **Human review recommended** — SLA policy, health score spec, QBR decks, VoC reports, save-play library.
   - **Licensed professional required** — rare in CS; contractual SLA language headed into enterprise contracts gets attorney review; anything touching a security incident's external comms gets counsel.
3. **Nothing externally binding happens before the PR is approved**: no SLA published to customers, no macro sent, no QBR delivered, no renewal proposal issued from an unapproved package.

## Phase 5 — External execution

The PR merge unlocks the human to-do checklist that every engagement prints. Typical items and destinations:

- SLA policy → website/contract appendix (after human sign-off; attorney review for enterprise contracts).
- Macro library → helpdesk saved replies (humans send; all P1/legal/security comms human-reviewed, always).
- KB seed articles → the KB platform; resolve every `[VERIFY: ...]` marker before publishing.
- Health score model → CS platform or the interim spreadsheet; instrument missing signals first.
- First-value event → product analytics (engineering task; blocks the onboarding program's metrics).
- QBR decks → delivered live by a human; renewal briefs → the human negotiates.

Afterwards the team monitors: SLA attainment vs the published policy, link rate and self-service success, health-score back-test hit rate each quarter, TTFV, renewal forecast accuracy (forecast vs actual, including whether the at-risk column named the right accounts).

## Operating cadence

| Rhythm | Activity |
|--------|----------|
| Weekly | Support ops review: queue health, SLA attainment, escalations, QA sample (4–10 tickets/agent/month pace) |
| Weekly | Red-account review: every Red has an active play with a named owner; plays past their 30-day checkpoint escalate |
| Monthly | Knowledge health: link rate, zero-result searches, content gap re-run; VoC theme refresh |
| Monthly | Renewal pipeline review: at-risk column first; no account inside T-90 Red without a play |
| Quarterly | Health score re-calibration (back-test against trailing churn); churn-reasons Pareto; relational NPS wave (fatigue cap: one per user per quarter); `--voc` report to product |
| Annual | SLA targets re-set from the year's measured attainment distribution (ratchet, never aspiration); segmentation and touch-model review against coverage economics; foundation docs full refresh |
| Per event | Churn post-mortem for every controllable loss above the ARR threshold; incident post-mortem to `docs/postmortems/` |

Cadence discipline: every review in this table ends with actions that have owners and dates, and starts by checking last cycle's actions. A metric that stays red across two consecutive reviews with the same explanation is an escalation failure, not a data point.

## FAQ

**When do I actually need a human lawyer?**
When SLA language enters a signed contract (credits, remedies, uptime commitments), and for any external communication during a security incident or data-loss event. Internal SLA targets and the support playbook need no attorney.

**Can I skip the review PR?**
Only for internal-only drafts (play logs, internal reports, post-mortems). Never for anything customer-facing or externally binding: published SLAs, macros, KB articles, QBR decks, renewal proposals.

**We're two founders and a shared inbox. Isn't this all overkill?**
Run `--support` at minimum — internal SLAs before a customer forces contractual ones. The skill right-sizes: you get a one-page tier model and six macros, not an enterprise handbook. The split triggers (>50 tickets/day → support lead; >$2M ARR managed → CSM) tell you when to grow the function.

**Our health score says everyone is Green. Are we done?**
Suspicious. Back-test it: of your last 10 churns, how many were Red 90 days prior? If the answer is "few," the score is decoration. Also check for watermelons — high usage with a departing champion is Green outside, Red inside.

**Why can't the AI just send the support replies itself?**
The long tail, with sampled human QA — fine. But P1s, legal or security mentions, service recovery after serious failures, and anything during an active incident carry relationship and legal weight a human must own. The hybrid pattern: AI drafts everything, humans review top accounts and all sensitive comms.

**How big does a churned account have to be before it gets a post-mortem?**
Set the ARR threshold in the team foundation doc (default: top-quartile account size). Below it, log the loss against the churn taxonomy and move on. Above it, every controllable loss gets the full post-mortem — signal timeline, plays run, 5-whys, systemic fix with an owner. Uncontrollable losses get logged and counted, never process-analyzed.

**The chatbot deflects half our tickets. Is support fixed?**
Only if those users actually succeeded. Measure deflection success — resolved AND no repeat contact within 7 days — not deflection count. A bot that "handles" tickets while users rage-quit and churn silently is deflection theater, and the churn number will find it before you do.

**The renewal forecast looks great — all commit, no red. Ship it?**
No. A forecast with no red is a lie. Populate the at-risk column with named accounts and active plays, or document — with evidence — why zero accounts qualify. Forecast reviews start at the red column.
