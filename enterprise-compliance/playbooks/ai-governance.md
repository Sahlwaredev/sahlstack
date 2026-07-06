# AI Governance Playbook

Reference templates for `/compliance --ai`. Regulatory facts below are **as of 2026-07**
and this area moved constantly through 2025–26 (the Digital Omnibus shifted core EU AI Act
dates in May 2026). WebSearch-verify every date and threshold before it lands in an
artifact.

## §1 AI system register

One row per AI system — including internal tools and vendor-embedded AI, not just
customer-facing features. Build the inventory from the repo (SDK greps, model configs,
inference endpoints) plus human confirmation for tools outside the codebase.

```
System ID | Name & purpose | Our role (provider / deployer) | Model & vendor
| Data in (personal data? source) | Data out (decisions? content? shown to whom)
| Training use (ours AND vendor defaults — verified from vendor terms, not memory)
| EU AI Act classification + rationale + as-of date | Other regimes (state AI laws, sector)
| NIST AI RMF mapping ref | Transparency disclosures in place
| Human oversight mechanism | Evaluation & monitoring | Incident / rollback procedure
| Owner | Last reviewed
```

Role accuracy is the cascade point: **provider** (you developed/place the system on the
market under your name) carries the heavy obligations; **deployer** (you use someone
else's system) carries lighter ones — use per instructions, ensure human oversight, ensure
input relevance, keep logs. Fine-tuning or substantially modifying a vendor model, or
white-labeling it under your brand, can flip you from deployer to provider — flag any
system where this is arguable for human/counsel review.

Training-use column trap: "we never train on your data" is false if a vendor's default
does. Verify each vendor's current data-use terms ([V] = the actual terms page, dated),
and reconcile with what the privacy policy and DPA promise customers.

## §2 EU AI Act classification workflow

Timeline (as of 2026-07 — verify current status via WebSearch before classifying):

- **Feb 2, 2025** — prohibitions and AI-literacy obligations in force.
- **Aug 2, 2025** — GPAI (general-purpose AI model) obligations in force.
- **Aug 2, 2026** — **Article 50 transparency obligations apply**: disclose chatbot
  interactions, mark AI-generated content, deepfake labeling. This held firm under the
  Digital Omnibus and is the near-term obligation for most SaaS.
- **Dec 2, 2027** — Annex III high-risk obligations, **deferred from 2026 by the May 2026
  Digital Omnibus — track final adoption**; this date has moved once and could move again.
- Penalties scale to 7% of global turnover for prohibited practices.

Classification decision sequence, per system:

```
STEP 1  PROHIBITED? (Art. 5)  Social scoring, exploitative manipulation, untargeted
        facial-image scraping, emotion recognition in workplace/education (with narrow
        exceptions), and the other Art. 5 practices.
        → If arguably yes: STOP. BLOCKING finding, escalate to human + counsel.

STEP 2  HIGH-RISK? (Annex III)  Employment/worker management (screening, evaluation),
        education access/assessment, credit & essential services eligibility, insurance
        pricing (life/health), law enforcement, migration, justice, biometrics, critical
        infrastructure. Also: product safety components under Annex I regimes.
        → If yes: record it, note the Dec 2, 2027 compliance horizon (verify), and start
        the gap plan early — risk management system, data governance, technical
        documentation, logging, human oversight, accuracy/robustness. Check the Art. 6(3)
        filter (narrow procedural/preparatory tasks may be exempt) — document the
        analysis either way.

STEP 3  LIMITED-RISK / TRANSPARENCY? (Art. 50)  Chatbots and conversational AI → users
        must know they're interacting with AI. Generated/synthetic content → machine-
        readable marking. Deepfakes → visible labeling.
        → If yes: draft the disclosure copy and marking spec now; obligation applies
        Aug 2, 2026.

STEP 4  MINIMAL RISK  Everything else (spam filters, code completion, internal search).
        → Register entry + AI acceptable-use policy coverage. No further AI Act
        obligations, but GDPR still applies to any personal data in the loop.
```

Every classification records: verdict, rationale citing the specific facts, role
(provider/deployer), as-of date, and a re-classification trigger ("re-classify if: feature
starts scoring job applicants, EU launch, model fine-tuned in-house").

GPAI note: building on top of a GPAI model does not make you a GPAI provider; training or
substantially modifying one might. Flag for counsel if in-house training approaches this line.

## §3 NIST AI RMF mapping

Use the four functions as the skeleton for the internal AI governance policy. Per function,
the register drives concrete items:

- **GOVERN** — AI acceptable-use policy; roles (who approves new AI systems); risk
  tolerance statement; this register as the accountable inventory; vendor AI assessment
  step in procurement.
- **MAP** — per-system context: purpose, users, impacted people, data flows (link to the
  privacy data map — AI systems processing personal data appear in BOTH), failure impact
  ("what happens when the model is wrong, and who does it happen to?").
- **MEASURE** — evaluation approach per system: accuracy/quality evals, bias testing where
  decisions affect people, red-teaming for user-facing generative features, monitoring
  metrics and thresholds.
- **MANAGE** — response: incident/rollback procedure per system, human oversight mechanism
  (a named human who can intervene, not a decorative checkbox), periodic review cadence,
  decommissioning.

Right-size: a 5-person startup's MEASURE section is "golden-set eval before each prompt
change, user feedback flag" — not an ML-ops platform. Statutory transparency obligations
are never right-sized away.

## §4 US state & other regimes checklist

As of 2026-07 — this list changes fast; WebSearch "US state AI laws in effect" before use:

- **Colorado AI Act (SB 24-205)** — duty of reasonable care re algorithmic discrimination
  for high-risk systems (consequential decisions: employment, credit, housing, insurance,
  education, healthcare); developer AND deployer duties; effective date shifted to
  June 30, 2026 by special session — **verify current status and any further amendment**.
- **CCPA ADMT regs** (operational Jan 1, 2026) — pre-use notices and opt-outs for automated
  decision-making technology affecting Californians; risk assessments filed with the CPPA.
- **Illinois BIPA** if any biometrics; **NYC Local Law 144** if automated employment
  decision tools touch NYC candidates (bias audit required).
- **GDPR Art. 22** — automated decisions with legal/significant effect need a lawful path
  (explicit consent, contract necessity) + human review right; a DPIA is almost always
  required (innovative tech + evaluation criteria).
- Sector overlays: FDA (clinical AI), FTC Act §5 (AI claims substantiation — "AI-powered"
  marketing that overstates capability is a deception theory), EEOC (hiring tools).

## §5 Transparency disclosure drafting kit (Article 50)

- **Chatbot disclosure:** shown before or at first interaction, plainly: "You're chatting
  with an AI assistant." Not buried in ToS. Exemption: obviousness to a reasonable user —
  do not rely on it; disclose anyway.
- **AI-generated content marking:** machine-readable marking for synthetic content
  (metadata/provenance standard where feasible) + human-visible label where the content
  could be mistaken for human-authored or real.
- **Deepfake labeling:** visible disclosure on image/audio/video of real people or events.
- **Model output caveat (product copy):** short, honest, specific — "AI-generated; may
  contain errors; verify before relying" beats a paragraph of hedging.

Each disclosure ships as: exact copy + placement spec + screenshot/verification step for
QA (`/qa` can verify placement post-implementation).
