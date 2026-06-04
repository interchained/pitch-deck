# Interchained + AiAssist Secure — Explainer

An interactive, single-page explainer and pitch site for **Interchained LLC**, covering two connected products:

- **AiAssist Secure (AiAS)** — a self-hosted, multi-tenant AI orchestration platform.
- **Interchained (ITC)** — the blockchain / digital-asset and coordination layer.

The narrative walks a reader from the problem (rented, fragmented, data-leaking SaaS) through both product layers, the ecosystem loop, use cases, market timing, and the opportunity — ending on a "builder-owned infrastructure" thesis.

---

## Deliverables

| File | Purpose |
|------|---------|
| `Interchained Explainer.html` | The primary interactive site. Scroll-through narrative with sticky nav, scroll-spy, a progress indicator, and a presenter **Pitch Mode** that advances section-by-section. |
| `Interchained Explainer-print.html` | A print / PDF-friendly version of the same content (flattened layout, no interactive chrome). |

Open either file directly in a browser — no build step or server required.

---

## How it's built

- **React 18 + Babel Standalone** — components are authored as inline JSX and transpiled in the browser. No bundler.
- **Lucide** (UMD) for icons.
- **Google Fonts** — Space Grotesk (display) + Inter (body).
- All display copy lives in a single data file; components render from it rather than hardcoding text.

### Source structure (`explainer/`)

| File | Role |
|------|------|
| `data.js` | **Single source of truth for all copy** — headlines, body, nav labels, section registry, links. Exposed on `window.DATA`. |
| `app.jsx` | Root `App`: wires the section registry into nav, scroll-spy, progress, and pitch mode. |
| `chrome.jsx` | Navigation, progress indicator, and pitch-mode controls. |
| `shared.jsx` | Shared hooks (`useScrollSpy`, `usePitchMode`, `useReducedMotion`) and primitives, on `window.Shared`. |
| `visuals.jsx` | Diagram / visual components (dashboards, rails, loops, maps). |
| `sections1.jsx` | Hero, Problem, AiAS Solution, ITC Layer sections. |
| `sections2.jsx` | Ecosystem, Use Cases, Why Now, Pitch, Closing, Footer sections. |
| `styles.css` | Layout, type, background field/grid, tokens. |
| `components.css` | Component-level styles. |
| `assets/` | Logos (Interchained, AiAS). |

`screenshots/` holds reference captures; `uploads/` holds the original logo source files.

---

## Editing

- **To change wording**, edit `explainer/data.js` — nearly all text flows from there.
- **To reorder or rename sections**, edit the `sections` registry in `data.js`. Nav, progress indicator, scroll-spy, and pitch-mode navigation all derive from it.
- **To change layout or styling**, edit `styles.css` / `components.css`.
- **To change structure / components**, edit the relevant `sections*.jsx` or `visuals.jsx`. Scripts load in order (data → shared → visuals → chrome → sections → app); keep that order intact in the HTML if adding files.

> Note: components share scope via `window` namespaces (`window.Shared`, `window.Chrome`, `window.Sections1`, `window.Sections2`, `window.DATA`) because each Babel `<script>` is transpiled in isolation.

---

## Disclaimer

ITC is a digital asset for ecosystem participation, access, and coordination. Nothing in this explainer is financial advice or an offer of securities.
