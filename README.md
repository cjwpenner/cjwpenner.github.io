# cjwpenner.github.io

Personal site for Chris Penner, served by GitHub Pages at
<https://cjwpenner.github.io>.

Static HTML and one hand-written stylesheet — no build step, no framework, and
no external requests (no CDN, web fonts, analytics or trackers).

| File | Purpose |
|---|---|
| `index.html` | Profile page |
| `privacy.html` | Privacy policy for the NoteTaker Android app, linked from the Google Play listing |
| `assets/style.css` | Shared styles, light and dark |

Design notes live in [`docs/superpowers/specs/`](docs/superpowers/specs/).

To preview locally:

```
python -m http.server 8000
```

then open <http://localhost:8000>.
