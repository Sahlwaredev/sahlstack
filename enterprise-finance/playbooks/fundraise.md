# Playbook: Fundraise Pack — Deck, Data Room, Dilution Math, Term Sheets

## 0. Readiness gate (run first, verdict required)

- **Runway at process start ≥ 6–9 months.** Starting under 6 months is raising from weakness;
  say so plainly and quantify bridge options (cost cuts from the `--runway` levers table,
  bridge SAFE from insiders, revenue-based financing) before proceeding.
- **The milestone narrative exists:** "what did the last dollar buy" (shipped, ARR, proof
  points) and "what will this dollar buy" — and the bought milestone must be **fundable for
  the NEXT round** (e.g. seed buys the metrics a Series A investor screens for: ~$1M+ ARR
  territory, NRR >100%, burn multiple <2 — verify current expectations via WebSearch, these
  date fast).
- Metrics from `--metrics` under canonical definitions. Deck ARR = model ARR = billing system,
  or the raise dies in diligence.

## 1. Instrument decision

- **Post-money SAFE** (YC standard): default pre-seed/seed. Fast, cheap, no board seat.
  **Danger: stacking SAFEs at varying caps creates dilution surprises — always run the
  conversion math below before signing the next one.**
- **Priced round** (NVCA-style docs): once the round is > ~$3–4M or a lead requires a board
  seat. Slower, $30-60K+ legal, but fixes ownership and governance explicitly.
- Recommend one, decisively, from round size + lead expectations. **Model both** dilution
  outcomes so the choice is made on numbers.
- (Economics only — an attorney papers the instrument. This playbook never drafts securities.)

## 2. Deck outline (10–15 slides — draft real content per slide, not placeholders)

1. Problem — felt, specific, expensive
2. Solution — what exists today (demo screenshot beats architecture)
3. Product — how it works, in the user's words
4. Why now — the shift that makes this possible/urgent
5. Market — **TAM bottom-up** (target accounts × achievable ACV), not top-down analyst quotes
6. Business model — pricing, unit economics (CAC payback, gross margin)
7. Traction — ARR walk, NRR, logos; the canonical numbers only
8. Competition — honest 2×2 or table; "no competitors" is an auto-fail
9. GTM — the motion that's working + the math to scale it (magic number if ≥0.75)
10. Team — why these people win this market
11. Financials — 24-month summary from the operating model, base case
12. Ask & use of funds — amount, instrument, milestones bought, months of runway

## 3. Data room index (numbered folders; build as a gap checklist: HAVE / MISSING / STALE)

```
01-Corporate/        cert. of incorporation, bylaws, board consents, qualifications
02-Cap-Table/        fully diluted (SAFEs, notes, options, warrants) + pro forma post-round
03-Financials/       closed statements, operating model, ARR schedule tied to billing
04-Legal/            IP assignments (EVERY founder + contractor — the classic diligence
                     killer), customer contracts, NDAs, prior financing docs
05-GTM/              pipeline snapshot, cohort retention, win/loss, pricing
06-Team/             org chart, offer templates, option grants, key-employee agreements
INDEX.md             master index with one-line description per document
```

**The cap table is the most-scrutinized document in the room.** It must be exported from the
system of record (Carta/Pulley) — a spreadsheet cap table gets a MISSING-grade flag with
"migrate to Carta/Pulley" as a human to-do.

## 4. SAFE-conversion dilution math (the method — run it, show every step)

Post-money SAFE ownership is fixed at signing: **ownership % = investment ÷ post-money
valuation cap** (with a discount, use the better of cap vs. discount price at conversion).

Worked method for a stack, at a proposed priced round:

1. List every SAFE: amount, cap, discount, post- vs. pre-money form. (Pre-money SAFEs
   dilute each other — convert them iteratively or with the algebraic simultaneous method;
   say which you used.)
2. Sum post-money SAFE ownership: Σ (investment_i ÷ cap_i). Example: $500K at $5M cap (10%)
   + $750K at $10M cap (7.5%) + $500K at $12M cap (4.17%) = **21.67% sold before the round —
   founders often think it's ~15%. This is the surprise the math exists to kill.**
3. **Option pool shuffle:** if the term sheet demands a post-round pool of X% created
   PRE-money, the pool expansion comes out of existing holders (mostly founders), not the
   new investor. Model the pool top-up before the new money prices.
4. New round: investor % = investment ÷ post-money valuation.
5. Fully diluted ownership table — founders, employees (pool), SAFEs, new investor —
   **before and after**, at 3 valuation scenarios (low / target / high).
6. Verify against Carta/Pulley export. No export → every number labeled
   `PROVISIONAL — VERIFY AGAINST CAP TABLE`.

Optional extension (`--raise` on request): exit waterfall — liquidation preferences,
participation, option strike netting — at 3–5 exit values.

## 5. Term-sheet comparison framework (pre-fill with the user's scenarios)

| Term | Sheet A | Sheet B | What it costs you |
|------|---------|---------|-------------------|
| Pre/post-money valuation | | | headline vs. real: check post-money |
| Round size / your dilution | | | from §4 math |
| Option pool top-up (pre/post) | | | pre-money pool = founder dilution (the shuffle) |
| Liquidation preference | | | 1x non-participating is standard; participating or >1x is expensive downside insurance for the investor |
| Pro rata rights | | | future round crowding |
| Board composition | | | control; 2-1 founder-majority typical at seed |
| Protective provisions / vetoes | | | flag unusual ones for the attorney |

Decisive comparison: name the better sheet and why, in dollars of founder ownership at the
target exit — not vibes.

## 6. Process & close

- Investor tiers (A/B/C) + tracking table (firm, partner, stage, next step, date).
- Run partner meetings in parallel — competing term sheets are the only real leverage.
- Close: confirmatory diligence checklist (from the data room gaps), legal docs (attorney),
  wire confirmations (human only).
- **Post-close within 30 days:** 409A refresh (material event — independent appraiser; the
  team preps the data package, never issues the valuation), board calendar set, investor
  update cadence started (see `board-pack.md`).

## Human boundary (repeat in the artifact footer)

Attorney papers all securities documents; qualified appraiser issues the 409A; humans send
the deck, take the meetings, negotiate, sign, and wire. This pack is the ammunition, not the
trigger.
