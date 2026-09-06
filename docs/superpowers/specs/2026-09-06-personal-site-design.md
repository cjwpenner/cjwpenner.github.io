# cjwpenner.github.io — personal / developer profile site

**Date:** 2026-09-06
**Status:** Approved

## Purpose

Replace the untouched Start Bootstrap "Clean Blog" demo content with a brief
personal site that can be linked from a Google Play developer profile, ahead of
publishing the NoteTaker Android app.

The site has one job: give a visitor arriving from the Play Store a quick,
credible sense of who wrote the app. It is not a blog and should not pretend to
be one.

## Decisions

| Decision | Choice | Reasoning |
|---|---|---|
| Template | Clean rebuild, single page | The demo site carried ~1MB of jQuery, Bootstrap 4, FontAwesome and stock photography to render four fake blog posts. None of it serves the purpose. |
| Privacy policy | Include `privacy.html` | Play Console requires a privacy policy URL for any app touching the microphone or user data. NoteTaker does both. |
| Neurodiversity framing | Light touch, one clause | Stated as a design interest, not a personal disclosure. The page is permanent and searchable. |
| Profession | Solution architect | Architecture in the IT sense, not the built environment. Application code is the hobby. |
| Name | Chris Penner | Matches the professional framing and the Play Store developer profile. |
| App status | Coming soon | Not yet listed; placeholder for the store link. |

## Structure

```
index.html          profile page
privacy.html        NoteTaker privacy policy
assets/style.css    hand-written, shared by both pages
README.md           retained
```

Removed: `about.html`, `contact.html`, `post.html`, `assets/bootstrap/`,
`assets/js/`, `assets/fonts/`, `assets/img/`.

GitHub Pages user sites serve `index.html` from the repository root with no
build step, so no Jekyll configuration is required.

## Constraints

- No external requests. No CDN, no web fonts, no analytics. A profile page
  linked from a store listing should not leak visitors to third parties, and it
  keeps the privacy policy honest about the site itself.
- Responsive and theme-aware (`prefers-color-scheme`).
- Semantic HTML; the page must be legible with CSS disabled.

## Content

Featured work: NoteTaker (primary), md-docx-converter, LightMD.

Contact: financetoolcp@gmail.com — the address used for the Play Store listing,
kept distinct from the personal GitHub address.

## Privacy policy scope

Drawn from the NoteTaker source rather than a template, so the claims are
verifiable:

- Audio is captured on device (`RECORD_AUDIO`, foreground microphone service)
  and written to a user-chosen folder via SAF (`SafMeetingStore`).
- Audio is chunked and sent over HTTPS to OpenRouter for transcription and
  summarising, authenticated with the *user's own* API key
  (`OpenRouterClient`). OpenRouter's own terms govern that leg.
- The API key is encrypted at rest using the Android Keystore
  (`KeystoreCipher`).
- Notes and transcript are emailed via the *user's own* SMTP account, sent
  directly from the device (`AndroidSmtpSender`).
- There is no developer-operated server, no account, and no analytics. The
  developer receives none of the user's data.

The last point is the substantive one and is only true because the app
orchestrates everything on the handset — a deliberate architectural choice
recorded in `PRD.md` ("I don't want to run this through a server").

## Out of scope

- Blog or writing section.
- Play Store badge artwork (added once the listing is live).
- Custom domain.
