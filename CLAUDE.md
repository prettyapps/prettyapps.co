# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This repository is the source for **prettyapps.co**, a single-page static "Coming Soon" landing site for Pretty Apps (an iOS app studio). It is hosted on **GitHub Pages** with a custom domain configured via the `CNAME` file (`prettyapps.co`).

The entire site is one self-contained file: `index.html`. There is no build step, no dependencies, no package manager, and no test suite. Everything — markup, CSS, and JavaScript — lives inline in that single file.

## Development

- **Preview locally:** open `index.html` directly in a browser, or serve the directory with `python3 -m http.server` and visit `http://localhost:8000`.
- **Deploy:** push to the `main` branch. GitHub Pages serves `index.html` automatically; there is no build or CI pipeline.
- **Custom domain:** the `CNAME` file must keep containing `prettyapps.co` — deleting or changing it breaks the custom-domain mapping.

## Architecture & conventions

`index.html` is structured as: a `<style>` block, the HTML body, and a small `<script>` at the end.

- **Color system:** all colors are CSS custom properties defined in `:root` (`--deep`, `--void`, `--plum`, `--violet`, `--iris`, `--lavender`, `--mist`, `--pale`) forming a dark-purple/violet palette. Reuse these variables rather than hardcoding hex values.
- **Visual effects** are layered with `position: fixed` and explicit `z-index` (`bg-glow` and `orb`s at 0, `stars` at 1, `.container` content at 10, noise grain overlay at 100). Preserve this stacking order when adding elements.
- **Typography:** two Google Fonts loaded via `<link>` — `Cormorant Garamond` (serif body/headings) and `Cinzel` (uppercase brand/badge labels). Sizes use `clamp()` for fluid responsiveness.
- **Entrance animations:** content fades in via the `fadeUp` keyframe with staggered `animation-delay` values; elements start at `opacity: 0`. When adding new content, give it a delay that fits the existing sequence.
- **Star field** is generated at runtime by the inline `<script>` (80 randomly positioned `.star` elements) — it is not in the static markup.

## Contact

Site contact email is `misha@prettyapps.co` (used in the page's mailto link).
