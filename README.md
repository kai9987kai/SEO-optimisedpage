# SEO-optimisedpage — Kai William Piper's Creative Technology Portfolio

[![HTML5](https://img.shields.io/badge/HTML5-single--file-E34F26?logo=html5&logoColor=white)](index.html)
[![CSS3](https://img.shields.io/badge/CSS3-responsive-1572B6?logo=css&logoColor=white)](index.html)
[![JavaScript](https://img.shields.io/badge/JavaScript-vanilla-F7DF1E?logo=javascript&logoColor=black)](index.html)
[![Dependencies](https://img.shields.io/badge/runtime%20dependencies-0-2ea44f)](index.html)
[![Licence: MIT](https://img.shields.io/badge/Licence-MIT-blue)](LICENSE)

A fast-to-deploy, responsive, **single-file creative technology portfolio** designed around discoverable content, accessible interactions and inspectable browser-side experiments. It showcases **AI-enabled web tools, 3D modelling and technical art, real-time simulations, and 3D printing workflows**.

The complete application is in **[`index.html`](index.html)**: HTML, CSS, JavaScript and JSON-LD together. There is **no framework, bundler, npm installation, backend, API key or external runtime dependency**.

**Links:** [Source repository](https://github.com/kai9987kai/SEO-optimisedpage) · [Kai's GitHub profile](https://github.com/kai9987kai) · [Configured canonical website](https://kai9987kai.pw/)

> **Release note — October 2026:** The repository's `main` branch contains the upgraded portfolio as `index.html`. This README describes the code in that file, rather than a separate `portfolio_upgraded_2026.html` that is **not** present in the repository. The canonical URL is configured in the HTML; its presence does not independently verify the deployed site's current version.

## Contents

- [Highlights](#highlights)
- [Portfolio content](#portfolio-content)
- [Getting started](#getting-started)
- [Using the website](#using-the-website)
- [Interactive agent playground](#interactive-agent-playground)
- [Technical architecture](#technical-architecture)
- [SEO and structured data](#seo-and-structured-data)
- [Accessibility and privacy](#accessibility-and-privacy)
- [Testing and regression history](#testing-and-regression-history)
- [Performance and known limitations](#performance-and-known-limitations)
- [Deployment](#deployment)
- [Customisation](#customisation)
- [Roadmap](#roadmap)
- [Contributing and security](#contributing-and-security)
- [Licence and references](#licence-and-references)

## Highlights

| Area | Implemented in `index.html` |
| --- | --- |
| **Responsive interface** | Mobile-friendly cards, CSS Grid/Flexbox, fluid typography, sticky navigation, scroll progress indicator and print styles |
| **Themes** | Automatic (system), dark and light modes; browser-local preference with a storage-denial fallback |
| **Portfolio search** | On-page, multi-term search across project cards; matches elsewhere on the page are surfaced separately rather than hiding entire sections |
| **Project filters** | All, AI, 3D, Simulation, Web and 3D printing; categories combine with search |
| **Deep links** | URL parameters `?q=` and `?filter=` with share/copy support, browser history updates and restoration via navigation |
| **Command palette** | Keyboard-accessible native dialog for section navigation, filtering and useful actions |
| **Project explanations** | Four project-area cards, tags and expandable workflow disclosures |
| **Agent experiment** | Optional, seeded Canvas 2D motion simulation, fixed 60 Hz simulation steps, playback controls and JSON snapshot export |
| **Browser-side diagnostics** | Observed LCP, CLS and a clearly labelled interaction-event latency proxy where browser APIs permit |
| **Local exports** | vCard (`.vcf`), project-area JSON, simulation JSON and diagnostics JSON |
| **Copy and share actions** | Site link, short bio, deployment checklist, hero image prompt, audit summary, vCard text and filtered portfolio URL |
| **SEO foundation** | Descriptive document metadata, canonical/hreflang tags, Open Graph and Twitter metadata, semantic content and JSON-LD |
| **Accessible fundamentals** | Skip link, focus visibility, semantic landmarks, native FAQ disclosures, keyboard support and reduced-motion handling |
| **Static-first behaviour** | Core content remains readable when JavaScript is disabled |

**Important scope:** Terms such as Unity, Three.js, WebGPU, Maya and machine learning describe the creator's work or future directions. They **do not** mean those engines, models or SDKs are executed or bundled by this webpage. The playground is a deterministic motion visualisation, **not a trained AI agent**.

## Portfolio content

The homepage is organised around four capability areas:

1. **AI-enabled web tools** — interfaces for AI-related prototypes, local memory/search concepts, feedback, analytics and debugging.
2. **Real-time simulation prototypes** — game/simulation systems, agents, procedural behaviour, profiling and repeatable configurations.
3. **3D modelling and technical art** — topology, UVs, optimisation, level-of-detail planning and engine-ready workflows.
4. **3D printing and fabrication debugging** — FDM calibration, slicer settings, adhesion, tolerance testing and iteration.

There are also **Skills**, **Research Lab**, **Playground**, **Proof and process**, and **FAQ** sections. The examples in the project cards explain workflows and interests; they should not be read as independently verified production-client case studies. Links to finished assets, repositories and measured outcomes are useful future additions.

## Getting started

### Option 1: open locally

Clone the repository:

```bash
git clone https://github.com/kai9987kai/SEO-optimisedpage.git
cd SEO-optimisedpage
```

Open **`index.html`** in a modern browser. No build is required. Some browser APIs behave differently under `file://` URLs, so a local server is recommended for testing search URLs, sharing and downloads.

### Option 2: serve locally (recommended)

From the project directory, using Python 3:

```bash
python -m http.server 8000
```

Visit **http://localhost:8000/**.

### Repository layout

The GitHub repository reviewed for this README contains:

```text
SEO-optimisedpage/
├── index.html          # Complete interactive portfolio (HTML + CSS + JS + JSON-LD)
├── README.md           # Project documentation
├── LICENSE             # MIT licence
├── CODE_OF_CONDUCT.md  # Community participation guidance
└── SECURITY.md         # Security policy (see maintenance note below)
```

**No `package.json`, `src/` directory, build step or checked-in regression test script is required by or currently included in this repository.** Separate local test/audit artefacts were produced during development, but they are not part of the reviewed GitHub tree.

## Using the website

| Action | Control / shortcut |
| --- | --- |
| Search | Use the header search field; `/` focuses it when you are not typing in another input |
| Clear search | **Clear** button in the search field |
| Filter portfolio cards | Select **All**, **AI**, **3D**, **Simulation**, **Web**, or **3D printing** |
| Reset search and filters | **Reset search and filters** below the cards |
| Open command palette | **Ctrl+K** (Windows/Linux) or **⌘K** (macOS) |
| Navigate palette | Type to narrow commands; **↑/↓** to move; **Enter** to activate; **Esc** to close |
| Change theme | **Theme** button cycles Auto → Dark → Light |
| Share the current view | **Share current view** (native sharing where supported; otherwise copy link) |
| Copy text | **Copy site link**, **Copy short bio**, **Copy checklist**, **Copy vCard text**, **Copy hero image prompt**, or **Copy audit summary** |
| Download vCard | **Download .vcf** |
| Export portfolio metadata | **Export project areas as JSON** |
| Expand/collapse FAQs | Select individual questions or use **Open all FAQs** / **Close all FAQs** |
| Export session readings | **Export session diagnostics** |

Search and filter settings are represented in the URL. Examples for a deployment at the configured domain:

```text
https://kai9987kai.pw/?q=Unity
https://kai9987kai.pw/?filter=ai
https://kai9987kai.pw/?q=simulation&filter=simulation
```

Those are **URL-format examples**, not guarantees that a particular hosting deployment currently serves this commit.

## Interactive agent playground

The **Playground** section contains a dependency-free Canvas 2D experiment intended to demonstrate deterministic simulation and lightweight debugging.

- **Seed:** Integer-controlled pseudo-random initial conditions.
- **Agent count:** Adjustable from **12 to 120**.
- **Speed:** Adjustable from **0.25× to 2×**.
- **Playback:** **Start simulation** / **Pause simulation**.
- **Reset:** Reinitialises the visual field using the selected seed.
- **Export:** Saves `agent-simulation-run.json`, including seed, agent positions/velocities, state and simulated ticks.
- **Motion preferences:** Starts paused, pauses when the browser tab is hidden, and does not start animation when reduced motion is requested.

The simulation uses a **fixed 1/60-second update step** and draws frames with `requestAnimationFrame`. Reproducibility depends on the same logical canvas dimensions, seed, speed and tick count. **Mid-run speed adjustments are not logged as a complete replay history** in exported snapshots. This is a graphical motion experiment, not reinforcement learning or a neural model.

## Technical architecture

### HTML, CSS and JavaScript

Everything necessary to run the website is embedded in [`index.html`](index.html):

- **HTML:** Semantic `main`, `nav`, `section`, `article`, headings, `<details>` FAQs, native `<dialog>`, form controls, and Canvas.
- **CSS:** Theme custom properties, grid layout, responsive breakpoints, transitions, print rules and `prefers-reduced-motion` handling.
- **JavaScript:** Search/filter state, query-parameter synchronisation, commands, copy/share, browser-local preference handling, downloads, diagnostics, animation and event listeners.
- **JSON-LD:** A Schema.org graph describing the page/site/person, breadcrumbs, portfolio project areas and FAQs.

State is kept on the client. The site does not require a remote database, account login, paid API, external icon font or server-rendered framework.

### Downloadable files produced by the page

| File | Purpose |
| --- | --- |
| `kai-william-piper.vcf` | Contact information in vCard 4.0 format |
| `kai-project-areas.json` | Portfolio project descriptions, categories and workflow data |
| `agent-simulation-run.json` | Current simulation configuration and agent snapshot |
| `portfolio-session-diagnostics.json` | Locally observed browser/session diagnostic information |

The text-only **Copy vCard text** button is also retained separately from the actual `.vcf` download.

## SEO and structured data

The site includes an SEO-oriented baseline:

- A descriptive `<title>` and meta description.
- A canonical URL set to `https://kai9987kai.pw/` and an `en-gb` alternate link.
- Open Graph and Twitter metadata for link previews (the current HTML does **not** supply a dedicated social preview image).
- An index/follow robots meta directive.
- A Schema.org `@graph` with **WebSite**, **Person**, **ProfilePage**, **BreadcrumbList**, **ItemList**, and **FAQPage** entries.
- Human-readable headings, project descriptions and visible FAQs aligned with structured content.

These elements help search engines interpret a page, but **do not guarantee rankings, indexing or rich-result eligibility**. FAQ rich results are restricted by Google, and Google's sitelinks search box was retired; including `FAQPage` or `SearchAction` does not restore those features. The repository also does **not** currently contain a separate `sitemap.xml`, `robots.txt`, favicon or Open Graph image. Add appropriate files/assets when deploying if needed.

To verify indexing, use [Google Search Console](https://search.google.com/search-console/about), [Bing Webmaster Tools](https://www.bing.com/webmasters/), and Google's [Rich Results Test](https://search.google.com/test/rich-results) on the **deployed URL**.

## Accessibility and privacy

### Accessibility features

The implementation includes a skip-to-content link, native keyboard-compatible controls, visible focus styling, heading/landmark structure, live status announcements, reduced-motion support and accessible FAQ disclosures. The command palette restores focus to the previously active element after closing.

These design features **are not a certification of WCAG 2.2 AA compliance**. Actual screen-reader, forced-colours, browser zoom, cross-browser and assistive-technology testing is still recommended.

### Privacy and storage

The examined `index.html` has **no built-in account system, analytics-upload endpoint, third-party runtime library or remote inference request**. Theme settings are stored locally when permitted. Search terms, agent state and diagnostics are operated on in the browser; data files are saved only when users invoke an export action.

Exported diagnostics can include the user-agent string and visited URL. Treat files as **potentially identifying if redistributed**.

## Testing and regression history

An earlier development comparison between the original HTML and the upgraded HTML reported **23/23 automated regression checks passing on 17 October 2026**. The checks covered functional preservation, search/filter behaviour, keyboard interactions, copy/export actions, simulated storage denial, seeded Canvas behaviour, reduced motion, structured data, offline dependency parity, print output and a 390 px layout check.

**What this result means:** The tested upgrade candidate passed that local suite. It is **not** a fresh CI run against the currently hosted GitHub Pages site, and the regression script/results are **not in this repository**. Do not treat the historical result as an automatically verified badge for future commits.

### Recommended repeatable checks

1. Serve `index.html` from a local HTTP server.
2. Check search, each category, reset, and URL state after refresh/back navigation.
3. Test clipboard permission denial, blocked `localStorage`, file downloads and browser sharing fallback.
4. Test command palette focus, keyboard shortcuts, Escape, and reduced-motion preferences.
5. Confirm agent-seed reproducibility, pause behaviour and JSON-export fields.
6. Check layouts at desktop and mobile widths, 200–400% browser zoom, print preview and JavaScript disabled.
7. Run [Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/), [axe-core](https://github.com/dequelabs/axe-core), HTML/structured-data validation and real-browser smoke tests.

For automated tests, a useful next repository addition would be a Playwright suite and a GitHub Actions workflow so that every pull request can be checked without relying on historical results.

## Performance and known limitations

The richer feature set increases the document payload. The following figures came from an **earlier local, ten-run headless Chromium comparison** of original versus upgraded HTML; they are not current production Lighthouse or field measurements:

| Metric | Original | Upgraded |
| --- | ---: | ---: |
| HTML source size | 56,903 bytes | 77,442 bytes |
| Gzip size (level 9) | 14,769 bytes | 20,980 bytes |
| Median local test-harness elapsed time | 43.42 ms | 60.80 ms |
| External runtime dependencies | 0 | 0 |

The tested upgrade was **functionally better in the checked scenarios**, but **larger and slower in the local harness**. The timings do not establish real network loading speed, and the live website may behave differently depending on caching, compression, hardware and connection quality.

**Measurement caveats:** The browser-side "interaction latency" value is an **event-duration proxy, not official Interaction to Next Paint (INP)**. LCP and CLS readings are limited to the current session and available PerformanceObserver APIs. Missing data must not be interpreted as a score of zero.

**Other limitations:** Current capability percentages are illustrative self-assessments; four overview cards are not the same as independently evidenced case studies; contact/location claims and canonical domain should be reviewed before publication; and not all browsers expose every progressive-enhancement API.

## Deployment

This is a **static website**. Because the homepage file is already named `index.html`, you can deploy the repository root without renaming any file.

### GitHub Pages

1. Open the repository's **Settings → Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch** if you want a standard branch-based Pages deployment.
3. Select **`main`** and **`/ (root)`**, then save.
4. After publishing, check the Pages URL shown by GitHub and test search, downloads, HTTPS and page navigation.
5. If deploying to **`kai9987kai.pw`**, configure the custom domain and DNS correctly; confirm the domain resolves to the intended published site before relying on its canonical URL.

**This README does not assume GitHub Pages or the custom domain is already enabled.**

### SEO and launch checklist

- [ ] Confirm the site's public name, location, bio and contact details.
- [ ] Verify the canonical URL matches the real published homepage.
- [ ] Confirm GitHub Pages / static-host configuration and HTTPS.
- [ ] Add `robots.txt` and `sitemap.xml` if useful for the deployment.
- [ ] Add a favicon and a suitable Open Graph image.
- [ ] Validate social metadata, JSON-LD and mobile page appearance.
- [ ] Check keyboard navigation, high contrast, screen-reader usage and reduced motion.
- [ ] Run Lighthouse/PageSpeed Insights against the deployed site and compare LCP, CLS and INP using appropriate methods.
- [ ] Verify indexing and crawl issues in Google Search Console and Bing Webmaster Tools.
- [ ] Ensure any security headers/CSP allow the site's inline CSS and JavaScript; restrictive CSP requires explicit hashes/nonces or a deliberate policy.

## Customisation

To edit the portfolio, modify [`index.html`](index.html) directly, then retest key interactions:

- **Brand/profile:** Update the header, introductory copy, footer, FAQ, vCard generator, JavaScript profile metadata and matching `Person`/`ProfilePage` JSON-LD together.
- **Design:** Adjust CSS custom properties for colour, spacing, typography and surface styling.
- **Projects:** Update the four `data-project` cards and their `data-tags`, expandable workflow details, project exports and relevant structured data.
- **Filters:** Keep category buttons consistent with each project's token-based tags.
- **Search links:** Preserve the `q` and `filter` query parameter behaviour when changing search or routing logic.
- **Playground:** Keep the seeded initialisation, fixed-step update, pause/export behaviour and motion accessibility guarantees intact.
- **FAQ:** Keep visible questions/answers aligned with the JSON-LD; do not promise rich-result display.

If adding substantial new capabilities, preserve the framework-free/static-first operation unless there is a clear, measured benefit to adding a dependency.

## Roadmap

**Ideas below are planned opportunities, not implemented features:**

- **Automated quality gates:** Commit Playwright regression tests and run them in GitHub Actions, alongside accessibility and HTML validation.
- **Evidence-rich portfolio:** Individual project pages, screenshots, source links, release history, measurements and lessons learned.
- **Measured performance work:** Minification/asset budgets, served-origin benchmarking, caching/compression checks and INP testing without deleting features.
- **Expanded compatibility:** Firefox, Safari, Android and iOS validation, plus assistive technology and forced-colour modes.
- **More interactive research:** Optional WebGPU-based experiments with feature detection and graceful Canvas fallback, when there is a concrete use case.
- **SEO assets:** Dedicated social preview imagery, sitemap, robots guidance and validated canonical-domain deployment.
- **Documentation maintenance:** Replace the generic version examples in [`SECURITY.md`](SECURITY.md) with a policy that matches this actual website and supported release process.

## Contributing and security

Issues and contributions can be discussed via the repository's [Issues page](https://github.com/kai9987kai/SEO-optimisedpage/issues), subject to the project's [Code of Conduct](CODE_OF_CONDUCT.md).

See [`SECURITY.md`](SECURITY.md) for the existing security-policy file. **At the time of review it contains generic example version numbers/reporting text**, so it should be customised before representing it as a fully operational vulnerability-disclosure policy. Do not post confidential vulnerability details in a public issue.

## Licence and references

Copyright © 2026 Kai Piper. The repository includes an **[MIT licence](LICENSE)**. See the licence text for the full permissions and conditions.

**Technical references:** [WCAG 2.2](https://www.w3.org/TR/WCAG22/) · [MDN: Web Performance APIs](https://developer.mozilla.org/en-US/docs/Web/API/Performance_API) · [web.dev: INP](https://web.dev/articles/inp) · [Google structured-data overview](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data) · [Google FAQ changes](https://developers.google.com/search/blog/2023/08/howto-faq-changes) · [Google sitelinks search-box retirement](https://developers.google.com/search/blog/2024/10/sitelinks-search-box) · [GitHub Pages](https://docs.github.com/en/pages)
