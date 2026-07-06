# Corporate Playbook — formation, hygiene calendar, board consents, data room

Reference for `/legal --corporate`. The theme: **will this survive diligence?** Every check
here is something a financing or acquisition lawyer will actually pull.

## 1. Formation checklist (Delaware C-corp, venture-track default)

In order — each step's output is a document that belongs in the minute book and data room:

1. Certificate of incorporation filed (10M authorized common is typical) — human files.
2. Bylaws adopted.
3. Initial board consent: appoint officers, adopt bylaws, authorize stock issuance, set
   fiscal year, authorize bank account.
4. Founder stock purchase agreements — with vesting (4-year/1-year cliff standard) and
   **assignment of all pre-formation IP** (chain-of-title anchor; see `ip.md`).
5. **83(b) elections filed within 30 days of the stock purchase** — hard IRS deadline,
   NO cure. Require proof: certified mail receipt + copy retained. Calendar it the day
   stock is signed.
6. EIN obtained; bank account opened in the exact legal name.
7. Foreign qualification in every state where the company has employees or offices.
8. Equity incentive plan adopted (board + stockholder consent) and **409A valuation obtained
   BEFORE any option grants**.
9. IP assignment paper for every hire from day one (PIIA — see `employment.md`).
10. BOI/CTA (Corporate Transparency Act) status: FinCEN's 2025 interim rule exempted
    domestic companies — **WebSearch current status; this has changed repeatedly.**

If the entity is an LLC or nothing yet and the company is venture-track, the finding is:
convert/form a DE C-corp (investors will force it; conversions get pricier with traction).

## 2. Hygiene calendar (recurring)

| When | Item | Failure cost |
|---|---|---|
| March 1, annually | Delaware franchise tax + annual report (use assumed-par-value method — the default calculation produces scary numbers) | Penalties, loss of good standing |
| Annually | Registered agent fee; confirm agent address current | Missed service of process = default judgments |
| Every grant | Board consent BEFORE the grant; strike price = current 409A FMV | §409A penalty tax on the employee; repricing mess |
| Every 12 months or material event | Refresh 409A valuation (funding round, major revenue change) | Stale FMV invalidates grants |
| Within 30 days of any restricted stock purchase | 83(b) filed with proof | Uncurable tax disaster |
| Quarterly | Stock ledger reconciles to cap table tool; no verbal/Slack equity promises outstanding | Diligence findings, disputes |
| Ongoing | Every contract signed in the exact legal entity name by an authorized officer | Personal liability; unenforceable contracts |
| On entering a new state | Foreign qualification + payroll registration | Penalties, inability to sue in-state |

## 3. Board consent formats

Every equity grant, officer appointment, 409A adoption, equity-plan amendment, and
out-of-ordinary-course contract gets a consent. Unanimous written consent (in lieu of a
meeting) is the startup workhorse:

```markdown
# ACTION BY UNANIMOUS WRITTEN CONSENT OF THE BOARD OF DIRECTORS OF <EXACT LEGAL NAME>

The undersigned, constituting all of the members of the Board of Directors of
<Exact Legal Name>, a Delaware corporation (the "Company"), acting pursuant to
Section 141(f) of the Delaware General Corporation Law and the Company's Bylaws,
hereby adopt the following resolutions by written consent as of <date>:

## Recitals
WHEREAS, <context — why the board is acting>;

## Resolutions
RESOLVED, that <specific action — see library below>;
RESOLVED FURTHER, that the officers of the Company are, and each of them is, authorized
to take all actions and execute all documents necessary or advisable to carry out the
foregoing resolutions (omnibus authority).

## Signature blocks
<one per director; date each>
```

**Resolution library** (draft the specific one needed):
- **Option grant:** "approve the grant of options to purchase <X> shares of Common Stock to
  <name> at an exercise price of $<Z> per share, being not less than the fair market value
  per share as determined under the Company's most recent Section 409A valuation dated
  <date>, under the <year> Equity Incentive Plan, vesting <schedule>."
- **Officer appointment:** name, office, authority.
- **409A adoption:** approve and adopt the independent valuation dated <date> setting FMV
  at $<Z>.
- **Material contract:** approve entry into <contract> with <party>, authorize <officer> to
  execute.
- **Ratification** (curing an unapproved past grant): recite the facts honestly and ratify
  as of TODAY's date. **Never backdate a consent.** Ratification cures authorization, not a
  stale 409A price — flag pricing problems to human counsel.

## 4. Diligence data room index

Maintain this tree perpetually — assembling it during a financing is too late. Audit output
marks each item `HAVE / MISSING / STALE`.

```
1. Corporate
   1.1 Certificate of incorporation + all amendments
   1.2 Bylaws (current)
   1.3 All board + stockholder consents/minutes (complete minute book)
   1.4 Good standing certificates; foreign qualifications
   1.5 Officer/director list; indemnification agreements
2. Capitalization
   2.1 Cap table (current, from the tool of record)
   2.2 All stock purchase agreements + 83(b) proof of filing
   2.3 Equity plan + all grant paperwork + 409A reports
   2.4 SAFEs/notes/warrants; any side letters
3. IP
   3.1 PIIAs for every employee; contractor agreements for every contractor
   3.2 Founder/confirmatory IP assignments
   3.3 Trademark filings; domain registrations; OSS inventory (from /legal --ip)
4. Material contracts
   4.1 Customer agreements (top 10 by revenue + any non-standard terms)
   4.2 Vendor contracts; leases
   4.3 Partnership/reseller agreements
5. Financial & tax
   5.1 Financial statements; tax returns; EIN letter
6. Employment
   6.1 Offer letters; handbook; contractor classifications; any separation agreements
7. Legal & compliance
   7.1 Litigation/claims log (even if empty — say so); demand letters
   7.2 Insurance policies
   7.3 Privacy policy history; DPAs; compliance artifacts (from /compliance)
```

## 5. Hygiene audit output format

```markdown
# Corporate Hygiene Audit — <date>
## Findings
| # | Area | Finding | Severity | Cure | Owner |
(Severity: Critical = diligence-killer or uncurable-if-late (83(b), unauthorized issuances);
High = fixable but urgent; Medium = fix this quarter; Low = note.)
## Consents drafted (attached)
## Data room status: <n> HAVE / <n> MISSING / <n> STALE
## Human to-do (sign/file/mail — agents never execute)
```
