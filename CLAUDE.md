# NYSGPT — Landing Page Design Gallery

**What this is:** A gallery of standalone landing-page design explorations for **NYSGPT**, an AI-first software company that builds domain-specific AI applications for complex, legacy, and regulatory systems. The gallery happens to double as a portfolio that links out to the eight live/shipped NYSGPT products.

**Positioning (canonical):** "AI for complex, legacy systems." NYSGPT = one founder (Brendan Stanton), full-stack, eight shipped products, all on one **ingest → ground → ship** architecture (crawl/structure the primary record → ground every answer in a verifiable source → rebuild the interface). Voice = grounded-not-generated, the-data-is-the-product, ship-to-production. Sourced from `code/resume` project MDX + `src/resources/content.tsx`.

**Stack:** Pure static — plain HTML/CSS/JS, **no build step**, one self-contained file per page. Deploy as-is.

## Pages

| File | Name | Direction |
|------|------|-----------|
| `index.html` | **Gallery** | Index/chooser; links to all six designs. Has its own light/dark. |
| `variant-a.html` | **Broadsheet** | Editorial engineering terminal — Fraunces serif + Spline mono, hairline rules, portfolio as a precise data table. Signal-orange accent. |
| `variant-b.html` | **Aurora** | Luminous/atmospheric — drifting gradient-mesh + grain + pointer parallax, Bricolage display, glowing gradient accent, lifting cards. |
| `variant-c2-schematic.html` | **Circuit** | (Blueprint family) Live PCB/wiring schematic — CORE bus → 8 product nodes rendered into SVG by JS, animated signal pulses, hover-to-trace. Solder-green accent. The most ambitious. |
| `variant-c1-spec.html` | **Datasheet** | (Blueprint family) Electronics datasheet — abs-max ratings table, electrical-characteristics product table (Sym/Param/Typ/Unit/Status), revision-history footer. Saira Condensed + mono, amber accent. |
| `variant-c3-plate.html` | **Plate** | (Blueprint family) Exploded-assembly drawing — **LIGHT by default** (drafting-paper inversion), item balloons + leader lines + parts list, page inside a drawing border. Fraunces serif, red-pencil accent. |
| `variant-c.html` | **Blueprint (combined)** | Original all-in-one: portfolio drawn three ways down one page (spec sheet · schematic · exploded plate). Cyanotype navy. |

The three Blueprint sub-variants (c1/c2/c3) were split out of `variant-c.html` — each is "its own world" (own palette, type, motion) while sharing cyanotype/drafting roots.

## Conventions baked into every page

- **Light/dark toggle:** sun/moon button in the nav. `[data-theme="light"]` overrides on `:root`; **dark is default** (except Plate = light default, `data-theme="dark"` opts in). Persisted in `localStorage` under a **per-page key** (`nysgpt-theme-a` … `-c1/-c2/-c3`, `-idx` for the gallery). A pre-paint `<script>` in `<head>` sets the attr before first paint to avoid flash. Toggle defaults to the design's intended mode, NOT the OS preference.
- **Design playground:** floating palette-icon button (bottom-right) opens a panel with live controls — **accent color** (swatches + custom picker; Aurora retunes the whole gradient via `--cyan/--violet/--pink`), **display + body font** (curated per page), **corner rounding** (`--radius`), **heading weight** (`--wght` offset), **density** (`--density`). All drive CSS custom properties via `el.style.setProperty`. **Session-only** (no persistence) + a Reset button. Theme-dependent values are CSS vars so both modes stay coherent.
- **Conversion flow (shared):** primary CTA = "Book a working session" (mailto Brendan@nysgpt.com); secondary = a project-brief form that hands off via `mailto`. No backend.
- **Fonts:** distinctive, NOT generic (no Inter/Roboto/Arial). Loaded via Google Fonts `<link>`.

## Deploy

- **Repo:** https://github.com/nyd-user-1/nysgpt-landing (public, `main`).
- **Live:** https://nysgpt-landing.vercel.app — Vercel project `nysgpt-landing` (org `nyd-user-1s-projects`), **GitHub-connected → auto-redeploys on push to `main`**. Static, no build. `vercel` CLI authed as `brendan-5480`; `.vercel/` is gitignored.

## Workflow notes

- **Screenshots for verification:** no Playwright/Puppeteer installed here — use the bundled Chromium in `code/tariffs` (`node` a script from *inside* that dir so `playwright` resolves; never the system Chrome binary). Or use the Chrome DevTools MCP (being set up) to read live elements.
- Clean up `_*.png` preview screenshots (gitignored) when done.

## Open edits (requested, not yet applied)

- **Circuit (c2):** section heads → `Signal`, `Board`, `Path` (drop "The"; "signal path" → just "Path").
- **Plate (c3):** "General notes" → `Notes`; remove the `// unless otherwise specified` subline; remove the duplicate inner `FIG. 1 — NYSGPT-8 ASSEMBLY` header row; move the `FIG. 1` tag to **straddle the top-right corner of the figure box** (on the border, not inside).
