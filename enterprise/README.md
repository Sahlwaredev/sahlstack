# AgentForce Enterprise Teams

Nine expert business teams plus a board-style review, built as gstack skills. gstack covers
the engineering department (/review, /qa, /cso, /ship, design skills); this suite covers the
rest of the company: strategy, marketing, sales, legal, compliance, finance, people, customer
success, and business operations.

**This directory family is a fork addition.** It is maintained by Sahlware in the
[Sahlwaredev/gstack](https://github.com/Sahlwaredev/gstack) fork and is intentionally not
part of upstream gstack.

## Layout (fork-separation rules)

| Path | What it is |
|------|------------|
| `enterprise/` | This directory — the `/enterprise` front-door skill (Gabe), persona roster, process pack |
| `enterprise/PROCESS.md` | **The company-level process** — bootstrap order, incremental engagements, change-propagation matrix, board-pass triggers |
| `enterprise/processes/` | Per-team operating processes (the enterprise analogue of a dev process doc) |
| `enterprise-strategy/` … `enterprise-bizops/` | One directory per team skill (`SKILL.md.tmpl` + `playbooks/`) |
| `enterprise-review/` | `/exec-review` — conditional specialist board review (`specialists/` checklists) |
| `enterprise-autoplan/` | `/enterprise-autoplan` — the /autoplan of the business side: full bootstrap or propagation refresh with auto-decisions |

Rules that keep upstream merges trivial:

1. **New top-level directories only.** No enterprise change ever edits an upstream-tracked
   file. Skill discovery, doc generation (`bun run gen:skill-docs`), `gstack/llms.txt`, and
   the `./setup` installer all pick up new skill directories automatically.
2. **Generated files stay generated.** `SKILL.md` files are produced from `SKILL.md.tmpl` by
   `bun run gen:skill-docs --host all` — never edit them by hand (CI enforces freshness).
3. **Only shared tokens.** Templates use `{{PREAMBLE}}` only — no new resolvers, so
   `scripts/resolvers/` stays untouched.
4. **No routing edits upstream.** The root router `SKILL.md.tmpl` is upstream-tracked; the
   enterprise suite relies on explicit invocation, its own `/enterprise` front door, and the
   auto-generated `llms.txt` catalog instead of editing the upstream routing list. (If
   proactive routing lines are ever wanted, isolate them in a single dedicated commit.)

## The shared operating pattern

Every team skill runs the same shape, modeled on gstack's own review/plan skills:

1. **Foundation first** — reads `docs/enterprise/foundation.md` (company) and
   `docs/enterprise/<team>/foundation.md` (team); interviews and creates them if missing.
2. **Mode selection** — each team offers 4–6 engagement modes (flags like
   `/marketing --positioning`).
3. **Expert interrogation** — the intake questions a real expert would ask, minus anything
   the repo already answers.
4. **Persona execution** — named team personas do the work using the industry frameworks
   encoded in each skill's `playbooks/`.
5. **Consultant adversarial review** — an independent consultant persona tries to refute the
   work against domain quality gates before it ships.
6. **Quality gates & verdict** — `READY FOR HUMAN REVIEW` or `NEEDS WORK`, with evidence.
7. **Dated artifacts + human to-do list** — outputs land in
   `docs/enterprise/<team>/<artifact>-<YYYY-MM-DD>.md` with a review-gate classification
   (`AI-final` / `Human review recommended` / `Licensed professional required`) and an
   explicit checklist of the things only a human can do (sign, file, send, approve, connect
   accounts).

`/exec-review` is the capstone: given any business plan or artifact set, it detects which
domains are implicated, dispatches the relevant consultant specialists in parallel (the same
mechanism as `/review`'s specialist army), merges findings with confidence gates, runs a
red-team pass for cross-domain interactions, and returns a board verdict.

## Getting started

```
/enterprise            # meet Gabe, set up the company foundation, activate your first team
/marketing             # or go straight to a team — it will build its foundation on first run
/exec-review <doc>     # board review of any business plan or artifact
/enterprise-autoplan   # the whole bootstrap in one pass: one fact interview, one approval gate
```

The order to run things — and what to re-run when a plan changes — is documented in
[PROCESS.md](PROCESS.md).

After installing skills (`./setup`), commands may be prefixed (`/gstack-enterprise`,
`/gstack-marketing`, …) depending on the `--no-prefix` setting.

## The human boundary

These teams frontload expert work so humans review instead of produce. They never sign,
file, send, negotiate live, publish externally, or claim certifications. Legal, compliance,
finance, and people outputs are drafts for review by the appropriate licensed professional —
each artifact says so on its face.
