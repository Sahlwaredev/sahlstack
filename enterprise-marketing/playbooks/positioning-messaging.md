# Playbook: Positioning Canvas & Messaging House

Templates for `/marketing --positioning`. Fill every slot or mark it `[PROOF NEEDED]` /
`[UNKNOWN — ask]`. Never delete a slot silently.

---

## 1. Positioning Canvas (April Dunford)

```markdown
# Positioning Canvas — <Product>

## 1. Competitive alternatives
What best-fit customers would ACTUALLY do without us. Include the unglamorous ones.
| Alternative | Type | Why customers pick it | Where it breaks for them |
|---|---|---|---|
| <named competitor> | Product | | |
| Spreadsheet / scripts / manual process | Status quo | | |
| Hire or assign a person | Status quo | | |
| Do nothing / live with the pain | Do nothing | | |

## 2. Unique attributes
Capabilities the alternatives lack. Each must be TRUE and PROVABLE.
| # | Attribute | Verified against top 3 alternatives? (how) | Proof |
|---|---|---|---|
| 1 | | | |

## 3. Value themes (attribute → benefit → business outcome, with proof)
| Attribute(s) | Benefit (what the user can now do) | Business outcome (what the buyer's boss cares about) | Proof point |
|---|---|---|---|
| | | | metric / customer quote / demo moment |

Run the "so what?" chain on every row until it terminates in a business outcome.
A row ending at a feature or a benefit is incomplete.

## 4. Best-fit customer characteristics
- Firmographics: <size, industry, stack, team shape>
- Situational triggers (events that open a buying window): <e.g. new funding, failed audit,
  key hire, tool sunset>
- Who cares MOST about the value themes above (role + why):
- We do NOT target: <explicit disqualifiers>

## 5. Market category (frame of reference)
- Chosen category: <existing category | subsegment of X | new category>
- Rationale: why this frame makes the value obvious fastest
- Frames rejected and why: <at least one>
- (New category is highest-risk and usually wrong for startups — if chosen, state the
  overwhelming evidence.)

## 6. Relevant trends (optional — only if genuinely connected)
- <trend> → <how it makes our value more urgent>. If the link is decorative, delete the row.

## 7. Positioning statement + boilerplate
One paragraph: For <best-fit customer> who <situational trigger/pain>, <product> is a
<market category> that <primary value theme>. Unlike <top alternative>, <provable difference>.
Boilerplate (website/press "about" paragraph): <3–4 sentences, buyer language>

## 8. Sign-off record & review triggers
- Agreed by: <founder> / <product> / <sales> on <date>   ← blank until humans sign
- Disagreements resolved: <what each party thought the competition was, and the resolution>
- Re-run this canvas when: major competitor move · pricing/packaging change ·
  2 quarters elapsed · 10 win-loss calls contradict it
```

### Facilitation notes (the 10 steps, operationally)

1. **Best customers first.** List them by name. Happiest, fastest-closing, highest-retention.
   Positioning is reverse-engineered from who already loves you, not from who you wish loved you.
2. **Cross-functional team.** Founder + product + sales must be in the sign-off. Disagreement
   about who the competitors are is the root of weak positioning — surface it, don't average it.
3. **Alternatives, not competitors.** "What would they do without you" — usually a spreadsheet,
   an intern, or nothing. If every alternative listed is a venture-backed lookalike, push back.
4. **Attributes must be provable.** "Easier to use" is not an attribute; "deploys without a
   schema migration" is.
5. **Value needs proof.** Metric, quote, or demo moment per theme. No proof → `[PROOF NEEDED]`.
6. **Best-fit = who cares most**, not who could theoretically buy.
7. **Category is a frame, not a wish.** Pick the frame in which the value is obvious in one
   sentence.
8. **Trends only if load-bearing.**
9. **Canvas is the artifact.** 10. **Ship it** — the activation list in the skill (homepage
   hero, pricing framing, sales one-liner) is mandatory output, not a suggestion.

---

## 2. Messaging House

```markdown
# Messaging House — <Product>
Derived from the positioning canvas dated <date>. Do not edit this without re-checking the canvas.

## Roof — brand promise
<One line. Outcome-first, no jargon. Test: would a buyer say this sentence to a colleague?>

## Pillars (3 value themes)
### Pillar 1: <headline in buyer language>
- Supporting copy: <2–3 sentences>
- Proof points: <metric> · <customer quote (verbatim, sourced)> · <demo moment>
### Pillar 2: ...
### Pillar 3: ...

## Foundation
- ICP: <one paragraph, from canvas §4>
- Voice & tone: <3–5 rules, e.g. "plain verbs, no hype, numbers over adjectives">
- Words we use: <buyer-corpus terms>
- Words we ban: seamless, powerful, revolutionary, cutting-edge, best-in-class,
  next-generation, game-changing, <domain-specific additions>
- Elevator pitches:
  - 10s: <one sentence>
  - 30s: <2–3 sentences>
  - 2min: <short paragraph incl. alternative displaced + proof>

## Extensions
### Per-persona message map
| Persona | Cares about | Lead message | Proof | Avoid saying |
|---|---|---|---|---|
| Economic buyer | | | | |
| End user | | | | |
| Technical evaluator | | | | |

### Per-funnel-stage variants
| Stage | Buyer question | Message | CTA |
|---|---|---|---|
| Problem-aware | | | |
| Solution-shopping | | | |
| Decision | | | |

### Objection → response table
| Objection (verbatim if possible) | Response | Proof |
|---|---|---|
```

### Messaging quality gates (check before shipping)

- [ ] **Swap test:** paste a competitor's logo on it — if it still reads true, rewrite.
- [ ] **Buyer-language test:** every headline traceable to the buyer-language corpus
      (win-loss quotes, call phrases, review-site language). Founder vocabulary rewritten out.
- [ ] **"So what?" chain:** feature → benefit → business outcome complete on every pillar.
- [ ] **Proof per claim:** no naked claims; `[PROOF NEEDED]` markers resolved or acknowledged.
- [ ] **Zero banned superlatives** anywhere in the house.

---

## Appendix: Quarterly GTM / Marketing Plan structure (used by `--plan`)

1. Objectives & targets (pipeline $, signups, CAC payback ceiling)
2. ICP & segments (primary + ranked secondary)
3. Positioning summary (link to canvas — do not duplicate)
4. Motion (PLG / sales-led / hybrid) + funnel model with stage conversion assumptions,
   each assumption labeled measured / benchmark / guess
5. Channel plan: per channel — rationale, owner, budget, expected CAC, kill criteria
6. Content & campaign calendar (themes by month; link to editorial calendar)
7. Launch calendar with tiers
8. Sales enablement commitments (what marketing delivers to `/sales`, by when)
9. Metrics & review cadence: 30/60/90 checkpoints + decision rules (which metric triggers a
   channel pivot, message change, or ICP revision)
10. Risks & dependencies
