# link-in-bio

A single-page "link in bio" for the two cafes:

- **Cafe Square One** — https://cafesquareone.com
- **Eggcellent Cafe** — https://eggcellent.cafe

One self-contained `index.html` (inline CSS, no build step, no dependencies, no
tracking) plus two logo PNGs. Mobile-first, light + dark mode, respects
`prefers-reduced-motion`.

## Branding

Both logos are the **official marks**, pulled from the live sites and only
trimmed/resized — no recoloring:

| File | Source | Notes |
| --- | --- | --- |
| `images/cafe-square-one-logo.png` | `cafesquareone.com/images/logo.png` | Navy circular badge, 256×256 |
| `images/eggcellent-logo.png` | `eggcellent.cafe/images/eggcellent-logo.png` | Yellow wordmark, 640×134 |

Palettes are sampled from each site's own CSS: Cafe Square One navy `#1f4073` /
gold `#fad02c`; Eggcellent yellow `#ffd70c`.

Each card has a **brand plate** behind its logo, and the plate colour is not
decorative — it is what keeps the mark legible:

- Cafe Square One's badge is dark navy, so its plate is **white** in both schemes.
- Eggcellent's wordmark is 100% flat yellow with no outline or dark detail, so its
  plate is **near-black** (`#15120c`) in both schemes. On a white plate that
  wordmark is effectively invisible (~1.3:1 contrast).

Chevrons and focus rings use `--cso-accent` / `--egg-accent`, which flip per colour
scheme so the accent stays readable against the current card background.

**If you swap in a different logo, re-check its plate.** A light-on-transparent
logo needs a dark plate; a dark-on-transparent logo needs a light one.

## Run locally

```sh
python3 -m http.server 8080
# http://localhost:8080
```

(Open `index.html` directly via `file://` and the logos still load — paths are relative.)

## Edit the links

Everything lives in `index.html`. Each button is one `<a class="card">` block:
change the `href`, the `.name` line (currently each cafe's own tagline), and the
`.host` line. To add a third cafe, copy a block, give it a modifier class
(see `.card--egg`) defining `--accent` and a `.plate` background, and drop its
logo in `images/`.

## Deploy

### Netlify (recommended)

1. Netlify → **Add new site → Import an existing project → GitHub**
2. Pick this repo. `netlify.toml` already sets publish dir `.` and no build command.
3. Deploy. Every push to `main` redeploys.

Custom domain: Site configuration → Domain management → Add a domain.

### GitHub Pages (alternative)

Settings → Pages → Source: **Deploy from a branch** → `main` / `/ (root)`.
Served at `https://<user>.github.io/link-in-bio/`.
