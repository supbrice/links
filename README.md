# Brice Links (`supbrice/links`)

Static Linktree-style page for [@supbrice](https://x.com/supbrice). Light/dark theme, one HTML file, no build step.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The full page (profile, socials, links) |
| `web-pfp.png` | Avatar image |
| `README.md` | This file |

## Edit content

Open `index.html` and change:

1. **Name / bio** — the `<h1>` and `.bio` paragraph near the top of `<main>`.
2. **Social icons** — the `<nav aria-label="Social links">` block (each `<a>` is one icon, including email).
3. **Main links** — edit the JavaScript `links` array near the bottom:

```js
const links = [
  { title: 'My New Link', url: 'https://example.com', icon: 'youtube' },
  // …
];
```

Add, remove, or reorder objects — they render automatically. Each item takes an `icon` key (`youtube`, `discord`, `apple-music`, `buymeacoffee`, `playstation`, `robinhood`, `church`, `briefcase`). Icons are inline monochrome SVGs (no extra CDN).

4. **Avatar** — replace `web-pfp.png` and keep that filename. The page uses it as the favicon and `og:image`.

## Preview locally

Open `index.html` in a browser, or from this folder:

```bash
# Python
python3 -m http.server 8080

# or Node
npx serve .
```

Then visit `http://localhost:8080`.

## Deploy to GitHub Pages

1. Create a new GitHub repo named **`links`** under the **`supbrice`** account (or rename/move this folder into that repo).
2. Push the contents of this folder to the `main` branch:

```bash
cd /path/to/supbrice-links
git init
git add .
git commit -m "Initial links page"
git branch -M main
git remote add origin https://github.com/supbrice/links.git
git push -u origin main
```

3. On GitHub: **Settings → Pages**
   - Source: **Deploy from a branch**
   - Branch: **`main`** / folder **`/` (root)**
   - Save

4. After a minute or two, the site will be live at:

**https://supbrice.github.io/links/**

> If the repo is named `links` under `supbrice`, GitHub Pages serves it at that URL. Asset paths in `index.html` are relative (`./web-pfp.png`), so they work on Pages without changes.

## Theme notes

- Default: light. The top-right button toggles `html.light` / `html.dark` and stores the choice in `localStorage`.
- Layout, type, and the animated background live in the `<style>` block (Inter). No Tailwind and no build step, so GitHub Pages can serve `index.html` from the repo root.
- Social icons and link buttons keep the existing platform logos. Brand color is set with `--brand` on each `[data-brand]` rule.
- `prefers-reduced-motion: reduce` stops the background blobs.
