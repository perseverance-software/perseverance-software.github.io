# Perseverance Software website

Static GitHub Pages site for Forced Rep at <https://perseverancesoftware.app>.
GitHub Pages publishes `main` from the repository root. **Pushing `main` publishes
the site.** Local review and commits do not publish it.

## Routes

- `/` — app introduction, two selected native app details, free essentials, Premium and privacy summary
- `/privacy/` — privacy policy
- `/terms/` — terms of service
- `/support/` — contact details and common questions
- `/forcedrep/`, `/forcedrep/privacy/`, `/forcedrep/terms/`, `/forcedrep/support/` — legacy redirects; preserve paths and hash fragments
- `/404.html` — not-found page

## Presentation

Follow the public-website section of
[`docs/design/form-design-system.md`](../docs/design/form-design-system.md).
The site uses Obsidian colors, system typography, restrained mint actions and
native app captures. No external fonts, analytics, frameworks or JavaScript are
needed for the home, policy or support pages. The legacy redirects use a small
script to preserve fragments, with a meta-refresh fallback.

The home page deliberately shows **only two app details**, workout logging and
the training calendar. Explain other features in text. Do not add a screenshot
for every feature, an interactive recreation of the app, or standalone generated
athlete/paywall artwork. Both captures are native SwiftUI renders from existing
deterministic QA fixtures, labeled as iPhone sample data. They contain no personal
workout information. The website never serves the full capture masters.

Policies and support remain available in the shared navigation. When product
behavior changes, update the relevant policy, its date, and matching home/support
claims together. A visual restyle alone does not change the policy date.

## Current image provenance

Original native renders are preserved locally in
`gym/assets/website/2026-10-27/masters/` (untracked source media), with their
original test outputs retained at the source paths below. Crop only the relevant
component and surrounding padding; do not repaint, reconstruct, annotate or
change the app data. Coordinates are source pixels, `x y width height`.

| Export | Native source relative to `gym/` | Test in `forcedrep-ios/FormAppTests/FormAppTests.swift` | Crop | Output |
| --- | --- | --- | --- | --- |
| `assets/images/workout-logging.webp` | `forcedrep-ios/build/session-review/prev-en-default-393.png` | `testPreviousTableRendersAtNarrowWidthsInEveryLanguageAndLightTheme` | `72 192 1035 1044` | 1000 × 1009, lossless RGB WebP, no alpha |
| `assets/images/training-calendar.webp` | `forcedrep-ios/build/calendar-tiles-review/attachments/history-tiles-default-393.png` | `testTiledCalendarPaintsReferenceColorsAndRetainsSnapshots` | `60 0 1060 1356` | 960 × 1229, quality 92 RGB WebP, no alpha |

Source masters are 1179 × 2100 (logging) and 1179 × 1920 (calendar).
The logging fixture shows one completed 80 kg × 9 set and previous-session values;
the calendar fixture shows August 2026 with seven completed, three unfinished and
three missed days. These are real native components, not full-device screenshots.

| File | SHA-256 |
| --- | --- |
| Logging source / local `masters/workout-logging.png` | `bebee920d800238c5ca5a8b62d79ccc7aba9735dd1de3b447613a76770d4dd0d` |
| Calendar source / local `masters/training-calendar.png` | `c5c3ad089b29a0891e895e96da3316db5e58e1487cde056f61a88a696e1d98e7` |
| `assets/images/workout-logging.webp` | `60b589a1d29c5c27c1848c9efc55e438c5d70d7e07d4a5ebfc4fcd16f3ec4bb3` |
| `assets/images/training-calendar.webp` | `0313f32cacfc773eed7fa5540a64bc5b48aeb2c3145b45f0bde29434902dadba` |
| `assets/images/og-image.png` | `84947a7cc6a636a262fad5183af7dbcddac8945521e29e4432a299fc6b3e2f23` |

Export from the website directory with `cwebp`:

```sh
cwebp -quiet -lossless -crop 72 192 1035 1044 -resize 1000 0 ../assets/website/2026-10-27/masters/workout-logging.png -o assets/images/workout-logging.webp
cwebp -quiet -q 92 -m 6 -sharp_yuv -crop 60 0 1060 1356 -resize 960 0 ../assets/website/2026-10-27/masters/training-calendar.png -o assets/images/training-calendar.webp
```

`assets/social-card.html` is the code source for the 1200 × 630 RGB PNG social
preview (no alpha). Render it through the local server at exactly 1200 × 630 and
capture the viewport as `assets/images/og-image.png`. It contains the existing
Sculpted F and website typography, with no athlete or additional app screens.
The system font may differ on other hosts; update the hash after an intentional
re-export. Do not regenerate screenshots merely to match a different host font.

## Retired artwork provenance

The standalone artwork exports below were removed on 2026-10-27. App originals,
local source media and this source mapping are preserved. Their former website
exports remain recoverable in Git history. Launcher icons are still in use.

| Site file | Source | Source SHA-256 |
| --- | --- | --- |
| `assets/images/athlete-chalk-{640,1200}.webp`, `assets/images/og-image.jpg` | `forcedrep-android/app/src/main/res/drawable-nodpi/paywall_general.jpg` | `ff92f55b2f8d394a4503ac603d9a7a2ed8eb9734090c746717c821b101937348` |
| `assets/images/athlete-curl-{640,1200}.webp` | `…/drawable-nodpi/paywall_smart_progression.jpg` | `04cc776435b601ca7d22e614b121bc277d253198cd0be03140eda38b81a3a3dd` |
| `assets/images/volume-heatmap-{640,1200}.webp` | `…/drawable-nodpi/paywall_volume_matrix.jpg` | `f0806206a5d6135250be96dace994a8ee01a1c853974b9d22428fc7aea15899d` |
| `assets/images/barbell-plates-{640,1200}.webp` | `…/drawable-nodpi/paywall_warmup_plates.jpg` | `ef4b3d4ec413f9b604233d95d035005c011c9a1c16e8bba416c8b05a82291893` |
| `assets/images/athlete-tablet-{640,1200}.webp` | `…/drawable-nodpi/paywall_rep_lab.jpg` | `639c503df2de41895560349cccf9a9028a26bec46b079a93e8ac39a4f8ff6fb1` |
| `apple-touch-icon.png` (180 px), `favicon-32.png` | `forcedrep-android/store-listing/android/app-icon.png` | `5687eab35c5d8645d5387e9cd06308e12aa35f8c2040838acabd2ee11fe93fba` |
| `favicon.svg` | Sculpted F path and 0.88 scale from `forcedrep-android/app/src/main/res/drawable/ic_launcher_foreground.xml`, on the `#14171A` launcher background | — |

WebP files were made with `sips -s format png -Z <width>` followed by `cwebp -q 80 -m 6`. `og-image.jpg` is `sips -s format jpeg -s formatOptions 82 -Z 1200`. Icons are `sips -Z <size>` of the store icon.

## Preview locally

Use an HTTP server because page assets use root-relative paths. From `gym/`:

```sh
python3 -m http.server 8765 --bind 127.0.0.1 --directory perseverance-software.github.io
```

Open <http://127.0.0.1:8765/>. Check the home page and policy/support routes at
320 px, a typical phone width, tablet and desktop widths; test the support FAQ,
keyboard focus, anchor links and the legacy redirects with fragments. The Python
server does not serve `404.html` for missing paths; GitHub Pages does.

Visual-review captures are local-only under
`gym/assets/website/2026-10-27/review/`.
