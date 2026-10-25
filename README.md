# link-in-bio

A single-page "link in bio" for the two cafés:

- **Café Square One** — https://cafesquareone.com
- **Eggcellent Cafe** — https://eggcellent.cafe

One self-contained `index.html`: no build step, no dependencies, no tracking.
Mobile-first, works offline-ish (everything is inline), light + dark mode,
respects `prefers-reduced-motion`.

## Run locally

Open `index.html` in a browser, or:

```sh
python3 -m http.server 8080
# http://localhost:8080
```

## Edit the links

Everything lives in `index.html`. Each button is one `<a class="link">` block —
change the `href`, the `.name`, and the `.host` text. To add a third café,
copy a block and give it its own accent by adding a modifier class
(see `.link--egg`) with a new `--accent` value.

## Deploy

### Netlify (recommended)

1. Netlify → **Add new site → Import an existing project → GitHub**
2. Pick this repo. `netlify.toml` already sets publish dir `.` and no build command.
3. Deploy. Every push to `main` redeploys.

Custom domain: Site configuration → Domain management → Add a domain.

### GitHub Pages (alternative)

Settings → Pages → Source: **Deploy from a branch** → `main` / `/ (root)`.
Served at `https://<user>.github.io/link-in-bio/`.
