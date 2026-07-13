# Creia Assets — Index

Top-level index for the `Documents/Creia Assets` folder. Naming scheme throughout: `creia_<type>_<detail>_<...>.<ext>`, lowercase, `_` between fields, `-` within a field.

---

## Fonts (`/Fonts`)

**Area Extended** — the primary brand typeface. Use it for almost everything.
**Hubot Sans** — secondary, small-text only.

### Usage rule (canon)

- **Area Extended is the default for all text**, primarily **Bold** (hero, headings, subheadings).
- **Body / running text** is still **Area Extended**, just a **lower weight** (Regular / Thin) — not Hubot Sans.
- **Hubot Sans is only for small text or subtext** (captions, fine print, legal, tiny UI labels).
- **Font sizing is not fixed.** Don't prescribe exact px sizes for creatives — every piece of text must simply be **legible**, and the tool/designer building the creative sets the size. (For reference proportions, see the email visual templates.)

### Files

| File | Weight | Use |
| -- | -- | -- |
| `Area_Extended_ExtraBold.otf` | ExtraBold | Heaviest hero display |
| `Area_Extended_Bold.otf` | Bold | Default — headings, subheadings, most text |
| `Area_Extended_Regular.otf` | Regular | Body / running text |
| `Area_Extended_Thin.otf` | Thin | Light display / large-format subtext |
| `HubotSans-Light.ttf` | Light | Small text / subtext only |
| `HubotSans-ExtraLight.ttf` | ExtraLight | Small text / subtext only |

---

## Colours

**There is no strict creative palette.** Imagery follows the brand vibe (Bible Part III), not a fixed swatch set. The only fixed colours are the product and logo:

| Element | Colour | Notes |
| -- | -- | -- |
| Logo wordmark | navy `#0D191F` (reads black) or white `#FFFFFF` | Use the supplied logo files; don't recolour |
| Sachet | silver / chrome metallic | As in the product asset files; not a flat hex |
| Box | pure white `#FFFFFF` ground, black `#000000` text | As in the product asset files |

Creative imagery (ads, email imagery, social) has **no strict palette** beyond following the brand vibe. Emails are built in Canva (primarily white) via the connector — no palette spec needed here.

---

## Dimensions

| Item | Size |
| -- | -- |
| Box | 12.5 cm H × 11 cm W × 8.5 cm D (125 × 110 × 85 mm) |
| Sachet | 120 mm × 35 mm × 10 mm (L × W × D, stick) |

---

## Logo (`/Logo`)

The "creia" wordmark (reversed-R script). Vector (SVG) + transparent PNG, black and white.

| File | Format | Colour | Notes |
| -- | -- | -- | -- |
| `creia_logo_wordmark_black.svg` | SVG (vector) | black | Fill is navy `#0D191F` (the brand logo navy), reads as black. Scale freely |
| `creia_logo_wordmark_black_transparent.png` | PNG, alpha | black | 6405×1917, transparent bg |
| `creia_logo_wordmark_white.svg` | SVG (vector) | white `#FFFFFF` | For dark grounds |
| `creia_logo_wordmark_white_transparent.png` | PNG, alpha | white | 6405×1917, transparent bg |

*Flag to confirm: the "black" logo vector is filled navy `#0D191F`, not true black `#171717`. It reads black and matches the on-sachet navy. Confirm this is intended as the master wordmark colour, or supply a true-black variant.*

---

## Safe zones + aspect ratios (`/Safe zones + Aspect ratios`)

Text-safe-zone templates. Grey margin = full bleed / unsafe area; white card = keep text inside it. **Every creative must be produced in both variants — post and story.**

| File | Placement | Ratio |
| -- | -- | -- |
| `creia_safezone_post_4x5.png` | Feed / post ads | 4:5 (1080×1350) |
| `creia_safezone_story_9x16.png` | Story / reel ads | 9:16 (1080×1920) |

---

## Casting (`/Casting`)

Approved on-spec model references the pipeline may generate toward (casting spec: Bible Part III §17). Scheme: `creia_casting_<name>_<nn|digitals>.<ext>`.

| Model | Files | Fit |
| -- | -- | -- |
| Faith Charnock — **founder** (Fabbrica Milano) | `creia_casting_faith-charnock_digitals.pdf` + `_01`–`_05.jpg` | Strong. 173cm, lean/long/narrow, editorial face, bare-faced, natural dark hair, not smiling. In age range, rights cleared. **This is the founder** — a real face for the brand, not just a casting proxy |

---

## Product (`/Product`)

Master product cutouts. See `Product/creia_assets_manifest.md` for the full list and scheme. Covers single sachet (transparent), trial 5-sachet, 30-day box (4 views), 90-day 3-box.
