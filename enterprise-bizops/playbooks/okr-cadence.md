# OKR & Cadence Playbook — OKR quality rules, planning rhythm, business post-mortems

Reference for `/bizops --okr`, `/bizops --postmortem`, and cadence design in `--metrics`.

## OKR structure

Per team, per quarter:
- **1–3 Objectives** — qualitative, memorable, each with a rationale line linking it to
  company strategy. If the team can't recite its objectives from memory, there are too
  many.
- **2–4 Key Results per Objective** — quantitative outcomes.
- **Initiatives tracked SEPARATELY, below the KRs** — each initiative names the KR it
  hypothesizes it will move. Initiatives are bets; KRs are results.

## The outcome test (run on every KR, no exceptions)

A KR that is secretly a task fails. The test: **could you complete this KR and have
nothing change for customers or the business?** If yes, it's a task.

| Fails (task in disguise) | Rewritten (outcome) |
|---|---|
| "Launch onboarding redesign" | "Activation rate 34% → 55%" |
| "Ship feature X" | "X adopted by 40% of weekly actives within 30 days of launch" |
| "Hire 2 engineers" | (Not a KR at all — it's an initiative under a delivery/velocity objective) |
| "Publish 12 blog posts" | "Organic signups 80/mo → 200/mo" |
| "Migrate to new billing system" | "Involuntary churn 2.1% → <1%; billing support tickets −60%" |

The failed phrasing doesn't die — it moves to the initiatives list under the KR it serves.

## OKR quality rules (the skill enforces these mechanically)

1. **Baselines mandatory.** Every KR is `<metric> <baseline> → <target>`, with data
   source and owner. A KR with no baseline is not ready — pull the number or mark
   "estimate — verify by <date>" and treat verifying as week-1 work.
2. **Committed vs aspirational labeled** on every KR. Committed = expected 1.0;
   aspirational = 0.7 is success. Unlabeled KRs get scored under two different theories
   and the retro becomes an argument.
3. **Never tie OKR scores to compensation.** The moment scores affect pay, everyone
   sandbags and the system measures negotiation skill, not progress. Say this out loud
   in the artifact.
4. **Not cascaded marching orders.** Company OKRs are top-down *context*; team OKRs are
   drafted bottom-up, then aligned in review. Teams own targets they set.
5. **Scoring-history health band: 0.6–0.8 average.** All-1.0 = sandbagging. All-0.3 =
   fantasy planning. Either pattern is a finding about the process, not the teams.
6. **First cycle: pilot one team, one quarter,** before going company-wide. OKR rollouts
   die of company-wide ceremony before habit forms.

## OKR document format

```markdown
# <Team> OKRs — Q<n> <year>
Mission line: <one sentence>

## O1: <objective>
Rationale: <one line linking to company strategy>
| KR | Baseline → Target | Source | Owner | C/A | Confidence |
|----|-------------------|--------|-------|-----|------------|
| KR1.1 <outcome> | 34% → 55% | <system> | <name> | Committed | 0.7 |

### Initiatives (bets against these KRs)
- <initiative> → hypothesizes KR1.1
```

Plus a weekly check-in log (date, per-KR confidence 0–1, blockers, one action) and an
end-of-quarter block per KR: score 0.0–1.0, the learning line ("what we now know that we
didn't"), and carry / kill / done.

## Quarterly cadence

- **Weekly:** 10-minute OKR check-in — confidence + blockers only. No status theater.
  Rides inside the WBR where one exists.
- **Mid-quarter:** grooming allowed. Killing a KR that events invalidated is discipline,
  not failure; silently ignoring it is failure.
- **End of quarter:** score, learn, carry/kill — then the retro feeds the next cycle.

## Planning cadence (annual/quarterly)

```
Company strategy & targets          (top-down: context, not orders)
        ↓
Team plans & resource asks          (bottom-up drafts)
        ↓
Tradeoff forum                      (the "what we will NOT do" list is written HERE)
        ↓
Locked plan → quarterly OKRs → weekly WBR heartbeat
        ↓
Reconciliation                      (plan vs actuals, every quarter — no spreadsheet fiction)
```

**The "what we will NOT do" list is the mark of a real plan.** A plan that only adds is
a wish list. The list is explicit, written, and shipped with the plan:

```markdown
## What we will NOT do this <quarter/year>
- <thing> — deliberately deferred because <reason>; revisit trigger: <observable fact>
```

Rules: minimum 3 entries or the tradeoff meeting didn't happen; each entry has a revisit
trigger so "not now" doesn't silently become "never considered"; when someone proposes a
NOT-list item mid-quarter, the answer is a link to this list plus "what changed?"

The tradeoff forum itself is a human meeting — the AI prepares the options, costs, and a
recommended NOT-list; humans make the cuts.

## Blameless business post-mortem template

Engineering-style incident review applied to business failures: missed quarter, botched
launch, bad hire process, failed vendor, blown budget. Blameless means root causes are
**process, incentive, or information failures — never people.** If the root cause reads
"X didn't try hard enough," dig again.

```markdown
# Post-mortem: <failure, stated neutrally> — <YYYY-MM-DD>
> Status: DRAFT — blameless review. Facilitator: <name>. Attendees: <roles>.

## Summary
Expected: <outcome with numbers>. Actual: <outcome with numbers>. Delta: <numbers>.

## Timeline
| Date | What happened | When the data knew | When humans acted |
|------|---------------|--------------------|-------------------|
The gap between "data knew" and "humans acted" is usually the real finding.

## Five whys → systemic cause
Why 1..5, ending at a process/incentive/information failure. Stop-rule: if a "why"
lands on a person, rephrase to the system that allowed it ("why was one person the
only one who could catch this?").

## What went right
Kept short but present — the mechanisms that limited the damage should be reinforced.

## Counterfactual signal
The metric that, had it been on the WBR page, would have surfaced this 30+ days
earlier. That metric is now a WBR candidate — name it and its owner.

## Action items
| # | Action (process-level) | Owner | Date | Verify-it-worked check |
"Be more careful" is banned. Each action changes a gate, a metric, an authority
limit, or an information flow — something inspectable.

## Prior art
Links to related past post-mortems. Repeat failure type = the previous actions
didn't work; say so.
```

Filing: `docs/postmortems/<YYYY-MM-DD>-<slug>.md` (searchable archive), indexed in
`docs/enterprise/bizops/INDEX.md`.

**Quarterly meta-review:** walk the archive — are past action items done, and did they
work (check the verify-it-worked column)? Completed-but-ineffective actions reopen the
post-mortem. An archive nobody re-reads is a diary, not a system.
