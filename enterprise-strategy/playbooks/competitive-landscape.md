# Playbook: Competitive Landscape (--landscape)

Maya's reference for competitor research, the map, dossiers, the watch list, and the
deep teardown. Every fact captured under this playbook carries
`(source: <url>, checked <YYYY-MM-DD>)`. Undated intel is worse than none.

## 1. Search patterns (run these, substituting real names)

Append the current year to category-level searches. Run in this order — roster first,
then per-competitor depth.

**Roster discovery (who exists):**
- `<category> tools <year>`
- `<category> alternatives`
- `best <category> for <target segment>`
- `<known competitor> alternatives` (alternatives-of-alternatives finds the long tail)
- `<category> site:g2.com` and `<category> site:producthunt.com`

**Per-competitor depth (one pass per roster competitor):**
- `<competitor> pricing` → then WebFetch their pricing page directly
- `<competitor> vs <us>` and `<competitor> vs <other roster competitor>`
- `<competitor> review site:reddit.com` and `<competitor> site:news.ycombinator.com`
- `<competitor> funding OR raised OR series` (stage signals resourcing and urgency)
- `<competitor> changelog OR release notes OR "what's new"` (velocity signal)
- `<competitor> careers` (hiring focus predicts roadmap: hiring 5 sales reps = moving
  upmarket; hiring ML engineers = feature direction)

**AI-answer visibility (2026-era check):** note which competitors an AI assistant
names when asked the category's top buying question. Being absent from AI answers is a
strategic fact for both sides. Record the prompt used and the date.

## 2. What to capture per competitor (dossier format)

Each research specialist returns exactly this. Missing data is written as
`UNKNOWN — <what was searched>`, never guessed.

```markdown
### <Competitor> — dossier (checked <YYYY-MM-DD>)

- **One-line pitch (their words):** <from their homepage> (source, checked date)
- **Target segment:** <who they actually sell to, per site language and pricing>
- **Pricing:** <model + entry price + top public tier; or "gated — contact-us only,
  which signals sales-led enterprise motion"> (source, checked date)
- **Stage & resourcing:** <funding, headcount estimate, notable investors> (source, date)
- **Motion:** <PLG / sales-led / hybrid — infer from signup flow + pricing page>
- **Recent moves (last 90 days):** <launches, price changes, positioning shifts> (sources)
- **Strengths (honest):** <2-3, from reviews and feature reality>
- **Exploitable weaknesses:** <2-3, ONLY from review mining or verifiable gaps — quote
  the reviewer's words with source>
- **When THEY win:** <deal/user profile where they beat us — honesty is mandatory;
  a landscape that says "we always win" is fiction>
- **When WE win:** <profile + the provable reason>
- **Threat rating:** HIGH / MEDIUM / LOW + one-line justification
- **Watch triggers:** <the 1-3 events that change the threat rating, e.g. "ships SSO",
  "drops entry price below $X", "raises a round">
```

### Review mining method

Reviews are the only public source of real weaknesses. For each competitor:
1. Search G2/Capterra/Reddit/HN for the competitor name + "switched", "left",
   "frustrating", "wish it".
2. Capture verbatim quotes (short), with URL and date.
3. Cluster complaints into themes. A theme quoted by 3+ independent reviewers is
   evidence; a single complaint is an anecdote — label it as such.

## 3. The competitor map

Two artifacts, both required:

**a) The table** — one row per roster competitor plus the mandatory status-quo row:

| Player | Segment | Pricing (entry) | Motion | Threat | Checked |
|--------|---------|-----------------|--------|--------|---------|
| Do nothing / DIY / spreadsheet | everyone | $0 + hidden time cost | — | usually HIGH | — |
| <Competitor A> | ... | ... | ... | ... | date |

The "do nothing" row is never omitted. For most early products the status quo wins more
deals than any named competitor. State what the DIY alternative actually is (a
spreadsheet, a cron job, an intern) and what it costs the buyer in time and errors.

**b) The 2x2 (ASCII)** — axes are the two dimensions buyers in THIS category actually
trade off, chosen from discovery. Never default to generic "price vs quality". Good
axis examples: depth-of-workflow vs breadth-of-integrations; self-serve-speed vs
enterprise-control; single-player vs team-native.

```
                 <axis 2 high>
                      |
        [Comp B]      |      [Us?]
                      |
  <axis 1 low> -------+------- <axis 1 high>
                      |
        [DIY]         |      [Comp A]
                      |
                 <axis 2 low>
```

Place "Us" and defend the placement in one paragraph. If we occupy the same cell as a
better-funded competitor, say so — that is the finding, not a formatting problem.

## 4. Watch list

The landscape decays; the watch list is the maintenance contract.

| Competitor | Watch triggers | Re-check by | Last checked |
|------------|----------------|-------------|--------------|
| <name> | <triggers from dossier> | <date +90d; +30d for HIGH threats> | <date> |

Rules:
- HIGH threats re-check every 30 days; others every 90.
- A fired trigger (competitor ships the feature, changes price, raises) means re-run
  `--landscape` scoped to that competitor and notify the pricing/growth artifacts that
  cite it.
- Long-tail players found in roster discovery but not deep-researched go here with
  trigger "appears in a lost deal or an AI-answer citation".

## 5. Deep teardown (optional depth, top threat only)

Run only when selected in discovery. Sections, in order:

1. **Product motion:** sign up for their trial if public; if not, reconstruct from docs,
   demo videos, changelog. Time-to-value estimate. What their onboarding optimizes for.
2. **Pricing architecture:** full tier table, fence features, value metric, discount
   signals (public "talk to sales for volume" language). What their pricing says about
   who they want.
3. **GTM anatomy:** channels visible (SEO footprint via `site:<domain>` count and top
   pages, paid ads presence, review-site investment, community). Where their demand
   comes from.
4. **Trajectory:** funding + hiring + changelog velocity → most likely next 2 moves,
   stated as predictions with confidence (HIGH/MED/LOW) and the trigger that confirms.
5. **Exploit plan:** 3 concrete moves we can make that they structurally cannot follow
   (because of their pricing model, their segment commitments, or their architecture) —
   each with the evidence for "cannot follow".

## 6. Quality bar (Maya self-checks before Phase 4)

- [ ] Every fact dated and sourced; zero "everyone knows" claims
- [ ] "Do nothing" row present with a real description of the status quo
- [ ] Every dossier has "when THEY win" filled honestly
- [ ] Weaknesses quote reviewers, not our hopes
- [ ] Map axes are category-specific, defended in prose
- [ ] Watch list has re-check dates and triggers for every entry
- [ ] Anything unverifiable is marked UNKNOWN, not filled with plausible fiction
