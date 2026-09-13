# Quasiinvestor: quasiinvestor.com

Quasiinvestor is a pre-launch editorial site for occasional essays on markets,
technology, and the machinery underneath, often through a Southeast Asian lens.
Nothing on the site is investment advice.

## Stack

Plain static HTML and CSS. There is no framework, JavaScript, or build step. The
directory deploys to Cloudflare Pages as-is.

## Site structure

- `index.html`: one-page home with anchored Hero, Essays, and About sections.
- `about.html`: a longer About page retained for existing inbound links.
- `style.css`: shared design system and responsive styles.
- `assets/quasi-logo.png`: transparent Q mark used for the lockup and favicon.

## Design system

The page is an understated editorial layout built from a warm paper background,
navy type, cyan details, fine rules, and generous whitespace. Do not add cards,
gradients, large shadows, or rounded interface panels.

### Colors

| Token | Value |
|---|---|
| Paper | `#f6f4ef` |
| Input fill | `#fffdf9` |
| Ink | `#0b1b3a` |
| Secondary ink | `#123a6b` |
| Body muted | `#3d4a63` |
| Label muted | `#5c6a86` |
| Meta muted | `#8b8879` |
| Accent | `#00a8e8` |
| Link hover | `#0090c8` |
| Hairline | `rgba(11, 27, 58, 0.1)` |

### Typography and layout

- Display/body: Newsreader (300/400/500 and italic 400), then Georgia.
- Labels/UI: IBM Plex Mono (400/500), then monospace.
- Content width: 900px; desktop gutters: 40px; mobile gutters: 22px.
- Header/footer stay full-width. Sections are divided by 1px hairlines.
- Preserve the existing responsive breakpoints at 820px and 640px.
- Preserve accessible focus rings and reduced-motion behavior.

## Publishing an essay

Replace the Forthcoming row in `index.html` with an entry containing a date, linked
title, and dek. Essay URLs should use `/essays/<slug>`, and entries should be ordered
newest first. Individual essay pages should reuse the same typography and keep body
copy near a 680px measure.

## Editorial style

- Use plain punctuation and direct sentences.
- Do not use em dashes.
- Avoid stock contrast constructions such as "not X but Y" and "not only X but Y."
- Avoid inflated claims and unnecessary self-characterization.
- Keep About and disclaimer copy literal and concise.
