# Business Operations Team Process

Every business-operations engagement at a company using AgentForce enterprise teams
follows this process. The goal is a company that runs on defined numbers, written
decisions, right-sized process, and closed loops — not vibes, meetings, and auto-renewed
contracts.

## Overview

```
┌────────────┐   ┌──────────────────────────────────────────────┐   ┌───────────┐
│ FOUNDATION │ → │ ENGAGEMENTS (natural order)                  │ → │ ARTIFACTS │
│ company +  │   │ --metrics → --okr → --vendor / --decide /    │   │ dated, in │
│ bizops     │   │ --program / --postmortem (as events demand)  │   │ docs/     │
└────────────┘   └──────────────────────────────────────────────┘   └─────┬─────┘
                                                                          ↓
                 ┌───────────────────────────┐   ┌────────────────────────────────┐
                 │ HUMAN REVIEW PR           │ → │ EXTERNAL EXECUTION             │
                 │ docs: bizops <mode>       │   │ sign, negotiate, commit,       │
                 │ review package            │   │ schedule the WBR, accept RACIs │
                 └───────────────────────────┘   └────────────────────────────────┘
```

`--metrics` comes first because everything else consumes its definitions: OKRs need
baselines, WBRs need the tree, decision memos need trusted numbers. The rest are
event-driven.

## Phase 1 — Foundation

Two foundation docs, created by the skill on first run and read on every run:

- `docs/enterprise/foundation.md` — company foundation: product, stage (team size,
  ARR, funding), business model, target customer, geography, constraints. Shared by all
  enterprise teams.
- `docs/enterprise/bizops/foundation.md` — bizops foundation: current operating cadence,
  where numbers live and whether definitions exist, the founder's three weekly numbers,
  goals system in use, vendor/spend state, decision hygiene.

Both carry a dated header and a `Last reviewed: <date>` line. **Refresh rule:** if a
foundation doc is more than 90 days old, the skill flags it and offers a refresh before
proceeding. Stage changes (funding round, headcount doubling) warrant an immediate
refresh — right-sizing decisions hang off these answers.

## Phase 2 — Engagements

| Mode | When to run it | What it produces | Prerequisite |
|------|----------------|------------------|--------------|
| `--metrics` | Teams quote conflicting numbers; no exec view exists; before any OKR cycle | KPI dictionary, KPI tree, exec dashboard spec, WBR template | Foundation only |
| `--okr` | Start of quarter (drafting), any time OKRs read like task lists (rewrite), end of quarter (scoring + retro) | OKR document with baselines, owners, C/A labels; check-in cadence; quarter review | `--metrics` recommended (baselines) |
| `--vendor` | A purchase is being considered; a renewal/notice deadline is inside 90 days; nobody knows the SaaS spend | Comparison matrix, RFP (≥$25k/yr), negotiation brief, vendor register, renewal calendar, spend-recovery estimate | Foundation only |
| `--decide` | A named decision is pending and nothing is written down | 1-pager (two-way door) or 6-pager (one-way door), decision-log entry | Trusted numbers help; not required |
| `--program` | A cross-functional initiative is starting (3+ teams or 5+ people) | Project charter, RACI with accepted A's, RAID log, status rhythm | A named accountable owner exists |
| `--postmortem` | A business failure worth learning from: missed quarter, botched launch, failed vendor, blown budget | Blameless post-mortem with process-level action items; WBR-candidate signal | None — run within 2 weeks of the failure |

Right-sizing is enforced inside every mode: no formal RFP under $25k/yr, one-page WBR
under 30 people, no RACI for two-person projects, 1-pager for any reversible decision.

## Phase 3 — Commit artifacts

Artifacts live in `docs/enterprise/bizops/`:

```
docs/enterprise/bizops/
  foundation.md
  INDEX.md                          # one line per artifact: date, mode, link, review gate
  decision-log.md                   # append-only
  kpi-dictionary-2026-07-06.md      # example dated artifacts
  vendor-register-2026-07-06.md
docs/postmortems/                   # business post-mortems join engineering ones here
  2026-07-06-missed-q2-pipeline.md
```

The date in each filename and document header is the audit trail — it proves the work
happened and when. Do not remove or change these dates. Superseded artifacts stay in
place; the INDEX marks the current one.

## Phase 4 — Human review & approval

Artifacts ship via a PR titled `docs: bizops <mode> review package`.

Review-gate legend (in every artifact header):

- **AI-final** — usable as-is: KPI dictionary entries, WBR/dashboard specs, RAID logs,
  post-mortem drafts, vendor register.
- **Human review recommended** — a human must own the outcome before it's acted on:
  OKR targets (teams commit, AI proposes), decision memos (humans decide), negotiation
  briefs and vendor recommendations (humans sign and call).
- **Licensed professional required** — anything with legal effect in vendor contracts
  (liability, indemnity, DPA terms) goes to a qualified attorney before signature.

Rule: nothing externally binding — no signature, no vendor commitment, no cancellation
notice, no published targets — until the PR is approved. Internal-only drafts may
iterate before the PR, but the package that drives action gets reviewed.

## Phase 5 — External execution

The engagement's handoff summary ends with a human to-do checklist. Only humans:

- [ ] Sign contracts and approve spend (named approver, runway impact stated)
- [ ] Make negotiation and reference calls (brief + BATNA provided)
- [ ] Accept residual vendor/security risk (named owner)
- [ ] Commit to OKR targets as a team; hold the "what we will NOT do" meeting
- [ ] Accept RACI accountability, by name
- [ ] Make one-way-door decisions (the 6-pager is ready)
- [ ] Present to the board (materials drafted)

Where artifacts get executed: KPI dictionary → BI tool / spreadsheet formulas; WBR
template → the recurring weekly slot; renewal calendar → reminders keyed to **notice
deadlines**, not renewal dates; decision memos → the decision meeting, then the log.
Afterwards the team monitors: WBR follow-through (last week's actions reviewed first),
renewal calendar 90-day triggers, OKR weekly confidence, post-mortem action-item
completion.

## Operating cadence

| Rhythm | Activity |
|--------|----------|
| Weekly | WBR (one page under 30 people, variance explanations written in advance); 10-min OKR check-in; program status with RAID refresh |
| Monthly | Renewal calendar sweep (anything entering the 90-day window gets a posture and, if "negotiate", a brief); spend anomaly check |
| Quarterly | OKR scoring + retro; planning cycle with the "what we will NOT do" list; SaaS spend review; post-mortem meta-review (are past action items done, and did they work?) |
| Annually | Annual plan; full vendor register re-verification; foundation refresh |

## FAQ

**When do I actually need a human lawyer or accountant?**
Before signing anything: contract liability, indemnity, and data-processing terms are
attorney work. Budget approvals and anything touching revenue recognition or tax belong
to whoever holds finance authority (or your CPA). The skill drafts the commercial
substance; licensed professionals bless the legal and financial edges.

**Can I skip the review PR?**
Only for internal-only drafts (a WBR page, a RAID update, dictionary edits). Never for
anything that triggers external action — a signed contract, a cancellation notice,
published OKR targets, a vendor commitment.

**We're 6 people. Isn't this all overkill?**
Most of it, yes — which is why right-sizing is a prime directive. At 6 people you want:
the KPI dictionary for your 5 numbers, a one-page async WBR, the vendor register (the
auto-renew ambush does not care how small you are), and 1-pagers for real decisions.
Skip RFPs, skip RACI, skip 6-pagers until a one-way door shows up.

**Our OKRs are basically our task list. Is that so bad?**
Yes — you'll "complete" everything and move nothing. Run `--okr` in rewrite mode: tasks
move to the initiatives list, KRs become baseline → target outcomes. If you can finish a
KR with no customer or business change, it was never a KR.

**A vendor contract renews next month. What now?**
Run `--vendor` today. If the notice deadline hasn't passed: negotiation brief with the
timing leverage you still have. If it has: the register gets the real dates, and the
brief targets next cycle — plus an uplift-cap ask at the first opportunity.

**Who attends a post-mortem for a missed quarter?**
The people closest to the process that failed, plus whoever owns the fixes — roles, not
blame targets. The facilitator enforces blamelessness: root causes must land on process,
incentive, or information failures. If it lands on a person, dig again.
