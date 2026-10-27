# Perseverance Software website

Static GitHub Pages site for Forced Rep, served at <https://perseverancesoftware.app> (see `CNAME`). GitHub Pages publishes the `main` branch from the repository root, so pushing `main` publishes the site.

## Routes

- `/` — Forced Rep home page: what the app does, free features, Forced Rep Premium, and a privacy summary
- `/privacy/` — privacy policy
- `/terms/` — terms of service
- `/support/` — contact details and common questions
- `/forcedrep/`, `/forcedrep/privacy/`, `/forcedrep/terms/`, `/forcedrep/support/` — redirects to the routes above (hash fragments are kept). Older links, including store listings, may still point here, so keep these pages.
- `/404.html` — not-found page

## Keeping it current

The home page and support answers restate parts of the policies: the Health data, storage, backup, advertising and subscription claims. When an app change alters a policy, update the policy page, its "Last updated" date, and any matching sentence on `/` and `/support/` in the same commit.

The look follows the Obsidian tokens, system font and contained surfaces in [`docs/design/form-design-system.md`](../docs/design/form-design-system.md). Do not add rebuilt app UI or invented data; use real screenshots or the approved artwork below.

## Images

All artwork is exported from assets that already ship in the apps.

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

Pages use root-relative paths, so open them through a server rather than `file://`. From the `gym` directory:

```sh
python3 -m http.server 8765 --directory perseverance-software.github.io
```

Then open <http://localhost:8765>. The local server does not serve `404.html` for missing paths; GitHub Pages does.
