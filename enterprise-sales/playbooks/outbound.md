# Outbound System — signals, infrastructure, sequences

Outbound in 2026 is a deliverability-constrained, signal-driven craft. Volume blasting is
not a strategy; it is how startups torch their domain reputation permanently. Everything
below assumes the ICP doc exists — outbound aims at ICP section 3 (triggers) and section 8
(tiers), not at a raw firmographic filter.

## 1. Signal taxonomy — every sequence needs an entry reason

Signal-triggered outreach outperforms static lists roughly 5x on reply rate (industry
averages hover around 3–4% for generic cold email vs 15–25% for signal-based personalized
outreach — verify current benchmarks via WebSearch; these date fast).

| Signal class | Examples | Observable via | Strength |
|--------------|----------|----------------|----------|
| Funding | new round, grant | press, Crunchbase-class sources | Medium — budget exists, priorities in flux |
| Hiring | job posts for roles your product serves/replaces | job boards, careers pages | High — active investment in the problem |
| Tech stack | installs/removals of tools you integrate with or replace | BuiltWith-class tools, job-post stacks, docs | High — precise fit signal |
| Leadership change | new exec in the buying-committee role | LinkedIn, announcements | High — new leaders change tools in their first 2 quarters |
| Product intent | pricing-page/docs visits, trial signups from target accounts | your own analytics/de-anonymization tooling | Very high — treat as warm, route fast |
| Competitor engagement | reviews of competitors, competitor community activity | review sites, communities | Medium |
| Regulatory/event | compliance deadline, incident in their space | news, industry sources | High when it maps to your value |

Per play, define: **the signal, where it's observed, the freshness window (a 6-month-old
funding round is not a signal), and the entry criterion combining signal + ICP tier.**
Static Tier-2 list sequences are permitted as a fallback play only, with lower volume and
explicitly lower reply expectations.

## 2. Sending infrastructure spec (non-negotiable rules)

1. **Never send cold outreach from the primary company domain.** Buy 1–3 lookalike sending
   domains (e.g. `get<product>.com`, `try<product>.com`); set them to redirect to the real site.
2. **SPF, DKIM, and DMARC configured on every sending domain — mandatory** before the first
   send. DMARC at enforcement (`p=quarantine` or `p=reject`), not just monitoring.
3. **Warmup:** 2–4 weeks of gradual warmup per new mailbox before real volume.
4. **Volume ceiling: 50–100 emails per mailbox per day.** Scale by adding mailboxes/domains,
   never by exceeding the ceiling.
5. **Health thresholds with a hard stop:** bounce rate <2%, spam-complaint rate <0.1%.
   Breach → pause the sequence the same day, re-verify the list, investigate before resuming.
   Write this rule into the artifact; a human must own the monitoring.
6. **List hygiene:** verify every email before sending (verification tool pass); remove
   catch-alls or send to them at reduced volume; suppress existing customers, open opps,
   and anyone who previously opted out.
7. Plain-text-looking emails, no more than one link, no tracking-pixel-heavy templates —
   engagement-bait formatting is a spam-filter magnet.

## 3. Sequence template (per play/segment)

Header block every sequence artifact must carry:

```
# Sequence: <play name>                        Created: <YYYY-MM-DD>
- Entry signal & criteria: <signal + ICP tier + freshness window>
- Exit criteria: replied (any) / meeting booked / opted out / 6 touches exhausted
- Owner (human): <who sends/monitors>
- Success metrics: reply rate ≥3% floor; positive-reply rate tracked separately;
  judged on SQOs and pipeline $, never on sends or opens.
```

### Touch map (10–14 business days, multi-channel)

| Day | Channel | Purpose |
|-----|---------|---------|
| 1 | Email 1 | Trigger + pain hypothesis + soft CTA |
| 2 | LinkedIn | Connection request, no pitch (or view + light engagement) |
| 3–4 | Email 2 | New angle: insight or proof, NOT "just bumping this" |
| 5 | Call | High-intent accounts only; voicemail references the emails |
| 7–10 | Email 3 | Proof: case study / concrete customer result |
| 10 | LinkedIn | Short DM if connected; value, not pressure |
| 14 | Email 4 | Breakup: give them an easy out, leave the door open |

### Copy rules (every email)

- **Body 75–100 words.** Structure: (1) trigger/relevance — why them, why now, one line;
  (2) insight or pain hypothesis — something they don't already know or a sharp guess at
  their pain; (3) soft, interest-based CTA — "worth a look?" / "open to the idea?",
  never "do you have 30 minutes Tuesday" on a first touch.
- 3 subject-line variants per email: lowercase-casual, direct-benefit, question form.
  Under ~6 words each. No clickbait, no "RE:" fakery.
- Personalization slots marked explicitly for the human: `[FIRST_NAME]`,
  `[TRIGGER_OBSERVATION]`, `[PAIN_HYPOTHESIS]` — the artifact states which slots are
  merge-fillable and which require a human sentence.
- Banned: filler adjectives, feature lists, "I hope this finds you well", fake deadlines,
  guilt bumps ("did you see my last email?"), attachments on cold touches.
- Breakup email is polite and genuinely final for this sequence; re-entry only on a NEW signal.

## 4. Handoff & metrics contract

- **Handoff:** meeting held (not merely booked) + lite qualification (fit confirmed, pain
  stated, right person or path to them) → AE, with structured notes: signal that opened it,
  what they said verbatim about pain, who they are in the buying committee, next step agreed.
- **Measure SQOs (sales-qualified opportunities), not meetings booked.** A meeting that
  no-shows or dies at qualification is a list-quality signal, not a success.
- Weekly review of: deliverability health (bounce/spam/inbox placement), reply and
  positive-reply rate per sequence, meeting-held rate, SQO conversion, pipeline $ sourced.
- Kill criteria per sequence: reply rate <3% after 100+ sends with healthy deliverability →
  the list or the message is wrong; stop and rework, don't push volume.

## 5. Pre-ship checklist for any outbound artifact

- [ ] Every sequence has a named entry signal with a freshness window
- [ ] Infrastructure spec included with the hard-stop thresholds
- [ ] All email bodies 75–100 words, interest-based CTAs, personalization slots marked
- [ ] Suppression rules stated (customers, open opps, opt-outs)
- [ ] Success metrics defined as SQOs + pipeline $, floors and kill criteria stated
- [ ] Human to-do list covers: domain purchase, DNS records, warmup, sequencer load, send identity
