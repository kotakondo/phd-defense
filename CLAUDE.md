# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single self-contained `index.html` — a PhD thesis defense invitation and door-to-door directions page for Kota Kondo (MIT AeroAstro, Aerospace Controls Lab). All CSS is inlined in a `<style>` block; the only external dependencies are Google Fonts (Space Grotesk, IBM Plex Sans, IBM Plex Mono). There is no build step, no JavaScript, no package manager, and no tests.

## Developing

Open `index.html` directly in a browser, or serve the folder (`python3 -m http.server`) and reload. Edits are live on save — nothing to compile.

## Structure & conventions

The page is a vertical sequence of numbered sections (`01 Getting there`, `02 On the map`, `03 What to look for`, `04 Access & remote`) plus a hero and footer. Visual system:

- **Design tokens** live in `:root` CSS custom properties (`--paper`, `--ink`, `--amber`, `--path`, etc.). Change colors there, not at call sites.
- **Directions** are a `.route` `<ol>` of `.wp` waypoints; the last one carries `.goal` for the highlighted destination styling. The connecting line and node dots are pure CSS (`::before`, `.node`).
- **Placeholders the author must fill** are marked two ways: a `.todo` pill (`<span class="todo">ADD THIS</span>`) for hero/cards/footer, and `.fill` italic spans (e.g. `[Building XX]`) inside the waypoints. The checklist of everything outstanding is in the HTML comment at the top of `<head>` ("TODO FOR KOTA"). When filling these in, remove the surrounding `.todo`/`.fill` markup so the placeholder styling disappears.
- The hero `.traj` SVG is an animated dashed "trajectory" backdrop; `@media(prefers-reduced-motion:reduce)` disables all animation.

Layout is mobile-responsive via `@media(max-width:560px)` breakpoints that collapse the multi-column grids (`.brief`, `.cards`, `.photos`) to single column.
