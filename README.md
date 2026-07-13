# Creia Brand Brain

Single source of truth for the Creia brand: the brand docs plus every anchored asset. If an asset or a piece of copy disagrees with this repo, the asset is wrong.

**This repo replaced Linear as the brain's home (July 2026).** The Linear docs are retired mirrors and carry a [MOVED] banner. Don't edit them.

## Start here

1. `Brand Brain/00_brand_brain_index.md` — routing, canonical facts, gaps, changelog
2. `Brand Brain/01_brand_bible_creative.md` — the main doc: brand, copy system, design system, product, facts bank, adapting & channels, asset register
3. `Brand Brain/02_web_design_system.md` — creia.com implementation only
4. `Brand Brain/03_ops_doc_parked.md` — parked ad-system manual; don't generate from it
5. `creia_assets_index.md` — asset file index

## Assets

| Folder | Contents |
| -- | -- |
| `Product/` | Master product render cutouts + manifest (`creia_<sku>_<view>_<bg>_<res>.png`) |
| `Logo/` | Wordmark SVG + transparent PNGs, black (navy #0D191F, intentional) + white |
| `Fonts/` | Area Extended ×4, Hubot Sans ×2 (licence for AI/render use confirmed) |
| `Safe zones + Aspect ratios/` | Post 4:5 + story 9:16 text-safe templates |
| `Casting/` | Faith Charnock (founder) casting reference, rights cleared |
| `Props/` | Prop/scene reference images (to be filled) |
| `Visual ad References/`, `Visual email references/`, `Visual Anti-references/` | On/off-brand visual boards (to be filled) |

## Rules for agents

- The bible's job: adapt winning reference creatives to Creia and generate Creia ads + emails. Not editorial work.
- Claims: anything not marked **Verified** in the bible's Part V gets an inline **[ASA CHECK]** tag.
- Every creative ships in both 4:5 and 9:16.
- Edit via commits with clear messages; the git history is the changelog.
