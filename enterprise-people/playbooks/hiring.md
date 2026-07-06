# Hiring Playbook — scorecard-first structured hiring

Reference for `/people --hire`. The load-bearing fact: structured interviews predict job
performance roughly 2x better than unstructured conversations. Everything here exists to keep
the process structured.

## The order of operations (never violate)

```
Scorecard → JD → Loop design → Rubrics → Sourcing → Interviews → Debrief (scores first) → Decision → References → Offer
```

The scorecard comes first. The JD is derived from it. The loop tests it. The debrief scores
against it. Quality-of-hire at 90 days is measured against it. If the user asks for a JD
without a scorecard, build the scorecard first — it takes 15 minutes and everything downstream
depends on it.

## 1. Role scorecard template

```markdown
# Scorecard: <Role Title> (<Level>)

## Mission (one paragraph)
Why this role exists. The single problem it solves. If you can't write this
paragraph, you are not ready to open the req.

## Outcomes (3–5, measurable, time-bound)
1. By month 3: <specific, verifiable result>
2. By month 6: <...>
3. By month 12: <...>
   (Outcomes are results, not activities. "Ship the billing migration with zero
   revenue-impacting incidents" — not "work on billing.")

## Competencies (5–8)
| # | Competency | Definition (one line, observable) |
|---|-----------|------------------------------------|
| 1 | <e.g. Systems debugging> | <what it looks like in behavior> |
...
Include 2–3 role-specific skills, 1–2 collaboration/communication competencies,
and 1 values-aligned competency defined behaviorally (never "culture fit").

## Deal-breakers
Explicit disqualifiers (e.g. cannot work in required time zones). Must be
job-related. Nothing here may touch a protected characteristic.
```

## 2. JD structure

```markdown
# <Title> — <Company>
<Mission paragraph from the scorecard, lightly edited for candidates.>

## What you'll accomplish (first year)
<The 3–5 outcomes, candidate-facing phrasing.>

## What we're looking for
<The competencies as bullets — behaviors and evidence, not years-of-X.
"You've debugged distributed systems under incident pressure" beats
"5+ years of Kubernetes.">

## Compensation & benefits
Base: $X–$Y <+ variable if any>. Equity: <range or "meaningful early-stage
equity; details in offer">. Benefits: <the real list>.

## How we hire
<Loop stages and total time commitment. Candidates convert better when the
process is legible.>

<EEO statement> + <accommodation notice: how to request interview accommodations>
```

JD rules:
- Salary range REQUIRED when the posting reaches candidates in a pay-transparency state
  (CA, CO, NY, WA, IL and a growing list — WebSearch the current list at run time). A remote
  posting viewable nationwide effectively means: include the range. Recommend including it
  always — it pre-filters misaligned candidates for free.
- Screen the language for coded terms ("rockstar", "ninja", "digital native" — age-coded;
  "aggressive" — gender-coded). Requirements listed must be real requirements: over-specified
  JDs measurably shrink qualified pipelines.
- No degree requirement unless genuinely job-required.

## 3. Interview loop design

| Stage | Duration | Who | Tests |
|-------|----------|-----|-------|
| Recruiter screen | 30 min | Talia-role | Mutual fit, logistics, comp alignment, deal-breakers |
| Hiring manager screen | 45 min | HM | 2 core competencies + outcomes walkthrough |
| Work sample | 60–90 min | 1–2 evaluators | THE core skill, directly |
| Loop interview A | 45 min | Panelist | 2 assigned competencies |
| Loop interview B | 45 min | Panelist | 2 different competencies (zero overlap with A) |
| Values/collaboration | 45 min | Cross-functional panelist | Behavioral values competency |

Rules:
- Every competency on the scorecard is owned by exactly one stage. No competency tested twice
  by accident; no competency untested. Publish the coverage matrix to the panel.
- Panel of 4–6 interviewers max. More adds cost, not signal.
- Work sample: time-capped (≤2 hours), representative of real work, never free labor on real
  company problems. If it exceeds ~2 hours, pay for it. Provide the same exercise and the same
  evaluation rubric to every candidate for the role.
- Same question bank per role, every candidate. Deviation destroys comparability and is the
  consistency gap a plaintiff's attorney looks for.

## 4. Rubric anchors (per competency)

For each competency, write 2–3 behavioral questions plus a probing chain, and a 1–4 anchored
scale:

```markdown
## Competency: <name>
Questions:
1. "Tell me about a time <situation targeting the competency>."
   Probes: What was the situation? What did YOU do (not the team)? What
   happened? What would you do differently?
2. <second question>

| Score | Anchor (concrete, observable) |
|-------|-------------------------------|
| 1 | <what a clear miss looks like — specific behavior, not "weak"> |
| 2 | <partial — can describe but not demonstrate; needed heavy prompting> |
| 3 | <solid — specific first-person examples with results; hire bar> |
| 4 | <exceptional — taught us something; multiple strong examples unprompted> |

Red flags: <e.g. takes team credit as "I"; blames without ownership;
cannot produce a single specific example>
```

Note template per interview: verbatim quotes and observed behaviors only. Write what was said,
not conclusions. "Said X, couldn't answer Y" — not "seemed junior."

## 5. Legality guardrails (include in every interviewer packet)

NEVER ask about, or note anywhere:
- Age, birth year, graduation year (as an age proxy)
- Family: marital status, children, pregnancy or plans, childcare
- Health, disability, medications, past injuries or workers-comp claims
- National origin, citizenship (only: "Are you legally authorized to work in the US?" and
  "Will you now or in the future require sponsorship?")
- Religion, race, ethnicity; arrest record (convictions only where job-related and state law
  allows — many states are ban-the-box)
- **Salary history — prohibited in many states (CA, NY, CO, WA, IL among them).** Ask
  expectations instead: "What compensation range are you targeting?"
- Union membership, protected leave history

If a candidate volunteers protected information: do not write it down, do not follow up on it,
steer back to the question.

Accommodations: any request for an interview accommodation goes to the process owner
immediately; it never appears in evaluation notes.

## 6. Debrief protocol (anti-anchoring)

1. Every interviewer submits scores + written evidence BEFORE seeing anyone else's and BEFORE
   any discussion. No hallway pre-reads. This is the single highest-leverage debrief rule.
2. Debrief reviews evidence low-to-high per competency. Challenge scores without evidence
   ("what did they say that supports the 4?").
3. The hiring manager decides. Not a consensus vote — vetoes and vote-counting select for
   inoffensiveness. Panelists advise; the HM owns the outcome and is accountable to the
   scorecard at the 90-day check.
4. Behavioral reference checks before offer: 2–3 references, same structure — "Tell me about
   <outcome-relevant situation>," plus the calibration question: "On a scale of 1–10, how
   likely would you be to hire them again? What would make it a 10?"

## 7. Offer letter structure (US, at-will)

```markdown
<Company letterhead>
Dear <name>,

We're pleased to offer you the position of <title> (<level>), starting <date>,
reporting to <manager>.

- Base salary: $<per pay period> (<annualized $X>), paid <cadence>, less
  applicable withholdings. You are classified as <exempt/non-exempt>.
- <Bonus/variable: target %, plan terms, "per the then-current plan">
- Equity: we will recommend to the Board a grant of <N> stock options under the
  <Plan name>, vesting over 4 years with a 1-year cliff, subject to Board
  approval and the terms of the Plan and your grant agreement.
- Benefits: <summary; "per plan documents, which control">
- Contingencies: <background check per FCRA / reference completion / proof of
  work authorization (I-9)>.
- Your employment is at-will: either you or the company may end it at any time,
  with or without cause or notice. Nothing in this letter changes that.
- This offer is contingent on signing the Confidential Information and
  Invention Assignment Agreement (enclosed).
- This offer expires <date — typically 5 business days>.
```

Offer rules — hard:
- **Never promissory language.** Banned phrases: "annual salary of" as a guarantee framing
  (state per-pay-period first), "job security", "permanent position", "you will receive a
  raise/promotion", any stated or implied term of employment. This letter is not an employment
  contract; promissory language can make it one.
- **Never promise a strike price.** The exercise price is set by the board at grant per the
  then-current 409A valuation. Say so if asked; never write a number.
- Equity is always "subject to board approval and plan documents."
- Within band, or the exception is documented and approved BEFORE the offer goes out (who
  approved, why, expiry).
- Arbitration agreement: a counsel decision, not a template default — flag it
  `Licensed professional required (employment attorney)` and never bundle it silently.
- Non-exempt hires: state the hourly rate and overtime eligibility, not just an annualized figure.

## 8. Funnel metrics (instrument the loop)

- Pass-through rate per stage and time-in-stage (find the leak before adding top-of-funnel).
- Offer-accept target ≥ 85–90%; below that, comp or process is broken — diagnose before hiring more.
- Source effectiveness: hires per source, not applicants per source.
- Quality-of-hire: 90-day check scored against the ORIGINAL scorecard outcomes. This closes the
  loop and is the only metric that validates the whole system.
