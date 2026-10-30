# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Static GitHub Pages site (served from `main`, root folder) with interactive neutrino animations that accompany the poster “Neutrinos: las partículas fantasma” for IF-UNAM Puertas Abiertas, 13 Nov 2026. Live at https://moiseszeleny.github.io/divulgacion-neutrinos/. All user-facing text, code comments, identifiers and commit messages are in **Spanish** — keep it that way.

## Commands

No build, lint or test tooling. Preview locally with:

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

Pushing to `main` redeploys the site in a couple of minutes (`.nojekyll` disables Jekyll).

## Architecture and constraints

- **Plain HTML/CSS/JS, zero dependencies and no external fonts/CDNs.** Each page must stay under ~30 KB and work on a weak mobile signal at the event. Each experience is a single self-contained `index.html` with page-specific `<style>` and an inline IIFE `<script>` (ES5 style: `var`, `"use strict"`), drawing on `<canvas>`.
- `assets/estilo.css` is the only shared file: CSS custom properties (`--nu-e`, `--nu-mu`, `--nu-tau`, `--cherenkov`, etc.) match the printed poster's colors, plus shared classes (`.barra`, `.tarjeta`, `.lienzo`, `.controles`, `.boton`, `.aviso`). The flavor colors are also duplicated as JS constants (e.g. `COLORES`/`RGB` in `oscilaciones/index.html`) — change both together.
- Pages link with relative paths (`../assets/estilo.css`, `../`); `404.html` is the exception and uses absolute `/divulgacion-neutrinos/...` paths because GitHub Pages serves it from any URL.
- Animations respect `prefers-reduced-motion` (start paused).

### Pages

- `oscilaciones/` — exact three-flavor vacuum oscillation probabilities (hand-rolled complex arithmetic, PMNS matrix, NuFIT 6.0 normal ordering; amplitude phase `2.534·m²·L/E` with L in km, E in GeV, m² in eV²; antineutrinos via U → U*). Scenarios reactor / DUNE / atmospheric. No MSW matter effects by design (the page text says so; solar neutrinos intentionally omitted).
- `cherenkov/` — wavefronts and Cherenkov cone, cos θ = 1/(nβ) with n = 1.31 ice, 1.33 water, 1.0003 air; simulated IceCube event colored by arrival time.
- `via-lactea/` — Milky Way in visible light vs. neutrinos (IceCube 2023). Shows a browser-generated schematic unless `assets/img/via-lactea-optica.jpg` and `assets/img/via-lactea-neutrinos.jpg` exist (2:1, ~1600×800, <250 KB each); the `<img>` tags are `hidden` and revealed when they load. Image credit text lives in that page.

### QR redirects — do not break

The printed QR codes (`qr/*.svg|png`) point to `q/osc/`, `q/cherenkov/`, `q/galaxia/`, which are tiny meta-refresh + `location.replace` redirect pages to the real experiences. To change where a QR goes, edit `q/<nombre>/index.html`. **Never rename or remove the `q/` folders** — the posters are already printed.

## Repo quirks

- Files are sometimes copied in from Windows, which creates `*:Zone.Identifier` junk files; `.gitignore` excludes them.
- `.gitattributes` forces LF line endings.
- Open TODOs (from README): group name/members/email in `index.html`, real Milky Way images with credit, testing printed QR size.
