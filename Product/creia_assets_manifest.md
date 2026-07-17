# Creia Product Assets — Master Set

Clean, tint-neutral product cutouts. Use as reference/base for scaling creatives.

## Physical dimensions

- **Box:** 12.5 cm H × 11 cm W × 8.5 cm D (125 × 110 × 85 mm)
- **Sachet:** 120 mm × 35 mm × 10 mm (L × W × D, stick)

Use for correct proportions/scale when compositing product into scenes.

## Naming scheme

`creia_<sku>_<view>_<bg>_<res>.png`

- **sku** — `trial` (5-day, 5 sachets) · `30` (30-day single box) · `90` (90-day 3-box pack) · `sachet` (single unit)
- **view** — what's in frame / angle
- **bg** — `white` (solid neutral white) or `transparent` (alpha)
- **res** — `2k`, or the identifying pixel dimension for non-2k assets (`1080` for the single-sachet master)

Lowercase, `_` between fields, `-` within a field. Sorts by SKU.

## The masters

| File | SKU | Background | Use |
| -- | -- | -- | -- |
| `creia_sachet_x1_transparent_1080.png` | sachet | transparent | Single sachet, alpha cutout — drop into any composite |
| `creia_trial_sachets-x5_white_2k.png` | trial | white | 5 sachets in a row — 5-day trial hero |
| `creia_30_box-open-front_white_2k.png` | 30-day | white | Open box, straight-on — primary box hero |
| `creia_30_box-closed-front_white_2k.png` | 30-day | white | Closed box, front — flat pack reference |
| `creia_30_box-closed-angle_white_2k.png` | 30-day | white | Closed box, 3/4 |
| `creia_30_box-with-sachets_white_2k.png` | 30-day | white | Box + 2 loose sachets — relationship shot |
| `creia_90_boxes-x3_white_2k.png` | 90-day | white | Three boxes in a row — 90-day pack hero (2048×1112) |

## Notes

- White-background assets are on solid neutral white (not transparent). Run a background-removal pass if you need alpha for those.
- Exact existing masters may retain the printed `getcreia.com` domain. All new copy and any reconstructed packaging must use `creia.com`.
- `box-with-sachets` and `boxes-x3` came from reflective-tile source photos; usable, candidates for an eventual seamless reshoot if pixel-perfect masters are needed.
