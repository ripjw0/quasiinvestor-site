# Quasiinvestor — quasiinvestor.com

Editorial blog. Positioning: "independent views of the world" — don't frame the site as being about tech/investing or as SEA-only in copy, titles, or metadata, even though articles often cover fintech, blockchain, agritech, and gaming with a Southeast Asia lean.

## Stack

Plain static HTML + CSS. **No frameworks, no JavaScript, no build step.** The folder deploys to Cloudflare Pages as-is. Keep it that way unless explicitly asked otherwise.

## Design system

Aesthetic: clean editorial (Bloomberg / Stratechery). Flat — **no gradients, no shadows, no boxed cards, no rounded panels**. Structure comes from thin 1px hairline dividers and whitespace only.

### Colours

| Token | Value | Use |
|---|---|---|
| Ink | `#1a1a1a` | Body text, headlines, nav, wordmark "Quasi" |
| Grey | `#666` | Secondary text: standfirsts, metadata |
| Teal (accent) | `#0F6E56` | See accent rule below |
| Hairline | `#e0e0e0` | All 1px dividers/borders |
| Footer bg | `#f5f5f4` | Footer strip only |
| Background | `#fff` | Page |

**Teal-only-accent rule (strict):** `#0F6E56` is the sole accent colour and may appear ONLY in three places:
1. Uppercase category labels
2. The "investor" half of the wordmark
3. The "Subscribe →" link in the footer

Nothing else gets colour. No hover colours in teal, no teal buttons, no second accent. When in doubt, use ink or grey.

### Typography

- **Serif** — headlines and the wordmark: `"Source Serif 4"` (Google Fonts), fallback Georgia. Loaded via `<link>` in `<head>` with weights 400/600/700.
- **Sans** — nav, category labels, metadata, standfirst, footer: system font stack (`-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, ...`).
- Wordmark: 32px serif bold with `letter-spacing: 0.02em` (slightly open, per owner preference — don't tighten it).
- Category labels: 12px, uppercase, `letter-spacing: 0.12em`, weight 600, teal.
- Featured headline ~34px serif (27px on mobile); grid card headlines ~18px serif.
- Metadata (read time · date): 13px grey, middot separator (`&middot;`).

### Layout & spacing

- Page content max-width **1000px**, centred, 24px horizontal padding.
- Featured article text block capped at **560px**.
- Vertical rhythm is generous: ~56px above the featured article, ~40–64px around the article grid.
- Article grid: 3 equal columns separated by 1px hairline **left borders** (not boxes), 32px column gutters. Collapses to a single column under 720px, with hairline **bottom borders** between stacked items instead.
- Footer: full-bleed light-grey strip; inner content aligns to the same 1000px column (done with `calc(max((100% - 1000px) / 2, 0px) + 24px)` padding).

### Page structure (top to bottom)

1. **Masthead** — wordmark left ("Quasi" ink + "investor" teal), nav right (About only — no article-topic links in the masthead, per owner preference), 1px hairline bottom border.
2. **Featured article** — teal category label, large serif headline, grey standfirst, grey metadata line.
3. **Hairline divider**, then 3-column recent-articles grid (category label, serif headline, read time each).
4. **Footer strip** — teal "Subscribe →" right-aligned; no tagline.

### Article & About pages

- Shared masthead and footer, duplicated verbatim in every page (no templating/includes — plain HTML).
- Article header (`.article-header`): teal category label, serif title 34px (27px mobile), grey standfirst, grey byline/meta line ("By … · read time · date"). Header, divider, and body are all capped at **680px**.
- Body copy (`.prose`): serif 18px (17px mobile), line-height 1.7, ink. Subheads are serif 22px `h2`s. Blockquotes get a 1px hairline left border with grey italic text — never teal. In-body links are ink with a thin underline (accent rule applies: no teal in body copy).
- About page reuses the same header + prose structure, minus category label and byline.

## Publishing a new post

No CMS — the site migrated off WordPress (DreamHost) to static files on Cloudflare (Workers/Pages, project `quasiinvestor-site`, auto-deploys on push to `main` at github.com/ripjw0/quasiinvestor-site).

1. Create a new slug-named file (e.g. `grab-earnings-q3.html`) from the article skeleton below, reusing the exact masthead/footer markup from `index.html` and the same `<head>` (Google Fonts link + `style.css`).
2. Update `index.html`: put the newest post in the featured slot (`.featured` block: category, headline link, standfirst, meta) and/or add a `.card` in the `.recent` grid. While the site has no posts, `index.html` shows an `.empty-state` block ("Essays coming soon.") — replace it with the featured/grid structure when the first real post lands.
3. Commit and push to `main` — Cloudflare redeploys automatically.

Article page skeleton (inside `<main>`):

```html
<header class="article-header">
  <p class="category">CATEGORY</p>
  <h1 class="article-title">Headline</h1>
  <p class="standfirst">Standfirst.</p>
  <p class="meta">By Quasiinvestor &middot; N min read &middot; Month D, YYYY</p>
</header>

<hr class="divider article-divider">

<div class="prose">
  <p>…</p>
  <h2>Subhead</h2>
  <blockquote><p>…</p></blockquote>
</div>
```

## Files

- `index.html` — homepage (currently the no-posts empty state)
- `about.html` — about page
- Article pages — one slug-named `.html` file per post, built from the skeleton in "Publishing a new post" above
- `style.css` — all styling; CSS custom properties for the palette are defined in `:root`
