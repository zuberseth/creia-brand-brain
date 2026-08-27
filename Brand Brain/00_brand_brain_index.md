# Brand Brain — Index

The codified, machine-readable version of Creia's brand and design system. Single source of truth for any agent (Lovable, Claude, Cursor, Figma, ad pipeline) producing on-brand work.

**Restructured July 2026.** Three active documents. Retired material lives in `Archive/` and is excluded from normal agent routing.

---

## The documents

| Doc | Role | Status |
| -- | -- | -- |
| **Brand Brain — Index** (this doc) | Entry point, routing, canonical facts | Active |
| **Brand Bible — Creative** | Seven parts: I. The Brand · II. Copy System · III. Creative Design System · IV. The Product · V. Facts Bank · VI. Adapting & Channels · VII. Asset Register | Active; task-routed production system live (Bible rev. ix, July 2026) |
| **Web Design System** | creia.com implementation: components, tokens, typography, layout, motion | Active — consolidated July 2026 |

---

## Routing for agents

* **The Bible's primary purpose:** adapt winning reference creatives to Creia, and generate Creia ads + emails. Not editorial work.
* **Creative-rule scope and exceptions** → Bible §4. Concept, frame and batch replace ambiguous creative uses of "asset". Agents may declare narrow creative deviations; required production contracts and text-mode gates change only on explicit user direction, while source data and approved masters stay fixed.
* **Writing any copy** (ad, email, social, packaging, OOH) → Bible Part II (how to write), Part IV (product truth), Part V (what you may claim). Anything not Verified in Part V gets an [ASA CHECK] flag in output metadata or the copy deck, never in artwork or image prompts; the claim is never softened or dropped.
* **Designing any creative** → Bible Part III (+ Part IV for the spec block, Part VII for source assets).
* **Making, copying or adapting standard ads** → Bible §12 for image generation, text modes and production gates, then §30 for the mandatory prompts, generated outputs when direct model access exists, and copy-deck handoff.
* **Making carousels** → Bible §12A. Keep carousel production separate from standard-still and email contracts.
* **Making emails** → Bible §9 for copy and §31 for the designed-email or plain-text contract. Email hero images follow the shared creative direction but do not inherit paid-social aspect ratios.
* **Building or editing creia.com** → Web Design System. Copy on the site still follows Bible Part II.
* **Ad pipeline work** → Live generation behaviour comes from Bible §§12 and 30–31; source assets come from Part VII. The archived OPS_DOC must not supply prompts, CTAs, funnel permissions or visual rules.
* **Fact disputes** → the block below, then Bible Parts IV–V. If an asset disagrees with Part IV, the asset is wrong.

## Two domains, one rule

Creative follows the Bible. The website follows the Web Design System. When they appear to conflict, scope decides; the split is intentional (calmer site, louder creative). Web typography follows the Web Design System. Final Creia ad type is Area Extended, except approved NATIVE_TEXT under Bible §12. Web colour is neutral-only. Creative uses deep black, flash white and material neutrals; if a concept uses a pop, one pop colour belongs to a minimal number of discrete physical props across that concept.

---

## Canonical facts (settle disputes here)

* Domain: **creia.com** · Sender: **team@creia.com** · Instagram: **@drinkcreia**. Exact existing packaging masters may retain their already-printed `getcreia.com`; all new copy and reconstructed packaging use `creia.com`
* From-names: brand emails **Creia**; founder emails **Faith from Creia**, signed Faith, Creia Founding Team (never "Founder")
* Composition per 8g sachet (label-confirmed July 2026): **5g 200-mesh ultra-micronised creatine monohydrate · 350mg pink Himalayan salt · 60mg magnesium · natural lemon flavouring (Dirty Lime) · citric acid · stevia extract**. "400mg electrolytes" = salt + magnesium, approved. 0 calories, all-natural
* Spec block: 5g Creatine · 400mg Electrolytes · 0 Calories · All-Natural Ingredients
* Full pricing: 30-day **£49.99 one-time / £39.99 sub**; 3-month **£129.99 one-time / £79.99 sub**. Email prices are discounted offers, never list
* Trial: 5 days, 5 sachets, **free**, no auto-subscribe, **£3.95 postage** at checkout (kept out of email copy). 10-day trial £8.95, free shipping
* Beef equivalence: **one kilo** of raw beef = one sachet's 5g (the site's "two kilos" is being corrected). High-performing fact
* Protocol: one sachet a day in cold water; flexible dosing to two sachets on demanding days ("One sachet a day for extra energy. Two a day to turn into megamind.")
* Dimensions: box 12.5 × 11 × 8.5 cm (125 × 110 × 85 mm); sachet 120 × 35 × 10 mm
* Tagline: **Beyond the gym.** Internal pillars: Cognition. Energy. Recovery. Consumer phrasing: Brain power. Clean energy. Lean definition
* Audiences: primary women 24–34 UK urban; secondary yummy mummies (mid-30s–mid-40s, same creative world); tertiary the cool guys (adopt, not pursued)
* Copy references: **Nothing + David (protein)**. Byredo and Skims are retired as references
* Type: final Creia ad type is assembled in post in **Area Extended** (primarily Bold; lower weights for body); **Hubot Sans only for small text/subtext**. Approved NATIVE_TEXT under Bible §12 is the bounded generated-text exception. Instrument Serif retired. Font licence for AI/render use confirmed (Jul 2026)
* Logo "black" = navy #0D191F, confirmed intentional (Jul 2026). Standalone wordmarks use approved post-production masters, never image-generated substitutes
* Shipping: same-day dispatch before 1pm Mon–Fri; next-day UK delivery
* Product renders + brand assets: this repo, folders at root (see Bible Part VII and `creia_assets_index.md`)
* Founder / casting face: Faith Charnock (in-range, rights cleared) — `Casting/`

---

## Archive

`Archive/03_ops_doc_parked.md` preserves the retired ad-system manual for historical reference. It predates the July 2026 Bible revisions and contradicts them. Do not read, retrieve or generate from it unless explicitly reworking that historical system.

## Gaps and open questions

* **Assets** — Bible §33. Done: product masters, approved wordmarks, installed fonts and licence, safe-zone guides, dimensions, fixed identity colours and current casting reference. Remaining: typography specimen; editable 4:5/9:16 assembly templates; logo finishing; tagged photography and prop library; ad/email, flash, contrast/black-level, pop-prop and anti-reference boards; moodboard mirror.
* Future operational agent specification, if needed; build it from the active Bible rather than reviving the archived OPS_DOC
* Asset errata: two infographics carry factual/typo errors (Bible Part V §28); the site's "two kilos" line needs correcting to 1kg
* Testimonials: unparked Aug 2026. creia.com carries a 161-review placeholder dataset with the 4.91/5 "Trusted by 1,000+ customers" banner (live 7 Aug 2026) and review cards under the buy widgets (10 Aug). Real reviews collected via Judge.me on the Shopify thank-you page replace the placeholder set once they exist
* Counsel pass on the §27 infographic claims (bulk myth, water/bloat, brain dosing) — currently [ASA CHECK]

## Changelog

* **August 2026:** Testimonials unparked. creia.com has carried a 161-review placeholder dataset, the 4.91/5 "Trusted by 1,000+ customers" banner and review cards under the buy widgets since 7 and 10 Aug 2026; real reviews via Judge.me on the Shopify thank-you page will replace the placeholder set. Gaps entry updated.
* **July 2026 (Bible rev. ix):** Standard ads, carousels and emails now route through separate production contracts. Copied and scratch ads share one prompts-plus-copy handoff; Zuber owns final typography and standalone wordmark assembly by default, while explicit full-production requests must verify generated imagery before adding text. Creative-rule scope is now defined by concept, frame and batch, with a narrow declared-deviation protocol and fixed source data. Duplicate workflow, reference and asset-status rules were consolidated; repo-root paths and missing-reference fallback were corrected.
* **July 2026 (repository cleanup):** Obsolete handoff guidance was tombstoned, OPS_DOC moved to `Archive/`, the 90-days source-language digest moved to `Corpus/`, web typography mapped to supplied font weights, the asset index became a factual manifest and the mislabelled casting PNG extension was corrected.
* **July 2026 (Bible rev. viii):** AI ad-production protocol added. Copied ads now return independent 4:5 and 9:16 prompts, outputs when direct generation is available, and an exact copy deck; text modes, native-text gate, deterministic post-production and generation/export QA are live.
* **July 2026 (repository migration):** Brain migrated to the private GitHub repo zuberseth/creia-brand-brain. Docs and assets now live in one place; git history is the changelog from here on. Linear docs retired as [MOVED] mirrors.
* **July 2026 (vii):** Bible §29 expanded with the full live 90-days page (creia.com/90-days-with-creia) — phase-by-phase science and quotable lines, "provably" flagged for ad reuse. Asset decisions logged: transparent box renders not needed; logo navy #0D191F confirmed intentional; font licence confirmed; extra casting range skipped for now. Aesop/Byredo line scrubbed from the Web Design System; OPS_DOC drift banner updated (stale reference set, funnel system removal).
* **July 2026 (vi):** Bible fully rewritten clean from Zuber's annotated markdown. Agent-first purpose note (adapt winning creatives + generate ads/emails, not editorial); contractions throughout the doc; noun-poetry strategies retired (cultural adjacency, sensory misdirection, quiet specificity, flat ending) with the worst examples moved to Bad; funnel-permission system removed (case-by-case); Nothing + David made primary copy references (Byredo test → Nothing/David test); yummy mummies added as secondary audience (cool guys → tertiary); myth-buster voice recast as confident/playful/cool; shoot rules relaxed (cool gym objects, vintage gymwear, tasteful before/after); Canva section added for email + carousel skeletons; canon examples cleaned and Zuber's new lines added (caffeine, coffee-signal, megamind); David added to corpus. Part VI renamed Adapting & Channels; Part VII renumbered (§33–34).
* **July 2026 (v):** Product-render masters produced and logged (Bible Part VII). Logos, fonts, safe-zone templates, dimensions, colour reference, and founder casting reference added to `Creia Assets`. Testimonials parked by decision.
* **July 2026 (iv):** Infographic-carousel facts folded into Bible Part V (§24 cognition/body claims promoted to Verified per GC; §27 new claims pending counsel). Asset Register added as Bible Part VII. Trial postage corrected to £3.95. Myth-buster and educational-carousel formats canonised.
* **July 2026 (iii):** Bible restructured into parts. Product composition added from confirmed label. Facts & Statistics Bank added. Canonical pricing settled; 1kg beef canon. Liquid template links fixed to creia.com.
* **July 2026 (i–ii):** copy gates loosened to defaults; [ASA CHECK] workflow; wink register + Nothing reference + pop set; email titles canonised ("Otw!" exception); Web Design System consolidated; OPS_DOC parked; Index rewritten.
* **April 2026:** Brain established.
