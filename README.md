# NYSGPT — Landing Page Design Gallery

A working gallery of landing-page design explorations for **NYSGPT**, an AI-first software company building domain-specific AI applications for complex, legacy, and regulatory systems.

Each page is a complete, self-contained landing page (no build step — plain HTML/CSS/JS), with a **light/dark toggle** and a **live design playground** (accent color, display/body font, corner rounding, heading weight, density — session-only).

## The directions

| File | Name | Family · Direction |
|------|------|-----------|
| `index.html` | **Gallery** | The index — links to every design below, grouped by family |
| `variant-a.html` | **Broadsheet** | Editorial · engineering terminal — serif + mono, hairline rules, portfolio as a data ledger |
| `variant-a1-column.html` | **Column** | Editorial · newspaper front page — nameplate, a multi-column drop-cap lede, products as a ruled register. Night edition + newsprint |
| `variant-a2-dispatch.html` | **Dispatch** | Editorial · newsroom wire terminal — a live typed bulletin, a scrolling ticker, products as an AP-style wire feed that prints in |
| `variant-a3-folio.html` | **Folio** | Editorial · luxe magazine spread — an oversized cover headline, an asymmetric grid with page-folios, products as a contents spread |
| `variant-b.html` | **Aurora** | Luminous · atmospheric — drifting gradient-mesh, glowing accent, lifting cards |
| `variant-c2-schematic.html` | **Circuit** | Blueprint · live wiring schematic — CORE bus → 8 product nodes, animated signal pulses, hover-to-trace |
| `variant-c1-spec.html` | **Datasheet** | Blueprint · electronics datasheet — abs-max ratings, electrical-characteristics table, revision history |
| `variant-c3-plate.html` | **Plate** | Blueprint · exploded assembly drawing on white drafting paper — item balloons, leader lines, parts list |
| `variant-c.html` | **Blueprint (combined)** | Blueprint · the original all-in-one — portfolio drawn three ways down one page |

## The product portfolio (what these pages link out to)

Eight domain-specific AI products, all built on one ingest → ground → ship architecture:

- **44B** — public AI registry + NY Article 44-B compliance portal · [44b.nysgpt.com](https://44b.nysgpt.com)
- **TariffsGPT** — tariff refund engine · [tariffs.nysgpt.com](https://tariffs.nysgpt.com)
- **ChildcareGPT** — NY childcare intelligence · [childcare.nysgpt.com](https://childcare.nysgpt.com/console)
- **SolarGPT** — clean-energy intelligence · [solar.nysgpt.com](https://solar.nysgpt.com/map/plants-2)
- **PolicyGPT** — NY legislative & financial intelligence
- **NSRgpt** — Nuclear Science References semantic search + RAG
- **InsuranceGPT** — auto-insurance quote & lead engine
- **SportsGPT** — Section XI high-school sports intelligence

## Run locally

It's static — open `index.html` directly, or serve the folder:

```bash
python3 -m http.server 8088
# → http://127.0.0.1:8088
```

## Deploy

Static site, no build step. Deploys to Vercel as-is (`index.html` at the root).

---

NYSGPT · AI-first software for legacy systems · Long Island, NY · [Brendan@nysgpt.com](mailto:Brendan@nysgpt.com)
