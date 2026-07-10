# `conversion-design-pdp` — Master Landing Page Blueprint
## The build spec the Scale House Landing Page Agent loads on every job

This blueprint fuses the **ConversionWise "Conversion Design" PDP structure** (reverse-engineered from 24 of their live ad teardowns — see `/README.md`) with Scale House's full persuasion stack:
- `01-conversion-psychology-cro.md` — biases, friction, offer/pricing psychology, measurement
- `02-persuasion-copywriting.md` — awareness stages, frameworks, headline formulas, VoC, objections
- `03-page-structure-build-instrumentation.md` — structure, mobile, CWV, forms, attribution, A/B
- `04-buyer-psychology-niche-matrix.md` — traffic source × vertical adaptation

**How to use:** Resolve the 7 pre-build inputs → build the section blueprint top-to-bottom (each section names the psychology that powers it) → adapt per niche → pass the pre-ship gate. Every default is overridable *with a stated reason* and *by the client's own VoC*.

---

## STEP 1 — Resolve the 7 pre-build inputs (never skip)

Before writing a word, answer these. If the brief is silent, use the defaults noted and flag the assumption.

1. **Traffic source** → sets awareness stage, page length, proof load, CTA hardness. (Cold Meta / Google high-intent / retargeting / email — see `04 §1`.) *Default if unknown: assume the colder source and layer the page.*
2. **Vertical** → sets hero emotion, proof type, credentials, offer, top-2 objections. (See the niche matrix, `04 §7`.)
3. **Awareness stage** (derived from #1) → sets what the headline leads with. (Schwartz, `02 §1`.)
4. **Trust tier** (price × consequence × irreversibility) → sets proof density and whether the LP closes or books-a-call. (`04 §4`.)
5. **Hero emotion** (one, from the driver table) → the single emotion the hero triggers. (`04 §3`.)
6. **The offer + conversion action** → what they get and the exact CTA action (purchase vs. lead vs. call). Match action to trust tier.
7. **The #1 and #2 objections** (vertical + VoC) → must be neutralized above the fold or in the first proof section.

> **VoC override:** Before finalizing hero copy, mine the client's Granola call transcripts + reviews (3-star reviews are gold). The customer's exact words for their pain/outcome beat every default headline. If 5+ customers use the same phrase, it goes in the headline.

---

## STEP 2 — The master section blueprint

Build top-to-bottom. Each section lists **what it contains** and **the psychology powering it**. This is the ConversionWise AFTER-page structure, generalized and psych-annotated. Sections scale with awareness (cold = all of them, long; warm = compress 3–6).

### Zone 1 — Above the Fold (the whole game on mobile)
| Element | Contains | Powered by |
|---|---|---|
| **Promo/trust bar** (thin, top) | Free-ship threshold OR rating+count OR license#/years | Social proof, authority, goal-gradient (free-ship threshold) |
| **Outcome hero image** | Lifestyle/result shot (never product-on-white); shows the AFTER | Emotion selection (`04 §3`), endowment (show them living it) |
| **Benefit headline (H1)** | Outcome + emotion (+timeframe +remove-objection); message-matched to ad/keyword | Awareness-stage match (`02 §1`), specificity, framing |
| **Subhead** | The mechanism / how / why-believe (makes the promise credible) | Sophistication L3+ (mechanism re-earns belief) |
| **Star rating + review count** | "4.9 ★ (2,341 reviews)" + "Loved by 20,000+" | Social proof, bandwagon |
| **Hero video** | "Watch how it works" — muted/autoplay/≤6s, never blocks LCP | Demonstration, peak interest |
| **Primary CTA** | Action-verb + first-person + outcome ("Get My Free Quote") | Von Restorff (one accent color), Fitts's, specificity |
| **Risk-reversal microcopy** | "Free · No card · 60 sec" directly under button | Kills #1 objection at the click point (highest-ROI copy) |

**ATF non-negotiable:** headline + a real CTA + one proof element + logo, all visible without scrolling on 375×667. The CTA must never sit below the fold.

### Zone 2 — Trust & Proof (mid-page)
| Section | Contains | Powered by |
|---|---|---|
| **Trust/logo/rating strip** | Review-platform badges, customer count, press/partner logos | Authority, social proof, "as seen in" |
| **Problem / agitation** | 2–4 pains in the customer's own words (VoC) | PAS, loss aversion, unity ("built for people like you") |
| **Benefit icon row** | 3–5 icons naming key benefits | Miller's law (3–5 chunks), scannability |
| **Solution / mechanism blocks** | 3–6 benefit-led blocks: outcome headline → benefit → feature as proof | Feature→benefit→meaning (`02 §6`), mechanism differentiation |
| **Certifications / trust badges** | Clinically proven / FDA / licensed / GMP etc. (vertical-dependent) | Authority (decisive in regulated verticals) |
| **Before/After OR comparison table** | Transformation visual OR "us vs. them" checkmark grid | Anchoring, framing, decoy, contrast |
| **Deep social proof** | 2–3 testimonials: real photo + name + specific number/result | Social proof (specificity > volume), similarity |
| **How it works** | 3–4 numbered steps, ≤8 words each + icon | Reduces perceived effort, goal-gradient, Miller's |

### Zone 3 — Convert (lower page)
| Section | Contains | Powered by |
|---|---|---|
| **Offer / pricing** | Anchored price (strike-through original), 3-tier w/ "Most Popular", or single clear offer | Anchoring, decoy, charm/round pricing to match positioning |
| **Bundle / upsell** | "Complete the routine" / "Buy 2 Get 1" / Best-Value tier | Raises AOV; bundling, framing |
| **Guarantee & endorsements** | Money-back, warranty, expert/practitioner endorsement | Risk reversal (trust multiplier), authority |
| **Objection / FAQ** | 5–8 Q&As, most-blocking first, phrased as the real worry | Objection handling (`02 §8`), addresses doubt at source |
| **Final CTA** | Repeat primary CTA + guarantee + (real) urgency | Peak-end rule, serial-position (strong close) |
| **Sticky CTA bar (mobile)** | Always-visible ATC / lead bar after hero scrolls out | Fitts's, keeps intent one tap away |
| **Footer** | Legal, privacy, contact, compliance disclosures | Trust floor, compliance |

**CTA cadence:** primary CTA in hero → after solution → after social proof → after pricing → final. Same color, same copy page-wide. Sticky bar mandatory on pages >2 viewports.

---

## STEP 3 — Adapt per niche (quick reference)

Pull the full row from `04 §7`. The levers that change by vertical:
- **Local service** → relief emotion; crew/before-after imagery; license# + response-time + service-area; free quote; click-to-call. Objections: legit/insured? show-up/gouge?
- **DTC product** → desire emotion; lifestyle+product; reviews/UGC/demo; free-ship + bundle + money-back; Add-to-Cart. Objections: works vs. cheaper? returns?
- **Supplement/health** → hope emotion; ingredient/science; third-party testing + citations; subscribe-and-save + 60–90d guarantee; Order/quiz. Objections: science-real? safe/auto-ship? *(structure-function claims only)*
- **Apparel** → aspiration emotion; on-model editorial; fit reviews + size guide + free returns; Shop/ATC. Objections: fit/exchange? quality vs. photo?
- **Lead-gen/B2B** → confidence emotion; team/result imagery; case studies + logos + specialization; free audit/consult; Book-a-Call. Objections: credible/get-my-industry? after-I-submit?
- **Coaching/info** → aspiration+hope; the creator's face; student results + method + founder story; value-stack + payment plans + guarantee; Enroll/Apply. Objections: works/legit? work-for-me/time? *(income disclaimers)*
- **High-ticket** → confidence+status; premium credibility imagery; deep case studies + video testimonials; no-price / "investment starts at"; Book-a-Strategy-Call. Objections: proven-enough? right-for-me/ROI?

---

## STEP 4 — The BEFORE audit rubric (pre-build gate + Proof Scorecard)

ConversionWise's "BEFORE" list, hardened into a checklist. Run it against the client's *current* page pre-build (to justify the rebuild) and against *our* draft pre-ship. Any YES is a defect:

1. **Generic product-only imagery** — studio shots, no lifestyle/outcome? → replace with outcome imagery (generate if needed).
2. **No emotional/outcome connection** — copy describes the product, not the result? → apply feature→benefit→meaning.
3. **Weak/hidden social proof** — low, buried, or unattributed reviews; no certs? → front-load specific attributed proof.
4. **Too many dropdowns/options** — selector or choice friction? → reduce (Hick's), default "Most Popular", multi-step.
5. **Hidden/low-contrast CTA** — buried below fold, no urgency/clarity, weak contrast? → ATF, one accent color, benefit copy, risk-reversal microcopy.

**4 pillars every page must satisfy (CW's frame):** Trust → Clarity → Confidence → Conversion.

---

## STEP 5 — Pre-ship QA gate (all must pass)

**Copy gate (per section):** (1) stranger gets the promise in 5s? (2) exactly one message / one number / one CTA? (3) matches the traffic's awareness stage + the ad/keyword that drove the click? (4) words are the *customer's* words?

**Build gate:** ATF CTA reachable without scroll on 375px · single accent color for CTAs only · tap targets ≥48px · body ≥16px · one primary CTA repeated with same copy · nav stripped/reduced.

**Performance gate (CWV):** LCP ≤2.5s · CLS ≤0.1 · INP/TBT <200ms · hero compressed (WebP/AVIF, explicit width/height) · page <2MB · hero eager+`fetchpriority=high`, below-fold lazy · Lighthouse Perf + a11y ≥ target.

**Instrumentation gate:** theme.liquid universal block live · UTMs captured + injected into form hidden fields + stamped on all events · 6 funnel events fire in order (`lp_pageview → lp_cta_click → lp_form_view → lp_form_engage → lp_form_submit_attempted → lead_form_submitted`) · pixels fire on `/thank-you` ONLY · same-domain redirect · verified in incognito with `?utm_source=smoketest` · JotForm reCAPTCHA off + field names match `qN_` schema.

**Program gate:** a live A/B test running + ICE-ranked backlog (≥3 hypotheses) seeded from audit signals · decision date set · never-go-dark enrolled (backlog.md created).

---

## Meta-principle (governs all of the above)
**Subtraction beats addition.** Layer persuasion onto a clean, single-goal, fast, trust-saturated page — never use psychology to paper over a confusing one. **Every signal must be genuine** — fake scarcity, invented reviews, or dishonest urgency win one session and lose the compounding trust. Message-market match (right promise, right words, right awareness) outweighs design polish every time.
