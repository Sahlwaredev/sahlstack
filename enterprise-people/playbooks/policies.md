# Policies & Handbook Playbook — core + state addenda architecture

Reference for `/people --handbook`. Governing rule: **employment law follows the employee's
work state, not HQ.** One core handbook (federal + company-wide policy) plus a per-state
addendum for every state where anyone works. Never one blended document — blended handbooks
either over-apply the strictest state everywhere (expensive) or under-apply it (illegal).

Every handbook artifact carries the gate `Licensed professional required (employment
attorney)` — attorney review before publication, no exceptions. An unreviewed handbook is a
liability document written by the defendant.

## 1. Core handbook TOC (15 sections)

1. **Welcome & values** — short; the one section allowed a voice.
2. **Employment basics** — at-will statement (see below), employee classifications
   (full/part-time, exempt/non-exempt, temporary), work authorization & immigration
   compliance, personnel records access.
3. **Hiring & referrals** — internal transfers, referral program, relatives/relationships.
4. **Compensation & payroll** — pay periods and paydays, timekeeping for non-exempt
   (meal/rest break logging), overtime authorization, expense reimbursement (see state
   addenda — CA and IL mandate), payroll deductions, direct deposit.
5. **Benefits** — summary only + "plan documents control"; eligibility, enrollment windows.
6. **Time off** — PTO (see §3 below), sick leave (state addenda control accrual), holidays,
   parental leave, PFML coordination, jury duty, voting leave, bereavement.
7. **Remote work** — eligibility, workspace expectations, stipends, security requirements,
   state-change notification duty ("tell People Ops BEFORE you move" — a move creates
   payroll, tax, and policy obligations).
8. **Conduct** — code of conduct, anti-harassment + anti-discrimination with named reporting
   channels (at least two routes, one bypassing the manager), anti-retaliation commitment,
   conflicts of interest, drug/alcohol.
9. **Technology & security** — acceptable use, company property, electronic monitoring notice
   (NY and CT require explicit notice — addenda), social media.
10. **Performance & development** — cycle summary, promotion process pointer, feedback norms.
11. **Leaves of absence** — FMLA (50+ employees within 75 miles), ADA accommodation process
    (the interactive process, who to contact), military/USERRA, state leaves via addenda.
12. **Safety** — workplace safety, injury reporting, workers comp, emergency procedures.
13. **Separation** — resignation notice request, final pay (state addenda control timing),
    return of property, references policy (dates/title confirmation only, name the contact).
14. **State addenda** — pointer: "Your state's addendum supplements and, where more generous,
    overrides this handbook."
15. **Acknowledgment page** — signature: received, read, understood; handbook is not a
    contract; at-will restated; supersedes prior versions; company may amend.

**At-will language appears three times**: cover page, §2, acknowledgment. CA employees:
addendum carries CA-specific at-will phrasing. The acknowledgment line "this handbook is not
an employment contract and creates no contractual rights" is load-bearing — never cut it.

## 2. State addenda — what drives a state addendum

Per state, the specialist checks (WebSearch current requirements — every item below moves by
legislative session; never trust a cached list):

| Driver | Notes |
|--------|-------|
| Paid sick leave | 17+ states mandate accrual (rate, cap, carryover, permitted uses vary) |
| State PFML | 7+ states and growing; payroll deductions + notice posters |
| Anti-harassment training | CA (SB 1343: 5+ employees, 1hr/2hr supervisor), NY (annual), IL |
| Pay transparency | Posting ranges (CA, CO, NY, WA, IL...); some require internal disclosure |
| Meal & rest breaks | CA is the strictest (timing + premium pay for misses); WA, OR, CO have rules |
| Final paycheck timing | CA: same day for involuntary termination; states range same-day → next payroll |
| Expense reimbursement | CA Labor Code 2802, IL: mandatory for necessary business expenses (incl. remote-work costs) |
| Electronic monitoring notice | NY (written notice + acknowledgment), CT |
| Lactation accommodation | Federal PUMP Act baseline + stricter state rules (CA) |
| At-will phrasing | CA-specific language conventions |
| Jury/voting/bereavement leave | State-specific paid/unpaid rules |
| Non-compete limits | CA void; CO/IL/WA income thresholds; FTC landscape shifting — counsel item |
| New-hire notices | Wage theft prevention notices (CA, NY), posting requirements |

Addendum format: same section numbering as the core handbook, only the sections that differ,
each entry citing which core provision it supplements or overrides.

## 3. PTO: unlimited vs. accrued (force the decision with the real tradeoffs)

| | Accrued | Unlimited |
|---|---------|-----------|
| Balance-sheet liability | Yes — accrues every pay period | No |
| CA payout on exit | Yes — accrued vacation is wages, paid out | No balance to pay |
| Failure mode | Hoarding; year-end rush | **Under-use** — people take less without a number |
| Required countermeasures | Caps + carryover rules per state (use-it-or-lose-it illegal in CA; caps are legal) | Minimum-usage norm (e.g. "at least 15 days"), manager tracking, leadership modeling |
| Signal | Conventional, legible | Startup-standard, but hollow without minimums |

Recommendation logic: unlimited WITH enforced minimums and usage tracking for <50-person
remote startups (removes the CA payout and the liability); accrued when the culture won't
sustain minimums or when hourly/non-exempt staff dominate. Sick leave is ALWAYS tracked
separately where state mandates exist — "unlimited PTO" does not satisfy state sick-leave
accrual/recordkeeping rules by default; the addenda handle this per state.

## 4. Classification tests (the two landmines)

### Contractor vs. employee

Three overlapping tests — the strictest applicable wins:
- **IRS common-law**: behavioral control, financial control, relationship of the parties.
- **DOL economic realities** (FLSA): is the worker economically dependent on the business?
- **CA ABC test** (and similar states): a worker is an EMPLOYEE unless ALL three hold —
  (A) free from control and direction in performing the work,
  (B) work is outside the usual course of the hiring entity's business,
  (C) worker is customarily engaged in an independent trade of the same nature.

**Prong B kills most startup arrangements**: a "contractor" writing your core product IS your
usual course of business. The screening heuristic: long-term + core product + company
direction + company tools = misclassified, in any state. This is the single most common
early-startup HR landmine; back taxes, penalties, and benefits liability compound quietly.

Remediation path: convert to employee (or through an EOR), fix payroll going forward, counsel
review for look-back exposure. Gate: `Licensed professional required (employment attorney)`.

### Exempt vs. non-exempt (FLSA + state)

Exempt requires BOTH:
1. **Salary basis + threshold** — federal minimum salary (WebSearch the current figure — it
   has been in litigation and flux) AND the state threshold where the employee works. CA and
   WA thresholds run far above federal (CA ≈ 2x state minimum wage annualized). The higher
   number wins.
2. **Duties test** — executive (manages 2+ FTEs, hiring authority), administrative
   (discretion and independent judgment on significant matters), professional, computer
   employee, or outside sales. Job titles are irrelevant; actual duties control.

Common startup failures: "salaried" support/ops/junior roles below the state threshold or
failing the duties test → unpaid overtime liability; "everyone is exempt because we pay
salaries" is not a test. Non-exempt obligations: overtime, timekeeping, meal/rest breaks per
state. When in doubt, classify non-exempt — over-classification as exempt is the expensive error.

## 5. Policy-practice match check (run before assembly)

For every policy in the draft:
1. Does it reference a procedure, system, or role that actually exists? (A policy citing a
   "hotline" the company doesn't have, or an "HR department" that is one founder, fails.)
2. Does it describe what the company actually does? An unfollowed policy is worse than none —
   it is evidence of a standard the company set and ignored.
3. Is anything copied from a template for a company shape we are not? (Shift-work rules at a
   remote software startup; 500-person procedures at a 12-person company.)
Fix by editing the policy to match reality or flagging the practice to change — never leave
the mismatch.

## 6. HR data handling (fold into §9 and records practice)

- I-9s: separate storage from personnel files; retain 3 years from hire or 1 year
  post-termination, whichever is later.
- Medical information (accommodations, leave certifications): segregated confidential files (ADA).
- Background checks: FCRA sequence — standalone disclosure, authorization, pre-adverse-action
  letter + copy of report + rights summary, waiting period, adverse-action letter;
  fair-chance individualized assessment where required.
- Candidate data: if EU candidates/employees exist, GDPR applies — lawful basis, ~6-month
  candidate retention post-rejection, DSAR readiness, DPAs with HR vendors. CA employees:
  CCPA/CPRA notice at collection.
