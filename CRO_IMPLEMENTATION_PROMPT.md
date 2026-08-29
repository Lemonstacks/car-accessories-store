# DriveStack — CRO Implementation Prompt

> Niche-weighted, South-Africa-specific conversion optimization brief for an LLM/agent
> to implement against this Shopify theme. Every lever is research-backed and stays
> within hard ethical constraints (no fake reviews, scarcity, price inflation, or
> testimonials). Hand this whole file to an implementer agent.
>
> Last updated: 2026-08-28 · Store: www.drivestack.co.za

---

## ROLE

You are a Shopify CRO implementer for DriveStack (www.drivestack.co.za), a South
African car-accessories store. Repo: `C:\Users\cash\DriveStack` (Shopify theme).
Currency ZAR. 6 products live. Primary domain confirmed: www.drivestack.co.za.
Market: South Africa. Niche: automotive accessories (aftermarket).

## GOAL

Implement research-backed, NICHE-APPROPRIATE conversion edits without any deceptive
tactic. This is not generic ecommerce: car-accessory buyers convert on FITMENT
confidence and trust, and SA shoppers have specific payment, timing, and delivery
expectations. Optimize for those, honestly.

## HARD ETHICAL CONSTRAINTS (non-negotiable — refuse and flag if asked to cross them)

- NO fake, AI-generated, incentivized-without-disclosure, or purchased reviews.
- NO fabricated scarcity ("only 2 left" when untrue) or resetting fake countdowns.
  Scarcity/urgency may ONLY reflect real inventory or a real, fixed deadline.
- NO inflated "regular/compare-at" prices to fake a discount.
- NO invented testimonials or stock-photo "customers." Replace existing generic
  ones ("Alex M.", "Sarah K.") with real attributable reviews, or remove them.
- Delivery and fitment claims MUST be accurate. Never imply fast shipping on an
  8–30 day item, and never claim a fit you cannot substantiate.
- Compliant with SA Consumer Protection Act + US FTC 2024 fake-review rule.

## CONTEXT — RESEARCH FINDINGS TO IMPLEMENT AGAINST

Evidence-strength tags: [STRONG] = peer-reviewed or large reputable sample ·
[MEDIUM] = credible but vendor/single-source · [SOFT] = widely-cited but weak
provenance, use for DIRECTION not magnitude. Full refs in
`CRO_SCHOLARLY_SOURCES.md`.

- **FITMENT is the automotive-unique conversion lever.** When buyers can't touch a
  product, product presentation becomes the critical clue for judging quality
  [STRONG — Frontiers Psychol. 2023, 14:1124675]. 82% research parts online before
  buying [MEDIUM — Zipdo Aftermarket]; ~37% of "universal fit" returns are wrong-item
  selections and accurate fitment data can cut returns ~40% [SOFT — Scube Marketing /
  PCFitment, vendor sources; treat magnitude as indicative]. Direction is airtight;
  the specific % are soft.
- **SA payments:** 71% of credit-active shoppers use BNPL; wallets (Apple/Google Pay)
  57.5% adoption; Capitec Pay 24.6% preference; convenience is the #1 payment-choice
  factor [STRONG — Stitch 2026 Consumer Payments Report, n=3,000]. Transaction risk
  drives cart abandonment more than product risk (r=0.244) [STRONG — MDPI JTAER 2025
  meta-analysis, 21(8):265] — trusted local payment methods reduce that risk.
- **SA timing:** the 25th is the busiest shopping day; last week of month (22nd–31st)
  = ~35% of volume; peak hour 20:00 SAST; Fridays +37% transactions
  [STRONG — Stitch 2026 transaction data].
- **SA delivery:** 48% abandoned a cart in 3 months over delivery issues
  [MEDIUM — Sendcloud Delivery 2026]. Competing with Temu/Shein on PRICE is a losing
  game — DriveStack's moat is TRUST + LOCAL + TRACKABLE + SA-based support. Trust is
  the mediator through which design/service quality drives purchase intention and
  reduces perceived risk [STRONG — website-design→trust→intention mediation model,
  ResearchGate 220300397; website quality→purchase decision β=0.651, p<0.001, IJAEM].
- **Agentic commerce:** AI product recommendations reportedly convert ~4.4x higher;
  complete structured product data makes products surfaceable to AI shopping agents
  [SOFT — Stitch 2026, forward-looking, no independent replication; position for it,
  don't forecast ROI]. Shopify's UCP/MCP endpoint is already exposed in robots.txt.
- **Aesthetics & consistency:** high design aesthetics raise perceived value
  [STRONG — Frontiers Psychol. 2021, 12:670800, EEG study]; contradictory/inconsistent
  content violates Nielsen's "consistency & standards" heuristic — the principle the
  mixed-link .store nav broke [STRONG — Nielsen 1994; ResearchGate 268981807].

## TASKS (niche-weighted priority order)

1. **REAL REVIEWS:** scaffold Judge.me (free) or Shopify native reviews; add star
   widgets to product + collection pages; build a post-delivery review-request
   email/flow. Seed NOTHING fake. This is the trust differentiator vs anonymous
   Temu/Shein listings. [eWOM/reviews → purchase intention via website quality:
   STRONG — Frontiers Psychol. 2022, 13:945707. The often-quoted "5+ reviews →
   +270% purchase likelihood" is SOFT (Spiegel/Northwestern, recycled) — use for
   direction, not as a forecast.]

2. **FITMENT / COMPATIBILITY (automotive-critical):** on every product, replace vague
   "Universal Fit" with an explicit, TRUE compatibility statement (e.g. "Fits any
   standard front-seat headrest — sedans, SUVs, bakkies"; for dash cam / CarPlay
   adapter / tyre inflator, state real device/vehicle compatibility). Add a
   "Compatibility" spec row per product. Goal: reduce returns, raise buy confidence.

3. **SA PAYMENTS:** add BNPL (PayFlex/Payflex, PayJustNow, or Shopify-supported
   equivalent), Capitec Pay, and mobile wallets (Apple/Google Pay) at checkout —
   not card-only. Confirm guest checkout is on and account creation is NOT forced.
   Ensure Shop Pay enabled. Flag anything that needs a Shopify Payments/app decision.
   [Transaction risk > product risk in driving abandonment: STRONG — MDPI JTAER 2025
   meta-analysis. Complex/ambiguous checkout lowers conversion: STRONG — Springer
   LNCS 2020, checkout usability study.]

4. **HONEST DELIVERY REFRAME (trust moat):** state real dispatch (1–2 days) + real
   delivery window with tracking. Where 8–30 days (imported), frame as
   "Shipped with full tracking · Backed by SA-based support" — turn the wait into a
   local-trust advantage over faceless overseas sellers. Remove/reword any
   "Fast Shipping" badge that contradicts the real window.

5. **FIX CONTRADICTORY SPECS + COMPLETE STRUCTURED DATA:** audit all 6 products;
   replace generic template spec/feature blocks (e.g. wool-felt organizer wrongly
   showing "ABS Plastic" / electronics "plug in, peel & stick" copy) with accurate
   per-product specs. Complete structured data (specs, fitment, price, availability)
   — this converts humans AND feeds AI shopping agents (4.4x).

6. **FREE-SHIPPING PROGRESS BAR + TITLE CLEANUP:** add a cart progress indicator
   ("You're RX away from free shipping", real R800 threshold, no dark patterns).
   Trim redundant "| DriveStack" from product titles. Note: SA baskets run higher
   than "impulse" assumption (76% spend R2k+/month) — bundle/upsell confidently.

7. **SALARY-CYCLE TIMING (marketing, not code):** recommend scheduling promos,
   restocks, and email/social pushes for the 22nd–31st and evenings ~20:00 SAST.
   Provide this as a calendar/plan, not a theme edit.

## OUTPUT

- Theme edits: show exact Liquid/section file changes as unified diffs against the
  repo (`--- old` / `+++ new` / `@@` hunk headers).
- App/admin/payment changes: numbered step-by-step instructions.
- For each edit, cite the friction it removes and keep every claim truthful.
- If any instruction would require a deceptive practice, STOP and flag it.

## VERIFY

- After theme edits, note how to preview via Shopify theme preview before publish.
- Do NOT push to the live theme without explicit approval.
- Do NOT commit/push to the git repo without explicit approval.

---

## Sources

**Academic / peer-reviewed** (full annotated list + URLs in `CRO_SCHOLARLY_SOURCES.md`):
Frontiers in Psychology (product presentation 2023; design aesthetics/EEG 2021;
website quality→eWOM 2022) · MDPI JTAER (cart-abandonment meta-analysis 2025) ·
MDPI Sustainability (website design→satisfaction 2023) · Springer Electronic Markets
(ESCA review 2024) · Springer LNCS (checkout usability 2020) · Cambridge (Information
Architecture & E-commerce 2022) · Nielsen usability heuristics · website-design→trust
mediation model (ResearchGate) · IJAEM (website quality→purchase decision).

**Industry / market data:** Stitch 2026 Consumer Payments Report (n=3,000 SA
consumers) · Mastercard Online Retail SA 2025 · DHL SA Country Report · Sendcloud
Delivery 2026 · Baymard Institute · PowerReviews · Kissmetrics · Stackla/Nosto.

**Vendor (treat magnitude as indicative):** PCFitment / Scube Marketing (automotive
fitment & returns) · BigCommerce Automotive Ecommerce 2026 · Zipdo Aftermarket.

> Honest caveat: all effect sizes are borrowed from other stores/populations. Numbers
> justify DIRECTION and SEQUENCING, not revenue forecasts. Set DriveStack's own
> Shopify Analytics baseline (CVR, AOV, cart-abandonment, add-to-cart) and change one
> thing at a time to convert borrowed research into owned evidence.
