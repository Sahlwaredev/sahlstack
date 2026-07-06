# Onboarding & Engagement Playbook — 30-60-90, compliance checklist, Q12-mapped surveys

Reference for `/people --onboard` and `/people --engage`.

## PART A — ONBOARDING

Program metrics (define before the first hire onboards): time-to-productivity (the role's
first independent ship, defined per role from the hiring scorecard) and 90-day regretted
attrition. Surveys at day 30 and day 90.

### 1. Pre-boarding & day-one compliance checklist

Offer signed → start date:
- [ ] Equipment ordered to arrive before day one; accounts provisioned (email, SSO, repo,
      HRIS) — access active at 9am day one, not "sometime that week"
- [ ] Payroll + HRIS entry: work state confirmed (drives tax withholding, workers comp,
      and policy addendum assignment)
- [ ] If a NEW work state for the company: payroll tax registration, workers comp coverage,
      required posters (electronic delivery for remote), state addendum exists — flag to the
      human to-do list if not
- [ ] Buddy assigned (peer, not manager); first-week calendar drafted
- [ ] Benefits enrollment window communicated

Day one → day three (federal clock, human-executed):
- [ ] **I-9 section 1**: employee completes on or before day one
- [ ] **I-9 section 2**: employer examines original documents within 3 business days of start
      (remote: authorized-representative or the DHS remote procedure if E-Verify-enrolled —
      verify current rules); NEVER specify which documents the employee must present (document
      abuse) — provide the full Lists A/B/C
- [ ] E-Verify case if enrolled (within 3 business days)
- [ ] State new-hire reporting (deadlines vary ~20 days federal floor; some states shorter)
- [ ] I-9 stored separately from the personnel file (retention: 3 years from hire or 1 year
      post-termination, whichever is later)

### 2. The 30-60-90 program

Anchor: the 30-60-90 maps to the ORIGINAL hiring scorecard. Day 90 is scored against the
scorecard outcomes — this closes the hiring loop.

```markdown
# 30-60-90 — <Name>, <Role>
Scorecard: <link to the role scorecard>

## Days 1–30 — Context
- Meet: <named list — manager, team, cross-functional partners, one founder>
- Learn: product end-to-end as a user; codebase/domain map; how decisions get made here
- Ship: ONE small real thing in week 1–2 (a fix, a doc, a process improvement) —
  momentum beats completeness
- Checkpoint (day 30): manager 1:1 — "what's confusing, what's missing, how is
  the role matching the pitch?" + 30-day survey

## Days 31–60 — Contribution
- Own: <a scoped piece of real work with a deliverable — from the scorecard's
  month-3 outcome>
- Feedback checkpoint (day 60): two-way, written — on-track statement against
  the scorecard, explicit. Concerns surfaced HERE, not at day 90.

## Days 61–90 — Full ramp
- Independent ownership of <the role's core area>
- Formal check-in (day 90): scored against scorecard outcomes; rating language
  from the review scale; 90-day survey
- Outcome: confirmed-in-role / concerns documented with a plan (the pre-PIP
  gate applies even here — no surprises)
```

30-day survey (5 items + open text): clarity of expectations, tools/access readiness, manager
support, "the role matches what I was told in hiring" (the mis-sell detector), inclusion.
90-day: repeat + "I can see myself here in two years" + eNPS.

## PART B — ENGAGEMENT SURVEYS

### 3. Survey design (annual full survey)

25–35 items. 5-point Likert (Strongly disagree → Strongly agree). Structure:

**Engagement index (5 items)** — the outcome variable:
1. I am proud to work at <Company>.
2. I would recommend <Company> as a great place to work. (doubles with eNPS)
3. I rarely think about looking for a job elsewhere.
4. I see myself still working here in two years.
5. <Company> motivates me to go beyond what I would in a similar role elsewhere.

**Drivers (Q12-mapped, 3–4 items each)** — the levers. Gallup's Q12 is the reference model;
map each driver block to its Q12 antecedents:
- **Manager quality** (Q12: expectations, materials, cares about me, development) — "I know
  what is expected of me at work" · "My manager gives me actionable feedback" · "My manager
  genuinely cares about my wellbeing"
- **Growth** (Q12: learn and grow, progress talks) — "I have opportunities to learn and grow
  here" · "Someone has talked to me about my progress in the last six months"
- **Recognition** (Q12: recognition in last 7 days, opinions count) — "I receive recognition
  when I do good work" · "My opinions seem to count"
- **Strategy confidence** (Q12: mission/purpose) — "I understand the company strategy" ·
  "I believe we will succeed" · "My work connects to the mission"
- **Wellbeing** — "My workload is sustainable" · "I can disconnect when I need to"
- **Enablement** (Q12: materials and equipment) — "I have the tools and information I need" ·
  "Processes here help rather than hinder me"

**eNPS**: "How likely are you to recommend <Company> as a place to work?" 0–10.
eNPS = %Promoters(9–10) − %Detractors(0–6).

**Open text (2)**: "What is the one thing we should change?" · "What should we make sure NOT
to change?"

### 4. Survey operating rules

- **Anonymity threshold n=5**: never report any cut (team, tenure, demographic) with fewer
  than 5 respondents — roll up instead. State the threshold in the launch comms; anonymity
  doubted once is anonymity lost forever.
- Participation target 70%+. Below that, results describe the vocal, not the company.
- Cadence: annual full survey + quarterly pulses (5–8 items: the engagement index + the 1–2
  weakest drivers from the last full survey).
- Keep item wording IDENTICAL across cycles — trend beats snapshot; a reworded item resets
  its trend line.

### 5. The action loop (ships WITH the survey — the iron law)

**Never survey without visibly acting.** Survey-and-ignore is worse than not surveying: it
converts private frustration into evidenced cynicism, and participation collapses the next
cycle. The action-planning kit is part of the survey deliverable, not a follow-up:

1. **Results out within 2 weeks** of close: company-level readout (scores, trends, the 2–3
   themes, verbatim samples curated for anonymity).
2. **Per-team action plan within 30 days**: each manager picks ONE driver (not five), with
   the team, and commits:
   ```markdown
   Team: <team> · Driver: <driver> · Score: <x.x> (Δ <±> vs last)
   What we heard: <2–3 specifics>
   Action: <one concrete change> · Owner: <name> · By: <date>
   How we'll know: <the item score next pulse / an observable behavior>
   ```
3. **Close the loop publicly**: "you said → we did" at the next all-hands, and again when the
   next survey launches.
4. Track action completion as a MANAGER metric — an unexecuted action plan is a manager
   performance item, visible in their next review.

### 6. Reading results (analysis guide)

- Rank drivers by correlation with the engagement index for YOUR data — fix what moves YOUR
  index, not the generic literature order.
- A high-scoring company with one team 1.5+ points below the mean has a manager problem, not
  a culture problem — handle via coaching (and §2 of the performance playbook if sustained),
  never via the survey readout.
- Falling participation IS a result: it usually means the last cycle's actions weren't felt.
  Say so in the readout.
- Open-text themes: cluster, count, and quote sparingly — one recognizable verbatim can
  deanonymize; paraphrase anything with identifying detail.
