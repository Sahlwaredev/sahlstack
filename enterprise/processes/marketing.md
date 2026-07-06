# Marketing Team Process

Every marketing engagement at a company using AgentForce enterprise teams follows this
process. The goal is positioning-first, evidence-backed marketing: agreed positioning before
channels, pre-registered metrics before launches, and artifacts a human can review, approve,
and execute — never AI output published unreviewed.

## Overview

```
                          ┌──────────────────────────────────────────┐
                          │ FOUNDATION                               │
                          │ docs/enterprise/foundation.md            │
                          │ docs/enterprise/marketing/foundation.md  │
                          └───────────────┬──────────────────────────┘
                                          │
              ┌───────────────────────────┼────────────────────────────┐
              │                 ENGAGEMENTS (natural order)             │
              │                                                        │
              │  --positioning ──► --plan ──► --content / --launch     │
              │        ▲                                    │          │
              │        └──────────── --audit ◄──────────────┘          │
              │        (audit feeds evidence back into everything)     │
              └───────────────────────────┬────────────────────────────┘
                                          │
                          ┌───────────────▼──────────────────────────┐
                          │ ARTIFACTS                                │
                          │ docs/enterprise/marketing/<slug>-<date>.md│
                          │ + INDEX.md entry + review-gate header    │
                          └───────────────┬──────────────────────────┘
                                          │
                          ┌───────────────▼──────────────────────────┐
                          │ HUMAN REVIEW PR                          │
                          │ "docs: marketing <mode> review package"  │
                          └───────────────┬──────────────────────────┘
                                          │
                          ┌───────────────▼──────────────────────────┐
                          │ EXTERNAL EXECUTION (humans press send)   │
                          │ site · email · ads · social · press      │
                          └──────────────────────────────────────────┘
```

## Phase 1 — Foundation

Two docs anchor every engagement:

- `docs/enterprise/foundation.md` — company foundation: product, stage (team/revenue/funding),
  business model and pricing, target customer hypothesis, geography, constraints (budget,
  regulated-industry claim rules, existing commitments).
- `docs/enterprise/marketing/foundation.md` — marketing baseline: current channels and their
  output, positioning status (written/contested/none), launch history, website and analytics
  state, content assets, and the marketing↔sales handoff status (lead definition, response
  SLA).

Both carry a dated header and a `Last reviewed: <date>` line. **Refresh rule:** any foundation
doc older than 90 days gets flagged at the start of the next engagement and offered a refresh.
Stage changes (funding round, pivot, pricing change) trigger an immediate refresh.

## Phase 2 — Engagements

| Mode | When to run it | What it produces | Prerequisite |
|---|---|---|---|
| `--positioning` | No agreed positioning; sales/product/founder name different competitors; after a major competitor move, pricing change, or 2 quarters | Dunford positioning canvas, messaging house, activation list (hero rewrite, sales one-liner) | Foundation docs |
| `--plan` | Quarter boundary; "what should marketing do?" | Quarterly GTM plan: targets, channel plan with kill criteria, funnel definitions + sales SLA, calendars, decision rules | Positioning (soft) |
| `--content` | Organic is a chosen motion; blog exists but produces nothing | Content strategy, topic cluster map, GEO requirements, editorial calendar, first 2–3 briefs | Positioning (soft) |
| `--launch` | Anything user-visible is shipping | Tier assignment, launch brief, three-layer checklist, all tier-appropriate assets drafted | Positioning (soft — warns and drafts a mini block if absent) |
| `--audit` | "Where do we stand?"; before a plan; quarterly | SEO/GEO + funnel + messaging audit with evidence-cited findings and impact/effort roadmap | Live site URL |

Prerequisites are soft: the skill warns and proceeds, never hard-blocks. But the natural
order is real — channels before positioning clarity is the canonical startup marketing
failure, and the team will say so.

## Phase 3 — Commit artifacts

All artifacts live under `docs/enterprise/marketing/`:

```
docs/enterprise/marketing/
  foundation.md
  INDEX.md                                  # one line per artifact: date · mode · link · gate
  positioning-canvas-2026-07-06.md
  messaging-house-2026-07-06.md
  gtm-plan-q3-2026-07-06.md
  launch-brief-sso-2026-07-06.md
  seo-geo-audit-2026-07-06.md
  ...
```

The date in each filename and document header is the audit trail — it proves the work
happened and when. Do not remove or change these dates. Superseded artifacts stay in place
(the INDEX marks the current one); history is the point.

## Phase 4 — Human review & approval

Artifacts are committed on a branch and opened as a PR titled
`docs: marketing <mode> review package`.

**Review-gate legend** (every artifact header declares one):

- **AI-final** — usable as-is once merged: editorial calendars, content briefs, audit
  reports, checklists.
- **Human review recommended** — needs founder/owner sign-off before use: positioning canvas
  (founder + product + sales sign-off is the entire point), messaging house, GTM plan,
  Tier 1 launch kits, anything customer-facing.
- **Licensed professional required** — claims in regulated industries (health, finance,
  legal) go to regulatory/claims counsel before publication.

**Rule:** nothing externally binding — publish, send, spend, or announce — until the PR is
approved. Merging the PR is the approval record.

## Phase 5 — External execution

Every engagement ends with a human to-do checklist: the items only a human can do. Typical
mapping of artifacts to execution surfaces:

| Artifact | Executed where | By whom | Team monitors afterwards |
|---|---|---|---|
| Messaging house / hero rewrite | Website CMS | Human with site access | Conversion and message resonance in next audit |
| Launch assets | Blog, email tool, social accounts, in-app | Human presses send/post | 30/60/90 pre-registered metrics, retro |
| Editorial calendar + briefs | Writing + publishing workflow | Named authors (real bylines) | Citation share, organic pipeline, quarterly decay audit |
| Channel plan | Ad platforms, budgets | Human connects accounts, approves spend | CAC/payback vs kill criteria at 30/60/90 |
| Funnel definitions + SLA | Analytics/CRM configuration | Human with admin access | MQL/PQL→pipeline conversion, quarterly definition audit |

The team never holds credentials for ad accounts, CMS, email tools, social accounts, or DNS.
AI drafts to 90%; a human approves, personalizes, and presses "send/spend".

## Operating cadence

- **Weekly** — growth check: funnel dashboard review, experiment results, next bets
  (15–30 min; needs instrumentation from the audit first).
- **Per launch** — brief before, retro at 30 days after, against pre-registered metrics.
- **Quarterly** — GTM plan (`--plan`); content decay audit; MQL/PQL definition audit against
  downstream conversion; win-loss review feeding messaging updates.
- **Every 2 quarters or on trigger** — positioning review (`--positioning` re-run) after a
  major competitor move, pricing change, or when 10 win-loss calls contradict the canvas.
- **90 days** — foundation doc refresh check (automatic at engagement start).

## FAQ

**Q: Can I skip the review PR?**
Only for internal-only drafts (briefs, calendars, working notes). Never for anything
customer-facing or externally published — positioning, website copy, launch assets, emails,
ads all go through the PR.

**Q: When do I actually need a human professional?**
Regulated-industry claims (health, finance, legal) need claims/regulatory counsel before
publication. Trademark questions on naming go to IP counsel (see the `/legal` team). Everything
else needs founder-level review, not licensed review.

**Q: Do I have to do positioning first? I just want ads running.**
The skill will warn and proceed if you insist. But ads on unvalidated positioning is the most
common way startups burn their first marketing budget — a positioning sprint is hours of work
with `/marketing`, not weeks. Do it first.

**Q: Who owns the numbers in the GTM plan?**
A human. The plan proposes targets with reasoning; accountability for hitting them is
assigned to a named person at PR review. The AI team never owns a metric commitment.

**Q: How does this connect to the sales team?**
One source of truth: the ICP doc, funnel stage definitions, MQL/PQL definition, and response
SLA produced here are the same documents `/sales` consumes. If sales changes them, marketing
re-runs the affected artifacts — never maintain two versions.

**Q: The audit says our AI citation share is zero. Is that an emergency?**
It is the 2026 equivalent of not ranking in 2015 — urgent, not panic. The audit's roadmap
orders the fixes: capture-topic content with GEO requirements, third-party surface presence,
and crawler access come first.
