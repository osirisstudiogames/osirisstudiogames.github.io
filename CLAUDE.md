# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Static GitHub Pages site (`osirisstudiogames.github.io`) hosting support/legal pages for oSiRiS Studio's apps. No build step, no dependencies, no tests — every page is a self-contained HTML file with inline CSS, served as-is by GitHub Pages from `main`.

## Commands

None. Preview changes by opening the HTML file directly in a browser (or a local static server); commit and push to `main` to publish — GitHub Pages serves the branch directly.

## Structure

- `index.html` — landing page, links to both apps below.
- `404.html` — custom not-found page.
- `sudoku/` — pages for **Sudoku Master: Classic Logic** (mobile app): `support.html`, `privacy.html`, `terms.html`.
- `vektra/` — pages for **Vektra** (Discord bot): `support.html`, `privacy.html`, `terms.html`.
- `app-ads.txt` — required at the root by AdMob for the Sudoku app; do not move.
- `favicon.png` in the root and in each app folder (`sudoku/favicon.png`, `vektra/favicon.png`) — every page's `<link rel="icon">`/`apple-touch-icon`/`og:image` points at the favicon in its own folder, so a new page must live inside the right folder to pick up the correct icon without extra config.

## Conventions across pages

- Every page repeats the same inline `<style>` block (no shared stylesheet) — when tweaking shared look and feel (colors, fonts, footer style), edit each page individually; there's no single source of truth to change once.
- Every page carries the full meta-tag set: `favicon`, `apple-touch-icon`, `theme-color` (`#1a73e8`, the accent blue used for links/headers everywhere — keep new pages consistent with it), `description`, and Open Graph (`og:type`, `og:title`, `og:description`, `og:url`, `og:image`) + `twitter:card`. Copy this block from a sibling page in the same folder rather than reinventing it, and update the `og:url`/`og:title`/`og:description` values for the new page.
- Footers cross-link the sibling pages in the same folder plus `../index.html`; keep that pattern when adding a page so navigation stays consistent.
- Each app's `support.html` documents that app's account/data-deletion flow — required by app store / platform verification (Google Play data safety, Discord app verification). If a new data-collecting feature is added to either app, its `privacy.html` and `support.html` need a corresponding update.
- Contact email across all pages is `osirisstudio.games@gmail.com` (not the personal account email) — keep it consistent.

## External dependencies on exact URLs

Several pages' URLs are registered in external systems and must not be moved/renamed without updating those systems first:
- `sudoku/support.html`, `sudoku/privacy.html`, `sudoku/terms.html` — linked from Google Play Console (data safety / account deletion).
- `vektra/support.html`, `vektra/privacy.html`, `vektra/terms.html` — linked from the Discord Developer Portal (app verification for Monetization).

Changing any of these paths requires updating the corresponding external console afterward.
