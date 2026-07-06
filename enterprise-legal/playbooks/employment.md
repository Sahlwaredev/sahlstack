# Employment Documents Playbook — offer letter, PIIA, contractor agreement

Reference for `/legal --employment-docs`. Scope: the legal documents only. The hiring
process, compensation bands, leveling, and benefits design belong to the `/people` team —
cross-reference it in every engagement. Terminations and separations in flight are
attorney-gated (see §4).

Everything calibrates to the **state (and country) of work** — confirm it first. Remote work
means the employee's state usually governs, not headquarters'.

## 1. Offer letter

Structure:
1. Position, title, manager, start date, location/remote status.
2. **At-will statement** — employment is at-will; nothing in this letter or elsewhere
   changes that except a writing signed by an officer.
3. Salary — stated per pay period with annualized figure ("$X per year, paid semi-monthly"),
   subject to withholding.
4. Equity — exactly this framing: "subject to approval by the Board of Directors, you will
   be granted an option to purchase <X> shares of the Company's Common Stock under the
   Company's Equity Incentive Plan, with an exercise price equal to fair market value on the
   date of grant, vesting over four years with a one-year cliff. The Plan and your grant
   documents govern." **Option COUNT, never percentage.**
5. Benefits — summary only; plan documents govern.
6. Contingencies — signed PIIA before day one; proof of work authorization (I-9);
   background/reference check if used.
7. No-conflicting-obligations rep — not bound by any agreement preventing this work; will
   not bring or use any third party's confidential information.
8. Acceptance deadline + signature blocks.

**Never-promise list** (each one has created litigation or 409A damage):
- No equity percentages ("1% of the company").
- No job security or term promises ("we see you here for years") — undermines at-will.
- No guaranteed bonuses without a written plan.
- No "your options will be worth..." valuation talk.

## 2. PIIA (Proprietary Information and Inventions Agreement)

Signed **before day one** — post-hoc PIIAs raise consideration questions in some states
(`[JURISDICTION]`: continued employment isn't sufficient consideration everywhere).

Structure:
1. Confidentiality — company and third-party confidential information; survives employment.
2. **IP assignment — present tense:** "Employee **hereby assigns**" all right, title, and
   interest in inventions made in the scope of employment. Never "agrees to assign"
   (Stanford v. Roche trap — see `ip.md`).
3. **State statutory carve-out notice** — where the state limits assignment of inventions
   made on the employee's own time without company resources, the statute requires WRITTEN
   NOTICE of the carve-out in the agreement:
   | State | Statute |
   |---|---|
   | California | Labor Code §2870 (notice per §2872) |
   | Washington | RCW 49.44.140 |
   | Illinois | 765 ILCS 1060/2 |
   | Minnesota | Minn. Stat. §181.78 |
   (Several other states have analogues — WebSearch when the state is none of these.)
   Omitting the notice can jeopardize the whole assignment provision.
4. Prior inventions schedule — employee lists pre-existing IP excluded from assignment;
   "none" is an acceptable and common entry, but the schedule must exist.
5. No use of third-party confidential information (prior-employer contamination shield).
6. Non-solicitation of employees (and customers where enforceable) — duration 12 months
   typical; check state (`[JURISDICTION]`).
7. Non-compete — **omit in California entirely** (void, and demanding one is itself
   unlawful); elsewhere, many states void or compensation-gate non-competes and the FTC/state
   landscape keeps moving — WebSearch the current rule for the work state before including
   one. Default recommendation: skip the non-compete; rely on confidentiality +
   non-solicitation + trade-secret law.
8. **DTSA whistleblower immunity notice** (18 U.S.C. §1833(b)) — verbatim-style notice that
   confidential disclosure of trade secrets to government officials or attorneys for
   reporting suspected legal violations is immune. **Required to preserve exemplary damages
   and attorney's fees in trade-secret actions** — never omit.
9. Return of company property on termination.
10. At-will preservation — this agreement creates no employment term.

## 3. Independent contractor agreement

Structure:
1. SOW (statement of work) — deliverables, timeline, acceptance criteria; payment on
   invoice (Net 15/30), no benefits, contractor bears own taxes (1099).
2. **IP: work-made-for-hire designation PLUS present assignment backup** — "the deliverables
   are works made for hire; to the extent any deliverable is not a work made for hire,
   Contractor hereby assigns all right, title, and interest..." WFH alone fails for most
   software (it rarely fits the nine statutory categories).
3. Moral-rights waiver (matters for design/creative work and non-US contractors).
4. Classification-supporting terms: contractor controls own schedule, methods, and tools;
   free to work for others; no company training/supervision of methods. **Caution:** the
   ABC test (California and others) looks at reality, not the contract. If the "contractor"
   works core-product hours under direction like an employee, the paper won't save you —
   raise the misclassification flag in the memo (back taxes, penalties, benefits exposure).
5. Confidentiality; no authority to bind the company; indemnity for contractor's breach;
   term and termination; independent-contractor status recital.
6. If the contractor is an entity, the agreement binds the entity AND requires each
   individual performing work to sign the IP/confidentiality terms.

**Chain-of-title tie-in:** any past contractor without this paper is a gap in `/legal --ip`'s
matrix — cure with a confirmatory assignment.

## 4. Attorney-gated items (draft checklists only, never the documents)

- Separation agreements and releases — releases for workers 40+ must satisfy ADEA/OWBPA
  (21/45-day consideration periods, 7-day revocation, specific disclosures for group
  terminations). In-flight terminations = engage employment counsel before acting.
- International hires — use an EOR (employer of record) or local counsel; never adapt US
  templates to foreign employment law.
- Multi-state handbook/policy suites — draft structure, gate content per state on counsel.

## 5. Output package format

Per document: complete draft with `[ASSUMPTION]` and `[JURISDICTION]` flags inline, the
review-gate footer, plus a one-page cover memo: state of work, classification analysis
(one paragraph, decisive), which state-specific provisions were included/omitted and why,
and the human to-do list (board approval for the equity grant BEFORE the start date if
possible, signatures, I-9, payroll/state registrations — cross-reference `/people`).
