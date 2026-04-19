# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static personal website hosted on GitHub Pages at `sebastianelsner.de`. No build step, no framework, no package manager - everything is plain HTML/CSS/JS deployed directly from the `master` branch.

The CSS (`css/styles.css`) is the compiled output of the Start Bootstrap Resume v7.0.6 theme (Bootstrap 5.2.3 bundled in). Do not hand-edit it for structural changes; only override via `<style>` blocks in individual pages if needed.

## Adding a blog post

1. Duplicate `blog/hello-world.html`, rename it to a slug (e.g. `blog/my-post.html`).
2. Update `<title>`, `<meta name="description">`, the `<h1>`, date, and body content.
3. Add an entry at the **top** of the list in `blog/index.html` (newest first):

```html
<div class="d-flex flex-column flex-md-row justify-content-between mb-5">
    <div class="flex-grow-1">
        <h3 class="mb-0"><a href="my-post.html">Post Title</a></h3>
        <p class="text-muted mb-1">One-line teaser.</p>
    </div>
    <div class="flex-shrink-0"><span class="text-primary">Month DD, YYYY</span></div>
</div>
```

## Page structure conventions

All pages (main and blog) share the same nav pattern. Blog pages use `../` relative paths for assets, CSS, and JS. The nav on blog pages links back to `../index.html#section` anchors rather than using `js-scroll-trigger` (that class only works on the single-page index).

The `js/scripts.js` activates Bootstrap ScrollSpy on `#sideNav` and collapses the mobile navbar on link click - only relevant on `index.html`.
