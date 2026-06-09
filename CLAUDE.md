# NYSGPT — Landing Page Design Gallery

**What this is:** A gallery of standalone landing-page design explorations for **NYSGPT**, an AI-first software company that builds domain-specific AI applications for complex, legacy, and regulatory systems. The gallery happens to double as a portfolio that links out to the eight live/shipped NYSGPT products.

**Positioning (canonical):** "AI for complex, legacy systems." NYSGPT = one founder (Brendan Stanton), full-stack, eight shipped products, all on one **ingest → ground → ship** architecture (crawl/structure the primary record → ground every answer in a verifiable source → rebuild the interface). Voice = grounded-not-generated, the-data-is-the-product, ship-to-production. Sourced from `code/resume` project MDX + `src/resources/content.tsx`.

**Stack:** Pure static — plain HTML/CSS/JS, **no build step**, one self-contained file per page. Deploy as-is.

## Pages

| File | Name | Direction |
|------|------|-----------|
| `index.html` | **Gallery** | Index/chooser; links to all designs, grouped into 3 labeled families (Editorial / Luminous / Blueprint). Has its own light/dark. |
| `variant-a.html` | **Broadsheet** | (Editorial family) Editorial engineering terminal — Fraunces serif + Spline mono, hairline rules, portfolio as a precise data table. Signal-orange accent. |
| `variant-a1-column.html` | **Column** | (Editorial family) Newspaper front page — double-rule nameplate + edition/folio lines, a 3-column justified lede with red drop-cap + run-in, products as a ruled "Register" index. Press-red. **Dark = night edition, light = warm newsprint.** Fraunces + Newsreader. |
| `variant-a2-dispatch.html` | **Dispatch** | (Editorial family) Newsroom wire terminal — a **live typewriter-streamed bulletin** in the hero, a scrolling amber ticker, products filed as an **AP-style wire feed that prints in on scroll**. Mono-forward (IBM Plex Mono). Teletype-amber on charcoal; light = telex paper. The bold/functional one. |
| `variant-a3-folio.html` | **Folio** | (Editorial family) Luxe print-magazine spread — oversized Fraunces+Playfair cover headline, asymmetric 12-col editorial grid w/ page-folio numbers, pull-quotes, products as a "Contents" feature spread. Claret/oxblood + a whisper of gold. Dark cover stock; light = cream gallery. The expressive one. |
| `variant-b.html` | **Aurora** | (Luminous family) Luminous/atmospheric — drifting gradient-mesh + grain + pointer parallax, Bricolage display, glowing gradient accent, lifting cards. The parent. |
| `variant-b1-signal.html` | **Signal** | (Luminous family) Live phosphor **oscilloscope** — a real `<canvas>` scope sweeps the hero (3 animated beams = ingest/ground/ship over a graticule), full-page scanlines + grain + CRT vignette, products read out as **8 channels (CH01–CH08)** each with its own mini SVG sparkline trace that draws in on scroll. Space Grotesk + Chivo Mono, phosphor-teal beam. **Dark = phosphor CRT, light = lab-bench paper readout.** The bold/functional one. |
| `variant-c2-schematic.html` | **Circuit** | (Blueprint family) Live PCB/wiring schematic — CORE bus → 8 product nodes rendered into SVG by JS, animated signal pulses, hover-to-trace. Solder-green accent. The most ambitious. |
| `variant-c1-spec.html` | **Datasheet** | (Blueprint family) Electronics datasheet — abs-max ratings table, electrical-characteristics product table (Sym/Param/Typ/Unit/Status), revision-history footer. Saira Condensed + mono, amber accent. |
| `variant-c3-plate.html` | **Plate** | (Blueprint family) Exploded-assembly drawing — **LIGHT by default** (drafting-paper inversion), item balloons + leader lines + parts list, page inside a drawing border. Fraunces serif, red-pencil accent. |
| `variant-c.html` | **Blueprint (combined)** | Original all-in-one: portfolio drawn three ways down one page (spec sheet · schematic · exploded plate). Cyanotype navy. |

**Families & method.** Designs are grouped into families that share DNA but each sub-variant is "its own world" (own palette, type, layout, signature move):
- **Editorial** (`a` / `a1` / `a2` / `a3`) — serif + mono, hairline rules, restraint, authority. Broadsheet is the parent; Column/Dispatch/Folio each diverge hard (newspaper / wire-terminal / magazine).
- **Luminous** (`b` / `b1`, more coming) — glow, motion, atmosphere, light-as-material. Aurora is the parent (gradient-mesh); Signal diverges into a live phosphor oscilloscope (canvas + scanlines + CRT).
- **Blueprint** (`c1`/`c2`/`c3`/`c`) — technical drafting / cyanotype. Split out of `variant-c.html`.

This is **The Iteration Project**: a fast landing-page foundry that doubles as a marketing + experimentation tool, advertising the 8 real platforms by reusing their messaging. **Speed first, then creativity + craft.** Alternate pragmatic ↔ bold per page. Content/messaging stays consistent across pages (fine-tune to fit the design only). Each new round updates the chooser and makes it a little better. Canonical hero/thesis/method/CTA copy lives in `variant-a.html` (and `variant-b.html`) — reuse it.

## Reusable components (to extract later — NOTE-ONLY, do not refactor yet)

Two patterns recur on nearly every page. Treat each as **one component with theme/content variants** (extract only when it stops being faster to copy inline):
- **`cta-pair`** — the primary + secondary button row (`.btn-primary` + `.btn-ghost`/`.btn-glow`/`.btn-line`). Label + `→`. Variants differ only by themed surface (orange solid / gradient-glow pill / green / amber / claret-pill) + secondary label ("See the products" / "Read the wire" / "Trace the board" / "Turn to the contents" …). Driven by each page's accent CSS vars.
- **`proof-bar`** — the 4-cell stat strip (`8 · 350k+ · 5 · {flex}`), each cell `big number / kicker label`. Variants differ by divider style (boxed grid / hairline rules / vertical pipes / serif-rule), label phrasing (`PRODUCTS / SHIPPED` vs `PRODUCTS SHIPPED`), and the 4th cell's content (Team:1 / Founder / Legacy:∞). Class names per page: `.ledger` (a), `.ribbon` (a1), `.proof` (a2), `.stats` (a3/b/b1).

## Conventions baked into every page

- **Light/dark toggle:** sun/moon button in the nav. `[data-theme="light"]` overrides on `:root`; **dark is default** (except Plate = light default, `data-theme="dark"` opts in). Persisted in `localStorage` under a **per-page key** (`nysgpt-theme-a` … `-b1` … `-c1/-c2/-c3`, `-idx` for the gallery). A pre-paint `<script>` in `<head>` sets the attr before first paint to avoid flash. Toggle defaults to the design's intended mode, NOT the OS preference.
- **Design playground:** floating palette-icon button (bottom-right) opens a panel with live controls — **accent color** (swatches + custom picker; Aurora retunes the whole gradient via `--cyan/--violet/--pink`), **display + body font** (curated per page), **corner rounding** (`--radius`), **heading weight** (`--wght` offset), **density** (`--density`). All drive CSS custom properties via `el.style.setProperty`. **Session-only** (no persistence) + a Reset button. Theme-dependent values are CSS vars so both modes stay coherent.
- **Conversion flow (shared):** primary CTA = "Book a working session" (mailto Brendan@nysgpt.com); secondary = a project-brief form that hands off via `mailto`. No backend.
- **Fonts:** distinctive, NOT generic (no Inter/Roboto/Arial). Loaded via Google Fonts `<link>`.

## Deploy

- **Repo:** https://github.com/nyd-user-1/nysgpt-landing (public, `main`).
- **Live:** https://nysgpt-landing.vercel.app — Vercel project `nysgpt-landing` (org `nyd-user-1s-projects`), **GitHub-connected → auto-redeploys on push to `main`**. Static, no build. `vercel` CLI authed as `brendan-5480`; `.vercel/` is gitignored.

## Workflow notes

- **Screenshots for verification:** no Playwright/Puppeteer installed here — use the bundled Chromium in `code/tariffs` (`node` a script from *inside* that dir so `playwright` resolves; never the system Chrome binary). Or use the Chrome DevTools MCP (being set up) to read live elements.
- Clean up `_*.png` preview screenshots (gitignored) when done.

## Roadmap / open edits

**Next up:** finish the **Luminous family** — 2 remaining sub-variants off Aurora (`b`), same "distinct worlds, shared DNA" method: **Prism** = refracted/chromatic-aberration; **Halo** = calm single-spotlight, the pragmatic one. Then grow into the canonical page types (changelog, docs, SaaS, converting LP, dashboard, chat, portfolio, commerce) over time.

**Shipped this round:** Luminous family expanded from 1 → 2 — added **Signal** (`b1`), the live phosphor-oscilloscope direction (a real animated `<canvas>` scope in the hero; products as 8 channels with mini draw-in sparklines; dark CRT / light lab-bench). Chooser renumbered (Editorial 01–04 · Luminous 05–06 · Blueprint 07–10), counts bumped to 10 explorations. Signal is genuinely new tech for the gallery — first canvas-driven page (Circuit uses SVG).

**Previous round:** Editorial family expanded 1 → 4 — added **Column** (`a1`), **Dispatch** (`a2`), **Folio** (`a3`); chooser regrouped into 3 labeled families.

_Blueprint (c1/c2/c3) backlog is cleared._

Resolved: Circuit section heads (`Signal`/`Board`/`Path`); Plate `Notes` rename + `// unless otherwise specified` removal; Plate section-header kicker tags dropped — both `NOTES` and `FIG. 1` removed so the headings stand alone (the figure's corner `NYSGPT-8 ASSEMBLY` tag stays); Plate part-name bottom margin opened up (5px → 20px) and the SportsGPT part caption trimmed to `choropleth maps · AI-generated highlights`.
