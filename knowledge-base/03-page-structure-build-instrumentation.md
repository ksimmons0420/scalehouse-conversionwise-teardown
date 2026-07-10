# PAGE STRUCTURE, BUILD & INSTRUMENTATION
## Reference Layer for Scale House Landing Page Agent

Vertical-agnostic. Every rule below is a default; deviations require a stated reason.

---

## 1. Canonical section order (top → bottom)

Paid traffic has zero patience and no navigation intent. Order is a conversion argument, not a layout.

| # | Section | Must contain | Purpose |
|---|---------|-------------|---------|
| 0 | **Trust bar / eyebrow** (thin, above/fused into hero) | 1 line: rating + count, years in business, license #, or "As seen in" | Instant legitimacy before the pitch |
| 1 | **Hero** | Headline, subhead, hero visual, primary CTA (or inline form), inline proof chip | Answer "what/why-care/what-do-I-do" in <3s |
| 2 | **Trust/logo/rating strip** | Review-platform badges, star rating, customer count, partner logos | Reinforce hero claim with third-party proof |
| 3 | **Problem / agitation** | 2–4 pain points in the customer's own words (VoC-mined) | Prove you understand them; create tension |
| 4 | **Solution / mechanism** | The offer as resolution; 3–6 benefit-led feature blocks (benefit headline, 1-line proof, icon) | Release tension; differentiate |
| 5 | **Social proof (deep)** | 2–3 testimonials with real photo + name + result, or case-study stat block | Transfer trust; handle "does it work" |
| 6 | **How it works** | 3–4 numbered steps, each ≤8 words + icon | Reduce perceived effort/risk |
| 7 | **Offer / pricing / incentive** | The specific offer, price anchor, guarantee, urgency element | Make the value concrete |
| 8 | **Objection handling / FAQ** | 5–8 Q&As targeting price, time, risk, trust, eligibility (FAQ schema) | Remove last blockers |
| 9 | **Final CTA** | Repeat primary CTA + guarantee + urgency; the form again if lead-gen | Capture the now-convinced |
| 10 | **Footer** | Legal, privacy policy, contact, license/compliance disclosures | Trust + compliance floor |

Rules: one conversion goal per page. Kill top-nav on paid LPs (or reduce to logo only) — every nav link is a leak. The form/CTA appears a minimum of 3 times (hero, mid, final) on any page over ~2 viewports.

---

## 2. Above the fold (mobile — the governing viewport)

Assume 375×667 CSS px (iPhone SE baseline). In the first viewport, **without scrolling**, these MUST be visible:
1. **Headline** — benefit + specificity, ≤10 words
2. **Primary CTA** — a real tappable button (or first form field), never below the fold
3. **One proof element** — star rating, customer count, or trust badge
4. **Brand identifier** — logo, so the click-through feels continuous with the ad

**Non-negotiable: the CTA must be reachable without scrolling.** The #1 mobile LP failure is a beautiful hero image that pushes the button to viewport 2. Message-match the ad — the headline should echo the ad's promise/keyword. Scent mismatch = bounce.

---

## 3. Mobile-first layout rules
- **Design mobile first, enhance up.** Default styles 320–430px; media queries add columns at ≥768/1024/1440.
- **Single column on mobile.** Multi-column only at tablet+.
- **Thumb zone:** primary CTAs in the bottom 60% of screen; never strand the only CTA top-right. Sticky bar guarantees thumb-reach on long pages.
- **Tap targets:** min **48×48 CSS px**, **≥8px** spacing. CTA buttons full-width or near, 56–64px tall.
- **Body text ≥16px** (prevents iOS zoom-on-focus; inputs specifically must be ≥16px).
- **Line length** 45–75 chars.
- **No horizontal scroll, ever.** Wide elements scroll in their own `overflow-x:auto` container.
- **Fluid type** with `clamp()`: `clamp(1.75rem, 5vw, 3rem)`.
- Test on a real device, not just DevTools emulation.

---

## 4. Hero composition (five ingredients, ranked by weight)
1. **Headline** — highest-leverage element. Clear > clever. Benefit-driven, specific, message-matched. ≤10 words mobile.
2. **Subhead** — the specificity/proof the headline couldn't carry: mechanism, timeframe, guarantee, number. 1–2 lines.
3. **Hero visual** — priority by vertical: Product/ecom = clean product shot on brand/lifestyle bg; Service/lead-gen = real outcome imagery (finished job, before/after) > stock (generate via Higgsfield/Nano Banana if client photos weak); SaaS = screenshot/looping UI. **Hero video:** muted, autoplay, looped, ≤6s, poster-framed; never block LCP — lazy-init after first paint, ship a static poster as the LCP element.
4. **Primary CTA** — one action, action-verb + outcome copy. One CTA color used nowhere else.
5. **Inline proof chip** — stars + count or trust badge directly under the CTA to de-risk the click.

Default to **inline form in hero for lead-gen** when the offer is simple; use a CTA→modal when the hero needs a content-heavy pitch competing with the form for space.

---

## 5. CTA placement, repetition & sticky bars
- **Cadence:** hero → after solution → after social proof → after pricing → final section. A CTA within one viewport-scroll of wherever the user is.
- **One CTA identity:** same color, same copy (or tight variants), same action page-wide. Secondary CTAs (e.g., "call now") are ghost/outline, subordinate.
- **Sticky bar (mobile, mandatory on pages >2 viewports):** Lead-gen = sticky bottom "Get Free Quote" scrolling to form/modal; E-com = sticky ATC bar (product + price + button) after hero ATC scrolls out. ~56–64px tall, high-contrast, `env(safe-area-inset-bottom)` padding. Hide it when the form/checkout is in view.

---

## 6. Form design & integration
**Field minimization is the highest-ROI form lever.** Lead-gen floor: name, phone OR email, one qualifying field. Defer the rest to the follow-up call.
- Single column, labels **above** fields (not placeholder-only).
- Correct `type`/`inputmode` for mobile keyboards (`email`, `tel`, `numeric`).
- `autocomplete` tokens on everything.
- Inline real-time validation; **never clear the form on error**.
- **Single-step** for ≤4 fields; **multi-step** for 5+ or when a low-commitment first question (ZIP, service type) creates momentum. Show progress, allow back-nav without data loss, persist to `localStorage`, easiest question first.

**JotForm gotchas (hard-won):**
- **Invisible reCAPTCHA silently blocks all submissions** — #1 "form looks fine, zero leads" cause. Verify before coding.
- **Field names must match exact `qN_fieldName` schema** — curl the live form HTML to read real names before wiring hidden fields/prefill.
- **JSform `postMessage` payload is an OBJECT, not a string** — listeners must handle both shapes or the redirect/conversion silently fails.
- Embed modes: JSform (inline hero forms + UTM injection), iframe (isolated; pass UTMs as URL params), raw HTML (fragile). Default JSform inline; iframe for modal.

**Same-domain redirect (tracking-critical):** post-submit redirect MUST stay on the LP's domain — cross-domain redirects silently break GTM/Pixel/PostHog attribution (cookies/context don't carry). Redirect to on-domain `/thank-you` where pixels fire.

---

## 7. Trust bar & social proof placement
Trust is front-loaded and reinforced:
- **Above/within hero:** one compact proof chip (rating + count).
- **Below hero (strip):** review-platform badges, star rating, customer count, partner/press logos.
- **Mid-page (deep proof):** 2–3 full testimonials — **real photo, name, specific result**. Stock faces read fake. Video > text.
- **Near every form/CTA:** micro-trust — "Secure," privacy link, guarantee, "No spam."
- **Near price:** money-back guarantee / free-trial badge.

Never rely on one proof type — stack rating + testimonial + logos + guarantee.

---

## 8. Visual hierarchy, whitespace, typography, color
- **Hierarchy via size, weight, AND color.** Each section: one dominant element, one action, rest subordinate.
- **Whitespace is a feature.** 8px spacing grid; consistent section padding (64–96px desktop, 40–56px mobile).
- **Max 2 typefaces.** Body ≥16px; headings via `clamp()`.
- **CTA color:** exactly one accent, reserved solely for primary CTAs.
- **Contrast:** WCAG AA min — **4.5:1 normal, 3:1 large/UI**. Low-contrast CTAs measurably reduce action.
- **Premium iconography:** consistent set (Phosphor duotone = Scale House default); one style/weight/scale. Never mix libraries or random emoji.

---

## 9. Page speed / Core Web Vitals — the conversion gate
| Metric | Target | Why it gates conversion |
|--------|--------|------------------------|
| **LCP** | **≤2.5s** (aim <2.0s on 4G) | Hero visual/headline is usually LCP; slow = bounce before message lands |
| **CLS** | **≤0.1** | Layout shift causes CTA mis-taps + erodes trust |
| **TBT/INP** | TBT <200ms; INP <200ms | Unresponsive CTA feels broken |
| Total load | <2s on 4G | Compounds all above |
| Page weight | <2MB | The controllable input |

**Hero weight matters most** — it's nearly always the LCP element. An uncompressed 2–4MB hero blows LCP past 5–9s (US Turf: Perf 42 / LCP 9.5s from an uncompressed hero).
**Image discipline:** WebP/AVIF w/ fallback via `<picture>`; **always set explicit `width`/`height` or `aspect-ratio`** (missing dims = #1 CLS cause; US Turf CLS 0.698); compress hero to actual rendered size, responsive `srcset`; `loading="lazy"` below fold, hero **eager** + `fetchpriority="high"`; inline critical CSS, defer non-critical JS; preload hero image + headline font (`font-display:swap`, subset).

---

## 10. Accessibility essentials (that also lift conversion)
Semantic HTML (one `<main>`, `<section>` + real headings); labels on every input; contrast 4.5:1/3:1 (helps outdoor mobile readers); keyboard access + visible focus; alt text on meaningful images; errors announced via `aria-describedby`; skip-nav link; tap targets ≥48px; never convey meaning by color alone. Ship-gate: Lighthouse a11y ≥95.

---

## 11. Attribution & instrumentation
Architecture: **one theme.liquid universal block** (parameterized, before `</head>` on the LIVE theme) handles init + capture + events. Shopify Page bodies strip `<script>` on save — ALL JS lives in theme.liquid behind a path conditional.

**UTM stamping (the spine):**
- On first LP load, capture UTMs → persist to `localStorage`/cookie (survives multi-step + hops).
- **Inject UTMs as hidden fields into every form** so they ride into JotForm/CRM — makes CPL-by-source real.
- **Stamp UTMs onto every PostHog event** so every funnel step is sliceable by source/campaign/ad-group.
- Schema: `?utm_source=google|facebook|tiktok&utm_medium=cpc|paid_social&utm_campaign={slug}&utm_content={adgroup}-{creative}`.

**Canonical 6 funnel events** (a gap between two = the leak to fix):
1. `lp_pageview` (carries UTMs) → 2. `lp_cta_click` → 3. `lp_form_view`/`modal_open` → 4. `lp_form_engage` (first field focus) → 5. `lp_form_submit_attempted` → 6. `lead_form_submitted` (confirmed on **thank-you page** — the only true conversion). Pin as a PostHog funnel per client.

**Pixels fire on thank-you ONLY** — Meta `Lead`/`Purchase` + Google Conversion on `/thank-you`, NEVER on the form page (firing on page-load double-counts + creates phantom leads).

**Verification (every deploy):** incognito Chrome with `?utm_source=smoketest`; confirm `posthog` defined; watch all 6 events fire in order; test-submit and confirm `lead_form_submitted` carries UTMs on thank-you. Never trust curl for Shopify verification. CPL truth = JotForm submissions filtered by UTM, not platform-reported leads. Always bot-filter (Meta paid LPs ~29% bot traffic).

---

## 12. A/B testing wiring & always-on program
A launched LP without a running test is a dead asset. Deliverable = **a live test + a ranked queue behind it**.
- **Wiring (PostHog flags):** create a flag; theme.liquid reads it on load and swaps variant behavior, then stamps assigned variant as an event property on all 6 events. Use `experiment-create` for PostHog's stats engine; raw flag + pinned funnel for manual control.
- **ICE-ranked backlog** in `experiments/backlog.md` (YAML frontmatter the sweep reads). Score Impact × Confidence × Ease; cheap-and-confident (CSS-only fold/CTA tests) outranks expensive-and-speculative early. Seed ≥3 from audit signals (Clarity rage/dead-clicks, scroll depth, form drop-off, funnel gaps). Check the pattern bank before queueing — don't re-test a lever that lost on a comparable client.
- **Two enforced rules:** **Never go dark** (no empty Live section >14 days; backlog dry = audit trigger) · **Don't peek** (decision date set at launch; read at ~100 conversions/arm AND ≥7-day cycle; kill-criterion is the only early exit; bot-filter always).
- **Close the loop:** bot-filter → decide → ship/revert → update backlog frontmatter → write a `learning_lp-test-{lever}.md` + MEMORY pattern-bank row → re-rank, promote next. Each client makes the next smarter.

### Build-order (so instrumentation doesn't silently break)
1. theme.liquid block (PostHog init + UTM capture + 6 events) → 2. LP body HTML/CSS (+ modal funnel JS if iframe) → 3. form UTM hidden-field injection → 4. PostHog funnel insight → 5. Meta Pixel + Google Conversion on thank-you only. Deploy to **LIVE** theme, confirm green Live badge, wait 60s for cache, verify in incognito.
