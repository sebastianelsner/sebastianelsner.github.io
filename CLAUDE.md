# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static personal website hosted on GitHub Pages at `sebastianelsner.de`. No build step, no framework, no package manager — plain HTML + a single CSS file, deployed directly from the `master` branch.

## Design system

All pages use the **engineering notebook** aesthetic defined in `css/notebook.css`:

- **Type**: JetBrains Mono for structural / CV / metadata; EB Garamond italic for the music section disruption and for blog post body (long-form readability).
- **Palette**: warm paper (`--paper`), ink, amber accent, oxblood reserved for the music section. Full dark-mode variant via `prefers-color-scheme: dark`.
- **Fonts**: served from `fonts.bunny.net` (GDPR-compliant Google Fonts mirror).
- **Disruption rule**: the music section is the only place that breaks from mono. Any new "fun" or personal section should follow the same pattern (paper-deep background, serif italic headline, oxblood accent).

## Adding a blog post

1. Duplicate `blog/hello-world.html`, rename to a slug (e.g. `blog/my-post.html`).
2. Update `<title>`, `<meta name="description">`, all `<meta property="og:*">` tags (title, description, url), the `<h1>`, the `.post-meta` date, and the body content.
3. Body content goes inside `<div class="body">…</div>`. Standard tags work: `<p>`, `<h2>` (renders as serif italic oxblood), `<h3>` (renders as small mono uppercase), `<code>`, `<pre>`, `<ul>`, `<a>`, `<strong>`, `<em>`, `<sup>`. There's also `<p class="tldr"><strong>TL;DR</strong> …</p>` for the lede.
4. Add an entry at the **top** of the list in `blog/index.html`:

```html
<a class="post" href="my-post.html">
    <div class="when">Month YYYY</div>
    <div class="body">
        <h3>Post Title</h3>
        <p>One-line teaser.</p>
    </div>
    <div class="arrow" aria-hidden="true">→</div>
</a>
```

5. Add the same teaser at the **top** of the `<section class="writing">` block in the root `index.html`, and remove the oldest one (home shows latest 3 only).

## Page structure conventions

- Root pages link `css/notebook.css` and `assets/img/favicon.ico`. Blog pages use `../css/notebook.css` and `../assets/img/favicon.ico`.
- Every page must include the Bunny font preconnect + stylesheet link (JetBrains Mono + EB Garamond).
- Every page must include the Umami snippet just before `</head>`.
- Decorative glyphs (`##`, `¶`, `→`, `✓`, `_`) carry `aria-hidden="true"`.
- Section headings use `<h2 class="name">` inside `<div class="sec-h">`. Don't downgrade to `<span>` — heading hierarchy matters.

## Analytics

Every page includes:

```html
<!-- Umami analytics -->
<script defer src="https://cloud.umami.is/script.js" data-website-id="73702148-36e0-4a0b-889e-6e1c29e062c0"></script>
```

No templating layer, so this snippet must be present on every new HTML page. Duplicating an existing post carries it over automatically; pages created from scratch must add it manually.
