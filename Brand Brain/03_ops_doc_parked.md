# CREIA Operations: The Ad System

*How the agent operates*

> **STATUS: PARKED — July 2026. Do not build or generate from this document.**
>
> This manual predates the July 2026 Brand Bible revisions and contradicts them. It is retained as the starting point for a future rework, not as a live instruction set. Until then, the Bible is authoritative. Known drift to resolve at rework: the copy-generator prompt hard-codes banned words as auto-fail (including "clean"/"pure", now carved out); exclamation marks and rhetorical questions are auto-fail (the Bible now allows "Otw!" transactionally and "Can't commit?" as a headline hook); the wink and concrete-equivalence hooks are missing; there is no [ASA CHECK] claims workflow; the offer architecture has £49.99 but no free trial (now the lead offer); the CTA list ("Shop now") conflicts with Bible guidance; the visual rules lack the pop set, toy-ish staging, and the Nothing reference; the reference set and Byredo test are stale (Byredo/Skims retired July 2026 — Nothing + David are the copy references, the Byredo test is now the Nothing/David test); the funnel-permission system itself was removed from the Bible (case-by-case now).

This is the operations manual for the ad agent. It specifies the three-layer funnel, the ad genome schema, the generation pipeline, the layer-aware reward model, the measurement framework, and the approval gates.

The companion document, `BRAND_BIBLE.md`, defines what Creia is. That document governs every aesthetic and voice decision referenced here.

## Current scope (what the agent actually ships)

The agent currently outputs two things:

* Still image ads rendered by an image model or composited in HTML/CSS, in 4:5 (feed) and 9:16 (story/reel) formats
* Accompanying copy: headline, primary text, CTA, per the funnel-layer permissions

Destination: Instagram, via the Meta Ads API. Feed, stories, reels-as-static-cards. Other placements (TikTok, Pinterest, email) exist in the brand system but are human-led or downstream of the agent at this stage.

Out of scope: AI-UGC video, native video, creator-led video, and any non-Meta placement. These are v2 extensions. When they come online, the genome extends (motion fields, voice fields, duration, shot list) and the copy generator extends to short scripts. The casting spec, funnel framework, permissions matrix, and reward model all carry over unchanged.

---

## 1. The three-layer funnel (operational spec)

Every ad has a `funnel_layer`. The value determines which copy strategies, desire types, proof elements, offer mentions, and CTAs are permitted.

### Layer definitions

#### top

* Audience: cold. Lookalikes, interest-based, broad-with-age-gender-filter
* Placement: IG feed, IG story, TikTok, Pinterest, reels
* Objective: awareness or engagement, never purchase-optimised
* Budget: 50%
* Evaluation window: 4 weeks minimum for kill, 6 weeks for scale

#### mid

* Audience: warm. Site visitors (30d), video-viewers-75%, social engagers, email-list non-openers
* Placement: feed, story, reel, retargeting
* Objective: add-to-cart or view content
* Budget: 20%
* Evaluation window: 2 weeks

#### bottom

* Audience: hot. ATC (7/14d), initiate-checkout, past purchasers, email openers who did not convert
* Placement: feed, story, reel, catalog ads, dynamic retargeting
* Objective: purchase
* Budget: 30%
* Evaluation window: 5 days

### Permissions matrix

How to read this matrix. The value of `funnel_layer` on a candidate genome determines which copy strategies and desire types the agent is allowed to select from when generating that candidate. The compliance critic rejects any candidate whose `hook_type` or `desire_type` falls outside the permitted set for its declared layer, and the copy generator is forced to re-roll with an in-range choice.

"Not permitted at this layer" is a contextual rule, not a universal ban. Every strategy and desire type is correct somewhere in the funnel.

#### Copy strategies by layer

* **top, permitted:** cultural-adjacency, sensory-misdirection, unexplained-reference, object-list, flat-ending, negative-confidence
* **top, not permitted at this layer:** quiet-specificity (product facts before anyone cares)
* **mid, permitted:** all top-layer strategies plus quiet-specificity
* **bottom, permitted:** all seven

#### Desire types by layer

* **top, permitted:** identity, aesthetic, social, sensory
* **top, not permitted at this layer:** functional (answers a question nobody has asked)
* **mid, permitted:** identity, aesthetic, social, sensory
* **mid, not permitted at this layer:** functional (still too early in the relationship)
* **bottom, permitted:** all five, including functional

#### Proof, offer, CTA by layer

* **top:** no proof, no offer, CTA = "Learn more" or absent
* **mid:** light proof (one UGC-style clip or press mention), minimal offer (format mention allowed, price not foregrounded), CTA = "Shop the 30-pack"
* **bottom:** full proof (reviews paraphrased, press mentions, numbers, no star ratings), full offer architecture, CTAs = "Shop now," "Subscribe and save"

### Universal rules (all layers, no exceptions)

* The banned language list
* The banned structures list
* The required constraints (Byredo test, flat-ending, one-specific-noun)
* The visual identity rules (flash photography, palette, no gym context, typography)
* The casting spec (early 20s, model-tier physique, anchor reference = elevator image)
* The voice

---

## 2. The ad genome (schema)

### Discrete fields

* `funnel_layer`: enum [top, mid, bottom]
* `format`: still, video, motion-still, UGC, editorial
* `hook_type`: cultural-adjacency, sensory-misdirection, quiet-specificity, negative-confidence, flat-ending, unexplained-reference, object-list
* `persona`: target archetype (8-12 maintained)
* `angle`: one-sentence argument
* `pain_articulated`: boolean
* `desire_type`: enum [identity, aesthetic, social, sensory, functional]
* `desire_object`: free text, mandatory
* `proof_element`: absent, light, full
* `offer_mention`: absent, minimal, full
* `product_asset`: asset brain reference
* `placement`: feed, story, reel, tiktok, pinterest
* `landing_page`: must match funnel_layer
* `axis_under_test`: the one variable this ad isolates
* `risk`: low, medium, high

### Format and differentiation fields

* `format_family`: structural pattern family (e.g., "stat-led-still," "in-hand-flash," "elevator-mirror-shot")
* `competitor_usage_count`: number of distinct competitor brands running ads in this format_family in last 90 days
* `competitor_longevity_days`: longest run time of any ad in this format_family across the competitor set
* `pattern_saturation`: 0 to 1, density of this format_family in the competitor library
* `differentiation_score`: 0 to 1, embedding distance between this candidate and the format_family centroid
* `competitor_prior`: 0 to 1, derived signal. High when usage_count >= 3 AND longevity_days >= 180

### Casting fields

* `casting_spec`: enum [lead, secondary, fragment, absent]
* `casting_anchor_match`: 0 to 1, classifier score against approved Creia imagery
* `casting_notes`: free text, model attributes / styling / attitude

### Latent fields

* `visual_embedding`: CLIP embedding
* `copy_embedding`: sentence embedding of headline + body
* `aesthetic_score`: brand-fit classifier output

---

## 3. The copy generator prompt (layer-aware)

Takes `funnel_layer` as required input and adjusts permissions dynamically. Banned language list never changes.

### System prompt (static)

```
You are writing copy for Creia, a premium fashion-adjacent wellness brand
selling creatine in single-serve sachets. Reference set: Miu Miu, Rhode,
Bottega Veneta, Byredo, Chrome Hearts (for cultural positioning, not
aesthetic), Skims. Photographic reference: Terry Richardson, Juergen
Teller, Glen Luchford. Anti-reference: every supplement brand, every
fitness-influencer brand, every "wellness at home" beige-linen brand.

Audience: woman aged 24 to 34, UK urban, high visual literacy. Not a gym
person.

Banned words (auto-fail): easy, easier, effortless, simple, simply,
routine, ritual, daily dose, consistency, transform, level up, unlock,
elevate, empower, game-changer, finally, no more, optimise, performance,
clean, pure, proven, clinically, science-backed, smart, feel the
difference, scoop-free, tub-free, mess-free, meet, introducing, designed
to, built to, crafted to.

Banned structures (auto-fail): tricolons, rhetorical questions,
transformation framing, parallel negation, sentences starting with "just"
or "meet," exclamation marks, em-dashes as flourish. Parallel pairs
allowed in editorial register.

Required: one concrete non-creatine noun per stanza; one descriptor per
noun max; sentences end on a noun or flat fact; Byredo test.

Register: confident, flat, culturally literate, comfortable with silence.
```

### Layer addenda

#### funnel_layer == top

```
Allowed hooks: cultural-adjacency, sensory-misdirection,
unexplained-reference, object-list, flat-ending, negative-confidence.
Allowed desires: identity, aesthetic, social, sensory.
No proof. No offer. No price. No urgency. CTA = "Learn more" or absent.
Do not mention "creatine" in the headline. Make her want to be the kind
of person who owns this.
```

#### funnel_layer == mid

```
All top-funnel hooks plus quiet-specificity.
Allowed desires: identity, aesthetic, social, sensory.
Light proof permitted: one press outlet or UGC voice, plain.
Format may be named. Price mentioned but not foregrounded.
CTA = "Shop the 30-pack," "Try it."
```

#### funnel_layer == bottom

```
All seven hooks. All five desires including functional.
Full proof: reviews paraphrased in brand voice, press mentions, numbers.
No star rating graphics.
Full offer: price (£49.99), subscription, shipping, bundles.
CTAs: "Shop now," "Subscribe and save."
Headline word limit relaxed to 12 when offer embedded.
Still passes Byredo test. No discount banners, countdown language, or
"LAST CHANCE."
```

---

## 4. The learning loop (layer-aware, differentiation-aware)

A contextual bandit with structured actions and delayed, noisy rewards. The reward modelling is layer-aware: a unified model trained across all layers would collapse toward bottom-funnel signals (which have the strongest short-horizon data) and reward the agent for producing bottom-funnel ads everywhere. To prevent this, the system uses one reward model with layer-specific weighting, or three reward models during the seed phase.

### State

* Brand inventory per layer: which winners are live in top, mid, bottom
* Fatigue age per creative
* Competitor saturation per format_family
* Competitor longevity per format_family
* Audience coverage: persona × desire_type × funnel_layer cells tested
* Seasonality
* Budget utilisation per layer

### Action space

* Discrete: funnel_layer, format, format_family, hook_type, persona, desire_type, proof, CTA, offer, placement, casting_spec
* Continuous: visual embedding, copy embedding
* `axis_under_test` flag for counterfactual credit assignment

### Reward function per layer

#### top

```
score_top = 0.40 * cohort_LTV_delta_90d +
            0.25 * assisted_conversions +
            0.15 * branded_search_lift +
            0.10 * direct_traffic_lift +
            0.05 * email_signup_rate +
            0.05 * first_party_survey_awareness_lift
```

Meta reported ROAS is explicitly NOT weighted at top-funnel. Short-horizon CTR/CPC signals are used only for fatigue detection, not for reward.

#### mid

```
score_mid = 0.35 * add_to_cart_rate +
            0.25 * assisted_conversions +
            0.20 * view_through_conversions +
            0.15 * cohort_LTV_delta_90d +
            0.05 * immediate_CVR
```

#### bottom

```
score_bottom = 0.45 * immediate_CAC_inverted +
               0.25 * LP_CVR +
               0.15 * AOV +
               0.10 * subscription_take_rate +
               0.05 * 30d_repeat_rate
```

### Acquisition function (differentiation-aware)

For candidate ranking within a batch:

```
score = layer_reward
      + lambda * uncertainty
      + mu * novelty_bonus
      + tau * competitor_prior
      - sigma * pattern_saturation * (1 - differentiation_score)
```

Two key behaviours:

* Saturation penalty is multiplied by `(1 - differentiation)`. When Creia's version is highly differentiated from the format's centroid, the penalty approaches zero even if the format is crowded
* `competitor_prior` is a positive term. When a format_family has been run by 3+ unrelated competitors for 180+ days, it provides a small positive bias toward adopting that format

### Starting weights per layer

* **top:** lambda=0.35, mu=0.25, tau=0.15, sigma=0.30
* **mid:** lambda=0.20, mu=0.15, tau=0.20, sigma=0.20
* **bottom:** lambda=0.10, mu=0.05, tau=0.25, sigma=0.10

### Exploration split per layer

* **top:** 20% exploit, 55% explore, 25% wildcard
* **mid:** 50% exploit, 30% explore, 20% wildcard
* **bottom:** 70% exploit, 20% explore, 10% wildcard

### Forced exploration

* If top-layer top-10 converges to fewer than 3 distinct format_families for 3 weeks, force 40% wildcard for the next week
* If `pattern_saturation > 0.8` AND `differentiation_score < 0.4` for a winning creative, archive and force divergence
* If a persona × desire_type × layer cell has no data, prioritise it
* When a wildcard wins at top, elevate that format_family's exploration weight for 4 weeks across all layers

### Cross-layer signal

When a winning visual at top-funnel is detected, automatically queue a variant of the same visual for mid-funnel testing (adding quiet-specificity) and for bottom-funnel testing (adding offer mention). Format consistency across layers compounds brand recognition.

### Cold start

In Phase 1 and Phase 2, the saturation penalty weight (sigma) should be tuned down significantly to let the agent borrow format freely. The brand system itself does the differentiation work at this stage. Saturation penalty becomes meaningful only once there is enough first-party performance data to distinguish "this format saturated" from "this format underperformed for unrelated reasons." Starting recommendation: run with sigma at 50% of target value initially, then ramp.

---

## 5. Measurement per layer

### Top-funnel

#### Primary signals

* Branded search volume lift
* Direct traffic share growth
* Email signup rate from new visitors
* Assisted conversions (Meta view-through + 28-day click)
* Post-purchase survey attribution
* 90-day cohort LTV per creative exposure

#### Secondary signals (fatigue detection only)

* CTR, thumbstop, hold rate
* CPM (delivery sanity check)
* Frequency

#### Kill / scale criteria

* Kill: freq > 3.5 AND CTR decline > 30%, or 4 weeks in bottom quartile of cohort composite score
* Scale: above-cohort composite for 3 consecutive weeks, detectable branded search lift

### Mid-funnel

* Add-to-cart rate, view-through conversions, retargeting pool-to-conversion rate, time-from-first-impression
* Kill: freq > 4 AND CTR decline > 25%, or below-cohort ATC for 2 weeks
* Scale: above-cohort ATC for 2 weeks + positive view-through contribution

### Bottom-funnel

* Immediate CAC (7d click), LP CVR, AOV, subscription take rate, 30d repeat rate
* Kill: below-cohort CAC for 5 consecutive days at significance, or freq > 5 AND CTR decline > 20%
* Scale: above-cohort CAC for 7 consecutive days + LP CVR top quartile

### Master business KPIs

* Monthly new unique customers
* Blended CAC (all paid / all new)
* 90-day cohort LTV
* 30, 60, 90-day cohort repeat rate
* Monthly branded search volume
* Monthly direct traffic share
* MMM output, monthly

When business KPIs diverge from per-ad reward functions, business KPIs are right. Per-ad models are retuned to match.

---

## 6. Budget allocation

### Target split

* Top: 50%
* Mid: 20%
* Bottom: 30%

### Guardrails

* Top floor: 40% of total
* Bottom ceiling: 40% of total
* No layer drifts below 70% of target share for more than 2 weeks without documented override

### Override conditions (documented start/end only)

* Product or flavour launch (mid can rise to 30%)
* Post-holiday clearance (bottom up to 45% for 2 weeks)
* Seeding cultural moment (top up to 60%)

### The 50% defence

* Geo holdout quarterly: compare full-funnel vs bottom-only market
* Track bottom-funnel ROAS against audience pool size
* MMM monthly for correct attribution

---

## 7. Approval checklist

### Compliance (automated)

* No banned words
* No banned structures
* Passes required constraints
* Hook_type permitted for declared funnel_layer
* Desire_type permitted for declared funnel_layer
* Proof / offer / CTA match funnel_layer permissions
* casting_anchor_match above threshold for casting_spec level

### Brand fit (automated)

* Passes Byredo-test classifier
* Novelty score above threshold
* Differentiation score above threshold for the format_family
* (pattern_saturation × (1 - differentiation_score)) below ceiling

### Genome completeness (automated)

* All required fields filled
* axis_under_test named
* desire_object written as free text, not a category label
* format_family named
* casting_spec declared
* landing_page matches funnel_layer
* kill_criteria defined

### Human gate

* Brand custodian reviewed
* Would not embarrass the brand to a reader of 032c
* Launched in counterfactual pair where possible

---

## 8. Working templates

### Example genome row

```json
{
  "genome_hash": "a7f3c",
  "funnel_layer": "top",
  "format": "still",
  "format_family": "elevator-mirror-shot",
  "hook_type": "object-list",
  "persona": "pilates-after-work-urbanist",
  "angle": "Creia as one object among a composed night",
  "pain_articulated": false,
  "desire_type": "identity",
  "desire_object": "the woman in the lift with the glass and the sachet",
  "proof_element": "absent",
  "offer_mention": "absent",
  "product_asset": "sachet_flash_stainless_v3",
  "placement": "ig_feed_4x5",
  "landing_page": "lp_brand_beyond_v2",
  "axis_under_test": "object_list_vs_single_hero",
  "competitor_usage_count": 1,
  "competitor_longevity_days": 45,
  "pattern_saturation": 0.18,
  "differentiation_score": 0.82,
  "competitor_prior": 0.12,
  "novelty_score": 0.71,
  "casting_spec": "lead",
  "casting_anchor_match": 0.78,
  "casting_notes": "early 20s, narrow-framed, dark hair, black tank, sunglasses indoors, reflected in chrome-lined lift",
  "risk": "low",
  "headline": "Keys, passport, perfume, creatine.",
  "body": "A small sachet among the other things.",
  "cta": "Learn more",
  "kill_criteria": {
    "freq_threshold": 3.5,
    "ctr_decline_threshold": 0.30,
    "min_evaluation_days": 28,
    "min_spend_before_judgement": 840
  }
}
```

### Casting reference card

#### The anchor image

Elevator shot. Early 20s model. Narrow frame. Black fitted tank top. Black fitted shorts. Dark sunglasses (early 2000s wrap style). Silver hoop earrings. Silver watch. Mirrored lift walls reflecting her sideways. Holding a glass of water with a Creia sachet visible in the glass. Detached expression, slight pout, not smiling, not looking at camera. Flash photography. Chrome and black palette.

#### Must-have attributes

* Age: 21 to 25
* Height: 170cm or taller (lead casting)
* Build: model-tier, narrow frame, long limbs
* Face: editorial, slightly unusual
* Skin: natural, minimal makeup
* Hair: unstyled or slept-in
* Attitude: caught, not posed; slightly bored; no warmth for camera

#### Disqualifiers

* Over 28
* Visible gym muscle or performance posture
* Commercial-smile casting
* Wellness-influencer aesthetic
* Full-beat glam makeup
* Direct-to-camera friendly eye contact

#### For agent-generated imagery

When the agent generates visual candidates, the `casting_notes` field must explicitly describe the model's physical attributes and styling. Generic prompts like "a woman holding the sachet" are rejected at the compliance critic stage. Required: age, build, face-type reference, hair state, styling, expression, lighting.
