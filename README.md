# Brice Links (`supbrice/links`)

Static Linktree-style page for [@supbrice](https://x.com/supbrice). Dark/light theme, Tailwind CDN, no build step.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The full page (profile, socials, links) |
| `web-pfp.png` | Avatar image |
| `README.md` | This file |

## Edit content

Open `index.html` and change:

1. **Name / bio / email** — in the `<header>` section near the top of `<main>`.
2. **Social icons** — the `<nav aria-label="Social links">` block (each `<a>` is one icon).
3. **Main links** — edit the JavaScript `links` array near the bottom:

```js
const links = [
  { title: 'My New Link', url: 'https://example.com' },
  // …
];
```

Add, remove, or reorder objects — they render automatically.

4. **Avatar** — replace `web-pfp.png` (keep the same filename, or update the `<img src>`).

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

- Default: dark (`html` has class `dark`).
- Light mode: toggled via the button (top-right); adds `html.light` and persists in `localStorage`.
- Colors / fonts live in the Tailwind CDN config and a small `<style>` block — match the Brice portfolio (abyss / graphite / steel / mist / accent, Space Grotesk + IBM Plex Mono).
