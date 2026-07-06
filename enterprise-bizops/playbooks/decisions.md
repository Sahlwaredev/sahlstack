# Decisions Playbook — memos, decision log, RACI/DACI

Reference for `/bizops --decide` and `/bizops --program`.

## Door classification (decides the artifact)

- **Two-way door** — reversible within roughly a quarter at modest cost. Most decisions.
  Gets a **1-pager**, a fast decider, and a bias to move. 70% of the information is
  enough.
- **One-way door** — irreversible or very costly to unwind (pricing model change,
  platform migration, key market exit, major vendor lock-in, senior hire structure).
  Gets a **6-pager** and a deliberate process.

The skill recommends the door type with reasoning; the human confirms. Misclassifying a
two-way door as one-way wastes a week; the reverse can cost the company. When genuinely
unsure, ask: "what would it cost, in time and money, to fully undo this in 90 days?"

## The 1-pager (two-way doors)

```markdown
# Decision: <one sentence>
**Deadline:** <date> · **Door type:** two-way · **DACI:** D: <driver> / A: <approver> / C: <consulted> / I: <informed>

## Context
3–5 sentences. What changed, why now, what happens if we do nothing.

## Options
2–4 options. Per option: cost / risk / reversibility / time-to-effect. One option is
always the honest status quo.

## Recommendation
Do X because Y. Decisive — no "consider whether."

## What we'd need to believe
For each non-recommended option: the fact pattern under which it would win instead.
(This is what makes the memo persuasive to skeptics — you did their thinking.)

## Risks & mitigations
Top 2–3, each with the mitigation and its owner.

## The ask
"Approve by <date> or we default to <X>." A memo without a default is a conversation
starter, not a decision instrument.
```

## The 6-pager (one-way doors)

Narrative prose — full sentences and paragraphs, not bullets. Bullets hide broken logic;
prose exposes it. Sections in order:

1. **Situation** — the state of the world, with numbers. No recommendations yet.
2. **Tenets / goals** — the principles this decision must honor (e.g. "we do not trade
   gross margin for growth," "no single vendor may hold our data hostage"). Agreed
   before options are argued.
3. **Options with honest tradeoffs** — each option argued at its strongest, including
   the ones the author dislikes. A 6-pager with one obviously-dressed-up winner and two
   strawmen is a sales document and will be called out in review.
4. **Recommendation with data** — the choice, the evidence, the expected outcome with
   baseline → target, and what milestones would confirm or refute it post-decision.
5. **Risks & mitigations** — including the bear case and the reversibility analysis
   (what, if anything, could be staged to keep an exit open).
6. **FAQ** — pre-answer the hardest questions a skeptical reader will ask. Write the
   questions in their voice. An empty or softball FAQ means the thinking isn't done.
7. **Appendices** — data tables, model outputs, vendor matrices, source links.

Meeting protocol: the memo is read silently at the start of the meeting (15–20 min),
then discussed. Nobody presents slides. The decision and dissents are recorded in the
decision log the same day.

## Decision log

Lives at `docs/enterprise/bizops/decision-log.md`. Append-only. One line-block per
significant decision:

```markdown
## <YYYY-MM-DD> — <decision, one sentence>
- **Decider:** <name> · **Door:** one-way / two-way · **Memo:** <link>
- **Chosen:** <option> · **Rejected:** <option — why, one clause each>
- **Revisit trigger:** <the observable fact that would legitimately reopen this> (or "none")
```

The log is what prevents relitigating. "Disagree and commit" only works with a written
record — when the debate resurfaces, the answer is a link, not a meeting. A decision
absent from the log is a decision that will be made again.

## RACI vs DACI — which to use

- **DACI** (Driver, Approver, Contributors, Informed) — one-off decisions. The Driver
  runs the process; the Approver is one person who decides.
- **RACI** (Responsible, Accountable, Consulted, Informed) — ongoing programs and
  deliverables. Rows = decisions/deliverables, columns = roles.

Right-size: no RACI for a two-person project — a sentence saying who owns what beats a
matrix. RACI earns its keep at 3+ teams or 5+ people with genuine handoffs.

## RACI construction rules

1. **Exactly one A per row.** Two A's = zero A's. "The founders" is not an A.
2. **Every row has at least one R.** An accountable owner with no one responsible for
   doing the work is a wish.
3. **Minimize C's.** Every Consulted is a latency tax on every decision in that row.
   Default people to I and promote to C only when their input changes outcomes.
4. **A's are people, not teams.** "Engineering" cannot accept accountability; a named
   person can.

## RACI expert checks (run all four before shipping the matrix)

- [ ] **No row with two A's or zero R's.**
- [ ] **No founder-bottleneck column:** if one person is A on (nearly) every row, the
      matrix is a bottleneck disguised as alignment. Redistribute or say explicitly why
      concentration is correct at this stage.
- [ ] **Acceptance is real:** each A has explicitly accepted accountability — listed as
      a human to-do item with names. An unaccepted RACI is fiction.
- [ ] **Socialized, not just published:** the matrix was walked through with every named
      person, not dropped in a channel. Schedule this in the program comms plan.

## RAID log format (companion to every charter)

| Section | Fields per entry |
|---|---|
| **R**isks | description · likelihood (H/M/L) · impact (H/M/L) · mitigation · owner · review date |
| **A**ssumptions | assumption · how we validate it · by when · owner · status |
| **I**ssues | description · severity · owner · opened date · target resolution date |
| **D**ependencies | what we need · from whom · needed by · status · escalation path |

Rules: every entry has one owner and a date. A RAID log reviewed only at kickoff is
decoration — it is a standing section of the weekly status, and last week's entries get
statuses before new ones are added.
