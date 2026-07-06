# People Team Process

Every people/HR engagement at a company using AgentForce enterprise teams follows this
process. The goal is people work that is consistent, documented, and legally defensible —
artifacts a founder can act on and an employment attorney can review efficiently.

## Overview

```
┌────────────┐   ┌──────────────────────────────────────────────┐   ┌────────────┐
│ Foundation │──▶│ Engagements (natural order)                  │──▶│ Artifacts  │
│ company +  │   │ --comp ▶ --hire ▶ --onboard                  │   │ docs/      │
│ people docs│   │ --handbook ▶ --perform        --engage (any) │   │ enterprise/│
└────────────┘   └──────────────────────────────────────────────┘   │ people/    │
                                                                    └─────┬──────┘
                                                                          ▼
                 ┌───────────────────────────┐   ┌────────────────────────────────┐
                 │ External execution        │◀──│ Human review PR                │
                 │ send offers · publish     │   │ docs: people <mode> review pkg │
                 │ handbook (post-attorney) ·│   │ + attorney gates where flagged │
                 │ deliver reviews/PIPs      │   └────────────────────────────────┘
                 └───────────────────────────┘
```

## Phase 1 — Foundation

Two documents, created by `/people` on first run:

- `docs/enterprise/foundation.md` — company foundation: product, stage (team size, revenue,
  funding), business model, geography/jurisdictions, constraints. Shared by all enterprise teams.
- `docs/enterprise/people/foundation.md` — people foundation: headcount + **work-state map**
  (every state/country where anyone works — this is the compliance surface), contractor
  classification snapshot, HR stack (HRIS/payroll/ATS/equity platform), inventory of existing
  artifacts (handbook, bands, templates), 12-month hiring plan, current comp posture, known risks.

Refresh rule: any foundation doc older than 90 days triggers a refresh offer at the start of
the next engagement. The work-state map goes stale fastest — one remote hire in a new state
changes payroll, policy, and posting obligations.

## Phase 2 — Engagements

| Mode | When to run it | What it produces | Prerequisite |
|------|----------------|------------------|--------------|
| `--comp` | Before the next offer goes out; annually for refresh | Leveling framework, salary bands, equity grant matrix, comp philosophy doc, pay-equity/compression check | Foundation |
| `--hire` | A req is opening | Role scorecard, JD (pay-transparency checked), interview loop + per-competency rubrics, debrief protocol, offer letter draft | `--comp` recommended (offers need bands; otherwise the offer is a documented exception) |
| `--onboard` | An offer is signed | Pre-boarding + I-9/state compliance checklist, 30-60-90 program, 30/90-day surveys | `--hire` recommended (the 30-60-90 maps to the scorecard) |
| `--handbook` | 5+ employees, any multi-state hiring, or before `--perform` | Core handbook + per-state addenda drafts, classification appendix, acknowledgment page | Foundation (the state map) |
| `--perform` | Designing the review cycle, or a performance problem exists | Cycle design, review + PIP templates, calibration guide, manager coaching guide, termination checklist | `--handbook` recommended (PIPs reference policy) |
| `--engage` | ~10+ people; then annual full + quarterly pulse | Q12-mapped survey, comms plan, action-planning kit, analysis guide | Foundation |

Prerequisites are soft: the skill warns and offers the prerequisite, then proceeds if declined,
documenting the gap inside the artifact.

## Phase 3 — Commit artifacts

All artifacts live in `docs/enterprise/people/`:

```
docs/enterprise/people/
  foundation.md
  INDEX.md                                  # one line per artifact: date · mode · link · review gate
  role-scorecard-senior-backend-2026-07-06.md
  salary-bands-2026-07-06.md
  handbook-core-2026-07-06.md
  handbook-addendum-ca-2026-07-06.md
  pip-draft-<initials>-2026-07-06.md        # initials, never full names in filenames
  ...
```

The date in each filename and document header is the audit trail — it proves the work happened
and when. Do not remove or change these dates. In employment matters specifically,
contemporaneous dating is evidence: a documentation file assembled after a dispute begins is
worth far less than one built as events happened.

Sensitive-artifact rule: PIPs, termination checklists, and pay-equity findings reference
people by initials or role in filenames, and the repo must be private. If the repo is shared
beyond leadership, keep these artifacts in a restricted location and commit only a pointer.

## Phase 4 — Human review & approval

Every engagement ends with a PR titled `docs: people <mode> review package`.

Review-gate legend (every artifact header carries one):
- **AI-final** — usable as-is: scorecards, rubrics, loop designs, 30-60-90 plans, survey designs.
- **Human review recommended** — founder/manager judgment before use: JDs, bands, comp
  philosophy, review templates, coaching guides.
- **Licensed professional required (employment attorney)** — handbook + every state addendum,
  offer letter templates (first use), PIPs, anything touching termination, severance, RIF,
  arbitration, or classification.

Nothing externally binding — sending an offer, publishing the handbook, delivering a PIP,
executing a termination — happens until the PR is approved AND the attorney gate (where
flagged) is cleared.

## Phase 5 — External execution

The engagement's handoff summary ends with the human to-do checklist. Typical items and where
they execute:

- Offers → e-signature tool, sent by the founder after board approval of the option grant
- Handbook + addenda → attorney review → HRIS/handbook tool with tracked acknowledgments
- Payroll/tax registration in a new state → payroll provider or registered-agent service
- I-9 section 2 → human with original documents, within 3 business days of start
- PIP/termination conversations → held by a human, always; the skill provides the script
- Surveys → survey tool; results return to `/people --engage` for analysis and action plans

Afterwards the team monitors: offer-accept rate, 90-day quality-of-hire vs. scorecard,
compression against bands, handbook acknowledgment completion, PIP check-in cadence, survey
participation and action-plan completion.

## Operating cadence

- **Per hire**: scorecard → loop → debrief → offer → onboarding checklist (event-driven).
- **Monthly**: hiring funnel review; onboarding checkpoints (30/60/90) due this month;
  exception log review (any out-of-band offers).
- **Quarterly**: engagement pulse; attrition review (regretted vs. non-regretted, split
  always); compliance calendar check (new state obligations, training deadlines).
- **Semi-annual**: performance cycle (review → calibration → comp linkage).
- **Annual**: benchmark refresh + band update; pay-equity analysis; handbook + addenda review
  (legislative sessions change the addenda); full engagement survey.

## FAQ

**When do I actually need a human employment attorney?**
Always for: severance/release agreements, terminations with any risk indicator (protected
class + recent complaint/leave/accommodation, age 40+, litigation threats), RIF lists,
arbitration agreements, contractor reclassification, and final handbook sign-off before
publication. The skill drafts everything and flags the gate; the attorney's review is fast
because the package is complete. Budget guide: a startup-savvy employment attorney reviewing
a well-prepared package costs hours, not weeks.

**Can I skip the review PR?**
Only for internal-only drafts (a scorecard you're iterating on, a survey design). Never for
anything an employee, candidate, or authority will see — offers, handbook, PIPs, terminations.

**Can I send an offer before the comp work is done?**
You can, but the offer becomes a documented exception: the skill records the numbers and the
rationale so future bands can reconcile it. Two undocumented ad-hoc offers is how compression starts.

**HQ is in Texas — why does the skill keep asking about California?**
Employment law follows the employee's work state, not HQ. One remote employee in CA brings CA
wage, leave, expense-reimbursement, and final-pay rules for that employee.

**Can the AI run the termination or the harassment investigation?**
No. It preps the documentation review, checklist, script, and investigation plan. A human has
the conversation; a human investigator conducts investigations; counsel reviews anything with
legal exposure.

**We're 4 people. Do we need any of this?**
You need three things at 4 people: clean classification (contractor vs. employee), a
consistent offer letter, and I-9s done right. Run `--hire` when you hire and skip the rest
until ~8–10 people. The skill right-sizes; it will not hand you a 6-level job architecture.
