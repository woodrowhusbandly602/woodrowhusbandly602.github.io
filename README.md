# ninjaapps.net

Static site for **NinjaApps** — iOS games & utilities. Design: "Paper Dojo"
(warm paper, ink, vermillion accent, hairline grids). Hosted on GitHub Pages
at [ninjaapps.net](https://ninjaapps.net). No build step: plain HTML + one
shared stylesheet.

## Structure

```
index.html                  landing page (cards for every app)
style.css                   all styles + design tokens (light/dark)
assets/theme.js             theme-toggle wiring
privacy/index.html          privacy hub (links each app's policy)
apps/<slug>/index.html      one page per app
apps/<slug>/privacy.html    one privacy policy per app
apps/_template/             copy this to add a new app
404.html                    not-found page
CNAME                       custom domain for GitHub Pages
```

## Adding a new app

1. Copy `apps/_template/` to `apps/<slug>/` and replace every `{{TOKEN}}`
   in both files (`{{EFFECTIVE_DATE}}` is `YYYY-MM-DD`). Remove the
   `noindex` meta line at the top of each copied file.
2. Add a card on `index.html` in the right group (`#games` 3-col grid or
   `#utilities` 2-col horizontal cards) and bump the group's `group-count`.
3. Add a row on `privacy/index.html` and bump its count.
4. Add both URLs to `sitemap.xml`.

## Placeholder inventory (TODO)

- All 5 apps are **sample content** — swap names, copy, and links for real apps.
- Striped boxes (`.ph`) are asset slots: hero art, app icons (1024×1024),
  screenshots (1290×2796).
- App Store buttons point at `#` — search `TODO` across the repo.
- No contact email yet — privacy pages point at the App Store page instead.

## Local preview

```sh
python3 -m http.server 8000   # then open http://localhost:8000
```

Pages also open fine directly from disk (`file://`) except `404.html`,
which uses absolute paths (it can be served from any URL).

## Theme

Light/dark toggle persists in `localStorage` (`ninjaapps-theme`); first visit
follows `prefers-color-scheme`. A blocking snippet in each `<head>` sets
`data-theme` before paint to avoid flashing.
