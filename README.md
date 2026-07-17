# Antler Design System

Antler's design tokens and text styles as **plain, standalone CSS** — zero
build dependencies. This repo is the published artifact of the design system;
the canonical source lives in the Antler website repo
(`src/styles/tokens/`) and is copied here by its release script on every
version tag. **Do not edit files here directly** — changes land in the website
repo and flow through a release.

## Usage

Link the two files, version-pinned, via jsDelivr:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/Antler-VC/antler-design-system@1.0.0/css/tokens.css" />
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/Antler-VC/antler-design-system@1.0.0/css/text-styles.css" />
```

- **`css/tokens.css`** — the design tokens (custom properties): color roles,
  palette, typography, spacing, radii, layout. Safe for every consumer.
- **`css/text-styles.css`** — the `.text-*` classes and the automatic text
  rhythm (flow) layer, for consumers **without** Tailwind. Tailwind sites must
  NOT load this file — their theme mapping generates the same classes.

Text rhythm only applies inside a `.antler-scope` wrapper (put it on `<body>`
for a standalone page, or on the embed's wrapper `<div>` in a host page), with
`.light` or `.dark` alongside it for the theme.

Load Satoshi in your `<head>`:

```html
<link rel="preconnect" href="https://api.fontshare.com" crossorigin />
<link rel="stylesheet" href="https://api.fontshare.com/v2/css?f[]=satoshi@300,400,500,1&display=swap" />
```

How to build pages with these tokens — the vocabulary, hard rules, and
recipes — is documented in `design.md` in the website repo.

## Versioning

Releases are git tags (`v2.0.0`, `v2.1.0`, …). Version-pinned jsDelivr URLs
are cached permanently — a page built against `@1.0.0` renders identically
forever. Never point production pages at `@main`.

## Smoke test

Open `preview.html` in a browser (locally or via the CDN) — it renders the
text styles, color roles, theming, and CTA using only the two published files.
