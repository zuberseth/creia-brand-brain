# Creia Brand Brain — Handoff Document

**Purpose of this doc:** everything a new agent (Fable 5) needs to continue building out the Creia Brand Brain. Read this first, then the four brand docs and the to-do file. Written July 2026 by the prior agent.

---

## 1. What this project is

Creia is a premium creatine brand for women 20–35, positioned as fashion-adjacent (Miu Miu / Rhode / Nothing), not a gym supplement. The **Brand Brain** is a set of documents that act as the single source of truth so that any agent — copy, design, web, or an automated ad pipeline — produces on-brand work. The end goal Zuber is driving toward: **a generation-ready source of truth that can batch-create on-brand ad variants and creatives** (product + copy + eventually people), with a real asset library the pipeline can pull from instead of hallucinating.

We are ~80% of the way to "generation-ready." Core identity is anchored (product, logo, fonts, safe zones, colour, a founder casting face). What remains is library depth and one big conceptual task: a **design-system cohesion pass**.

---

## 2. Where everything lives

### The Brain (Linear — "Brand Brain" project, workspace `healf-creia`)

Editing the brain = editing these Linear documents via the Linear connector (MCP). Four active docs + stubs:

| Doc | Linear ID | URL slug |
| -- | -- | -- |
| Brand Brain — Index | `d58bb901-2351-474a-a636-880576f24c00` | brand-brain-index-4ef5a5a45136 |
| Brand Bible — Creative | `2db6593f-a291-4f10-81eb-c78abd3b7f54` | brand-bible-creative-d13f40d1470c |
| Web Design System | `0f5fd387-1815-4470-a929-67c7ee19d5db` | web-design-system-36ee85a9886e |
| [PARKED] OPS_DOC — The Ad System | `8f474783-181e-400e-8a32-dd774bcc8803` | parked-ops-doc-the-ad-system-1ccc3cad1768 |
| [SUPERSEDED] Design System (stub) | `9a8f5458-486a-4ebf-80fc-b5756dd7d1bf` | — archive in UI |
| [SUPERSEDED] Typography Reference (stub) | `894ba9d3-962e-476c-8afe-07c383e1cea9` | — archive in UI |

Project ID: `989ffac4-c62d-4d81-ae4a-3ee04baa6e95`. There is also a second superseded Design System duplicate and a second Typography duplicate — all carry `[SUPERSEDED]` and can be archived in the Linear UI (the API can't archive).

### Local markdown mirror (for offline editing)

`Documents/Creia Assets/Brand Brain/` — `00_brand_brain_index.md`, `01_brand_bible_creative.md`, `02_web_design_system.md`, `03_ops_doc_parked.md`. **These are a snapshot, NOT linked to Linear.** Edits here do not sync back; someone must push them into the Linear docs.

### Assets (`Documents/Creia Assets/`)

- `creia_assets_index.md` — master index (fonts + usage rule, logos, colours, dimensions, casting, product pointer)
- `Fonts/` — Area Extended ×4 (Thin/Regular/Bold/ExtraBold), Hubot Sans ×2 (Light/ExtraLight)
- `Logo/` — `creia_logo_wordmark_{black,white}.svg` + `_{black,white}_transparent.png`
- `Safe zones + Aspect ratios/` — `creia_safezone_post_4x5.png`, `creia_safezone_story_9x16.png`
- `Product/` — 7 master renders + `creia_assets_manifest.md`
- `Casting/` — `creia_casting_faith-charnock_digitals.pdf` + `_01`–`_05.jpg`

### Other source material

- `Downloads/Creia Emails/` — the email PNG set, two order-confirmation `.liquid` templates (links fixed to creia.com), the abandoned-checkout + upsell `.md` flow docs, and **`creia_brand_brain_todos.md`** (the live to-do list)
- `Documents/Creia/Creia (Temp)/Infographs/` — 5 educational carousels (Coffee vs Creatine, Creatine Bulk, Beyond the Gym, Dosage Dilemma, Weight/Water)
- `Downloads/Creia Product Asset Blanks/` — original product photos + the `OUT_*` white-bg renders + renamed masters (working files)

---

## 3. Current state — what's done

- **Bible restructured** into 7 parts (I Brand, II Copy System, III Creative Design System, IV Product, V Facts Bank, VI Funnel, VII Asset Register).
- **Copy system loosened**: rules are defaults not gates; contractions/abbreviations in; generate-first with `[ASA CHECK]` tagging for unverified claims; the **wink register** (Nothing-inspired) added; email titles canonised incl. the `Otw!` transactional-exclamation carve-out.
- **Product truth confirmed** from the label (composition, dimensions, pricing, trial architecture).
- **Facts & Statistics Bank** built (Verified / [ASA CHECK] / Retired), incl. GC-blessed cognition/body claims and the infographic claims.
- **Web Design System** consolidated (absorbed old Design System + Typography refs); domain corrected to creia.com.
- **Assets produced & logged**: product renders (7), logos (SVG+PNG), fonts + usage rule, safe-zone templates, dimensions, colour reference, founder casting reference.
- **Naming schemes** established (see §5).

---

## 4. What's left (full list in `Downloads/Creia Emails/creia_brand_brain_todos.md`)

Priority order:

1. **Design-system cohesion pass** (the big one). The visual system is fragmented — dark/flash editorial + clean studio product-hero + educational infographic + pop set + infographic accent grounds read as separate registers. Zuber's steer: make **"pop of colour" a defined move *within* the dark style**, not a standalone register; unify into one hierarchy. As part of this, **refresh the reference set** (see open questions) and fold in the font-usage rule + safe-zone both-variants rule.
2. **Replace weak canon headlines** in Bible Part II §10 — Zuber's words: "canon headlines are shit." Source stronger exemplars.
3. **On-brand vs off-brand visual reference board** — the brain has bad-*copy* examples but zero negative *visual* examples.
4. **Library depth**: tagged photography library; prop/scene reference frames; more casting references for range (founder is the only one so far).
5. **Content**: verify/expand product composition (already in Part IV §19); expand "90 Days With Creia" full arc into Part V §29; document 8–12 personas; add 2–3 worked end-to-end example creatives; produce a machine-readable export (JSON/table of facts, strategies, product, props).
6. **Claims/legal**: counsel pass on §27 infographic claims; define the auto-publish gate for `[ASA CHECK]`; fix source-asset errata (the "enzyme" claim + "mental food" typo in the Beyond-the-Gym carousel; the site's "two kilos" → 1kg).
7. **Ops**: rework the parked OPS_DOC to match the revised Bible; resolve the two live CTA/type systems.
8. **Housekeeping**: archive the `[SUPERSEDED]` stubs in Linear; transparent-background box renders; logo lockup/misuse sheet; moodboard mirrored into the brain.

---

## 5. Naming schemes (keep these consistent)

- **Product renders:** `creia_<sku>_<view>_<bg>_<res>.png` — sku ∈ {trial, 30, 90, sachet}; bg ∈ {white, transparent}; e.g. `creia_30_box-open-front_white_2k.png`.
- **Logos:** `creia_logo_wordmark_<colour>[_transparent].<svg|png>`.
- **Safe zones:** `creia_safezone_<placement>_<ratio>.png`.
- **Casting:** `creia_casting_<name>_<nn|digitals>.<ext>`.

Convention throughout: lowercase, `_` between fields, `-` within a field.

---

## 6. Key decisions already made (do NOT relitigate without reason)

- **1kg of raw beef = one sachet** is canon (the old "2kg" is retired; the site still says two kilos and needs fixing). High-performing fact.
- **Full pricing** 30-day £49.99 one-time / £39.99 sub; 3-month £129.99 / £79.99. **Email prices are discounted offers, never treat as list.**
- **Trial**: 5 days, 5 sachets, free, no auto-subscribe, £3.95 postage (kept out of email copy).
- **Composition** (per 8g sachet): 5g 200-mesh ultra-micronised creatine mono, 350mg pink Himalayan salt, 60mg magnesium, natural lemon flavouring (Dirty Lime), citric acid, stevia. "400mg electrolytes" = salt + magnesium, approved.
- **Dimensions**: box 12.5 × 11 × 8.5 cm; sachet 120 × 35 × 10 mm.
- **Font usage rule**: Area Extended default for everything, primarily Bold; body/running text is Area Extended in a lower weight (not Hubot Sans); Hubot Sans only for small text/subtext; **font sizing left to the tool/designer — just legible**, no fixed px.
- **No strict creative palette.** Fixed colours are product/logo only (logo navy `#0D191F`/white, sachet silver, box white + black text). Imagery follows brand vibe.
- **Every creative ships in both variants — post (4:5) and story (9:16).**
- **Casting face = Faith Charnock, the founder** — on-spec (173cm), in age range, rights cleared. Ties to the "crowd is the brand" seeding strategy.
- **Testimonials parked by decision** — social-proof slot stays empty until real reviews exist (no fabrication).
- **Nothing's actual lines are fair game** when they fit the sachet better ("Your new party pill" — tag [ASA CHECK], drug-adjacent on an ingestible).

---

## 7. Open questions for Zuber (needs his input before acting)

1. **Reference-set refresh:** he said "add **David** (confirm which David — likely the protein brand), keep **Nothing**, remove **[?]**" — he hasn't said which reference to remove. Also add **Exist (lip balm)** as a new visual reference.
2. **Font licence** for AI/render use — still to confirm.
3. **Black logo colour:** the "black" vector is filled navy `#0D191F` (reads black, matches sachet navy). Confirm intended, or he supplies a true-black `#171717` variant.
4. **Transparent box renders** — only the single sachet has alpha; does he want transparent box versions?
5. **Sync model:** edit the local markdown then have an agent push to Linear, OR edit Linear directly and treat the markdown as a read-only mirror. Pick one to avoid drift.

---

## 8. Environment & tooling gotchas (important)

- **Linear editing = full-document replace.** The `save_document` tool overwrites the entire doc; there is no partial patch. Always `get_document` first, edit the full content, save it back. The Bible is very long — be careful not to drop sections.
- **The local markdown is not linked to Linear.** Decide the sync direction (open question #5) or the two will diverge.
- **Subfolders created inside the sandbox can vanish on a mount refresh.** A `graded/` folder created mid-session was wiped once; regenerate into user-visible folders and write final files directly there. User-created folders persist fine.
- **creia.com is client-rendered.** Plain web-fetch returns an empty shell; use the Chrome MCP (`navigate` + `get_page_text`) to read it. The Chrome extension was intermittently disconnected — retry, or ask the user to check it.
- **Image generation pipeline (Higgsfield / Nano Banana Pro):** flow is `media_upload` → `curl -X PUT` the bytes to the presigned URL → `media_confirm` → `generate_image` (model `nano_banana_pro`, `resolution: "2k"`) → `job_display` to poll → download the `rawUrl`. **Nano Banana regenerates rather than masks** — it can hallucinate label text or recolour (it turned "DIRTY LIME" green once, and garbled side-panel text). **Always visually verify** the wordmark + fine print against the original before accepting. Reflective-tile source photos are the hardest to cut out cleanly.
- **Colour-neutralising recipe** (used to kill a warm tint on renders): desaturate to luminance, then normalise the corner-background to ~254 for a clean neutral white. Product is monochrome so full desaturation is lossless for brand colour.
- **Sharing files with the user:** use `present_files` after creating them.
- **PDFs:** the host Read tool couldn't render PDF pages (no poppler); extract images with `pypdf` in the sandbox and view those.

---

## 9. Recommended first moves for Fable 5

1. Read: this doc → `01_brand_bible_creative.md` → `creia_brand_brain_todos.md`.
2. Confirm the **sync model** (open question #5) with Zuber before editing anything, so brain and mirror don't drift.
3. Get answers to open questions #1–4 (reference removal, David, font licence, logo colour, transparent boxes) — these unblock the design-system pass.
4. Do the **design-system cohesion pass** — the highest-leverage remaining task — folding in the font rule, safe-zone rule, pop-colour-within-dark decision, and the reference refresh.
5. Then work down the to-do priorities: better canon headlines, the on/off-brand visual board, library depth, then legal/ops.

Everything above is current as of the last session. When in doubt, the Bible (Linear) is the source of truth; if an asset disagrees with Part IV, the asset is wrong.
