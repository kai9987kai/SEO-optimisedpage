# Kai William Piper — Creative Technology Portfolio

A responsive, dependency-free, single-file portfolio showcasing AI-enabled web tools, 3D modelling and technical art, real-time simulations, and 3D printing workflows.

The October 2026 upgrade preserves the original portfolio experience and adds more resilient search, shareable filtered views, portable exports, keyboard improvements, and an opt-in deterministic Canvas experiment. The website is designed for **static hosting**: no build system, backend, account, API key, or external JavaScript framework is required.

**Canonical site configured in the HTML:** [kai9987kai.pw](https://kai9987kai.pw/)  
**GitHub profile:** [github.com/kai9987kai](https://github.com/kai9987kai)  
**Main application file:** [`portfolio_upgraded_2026.html`](portfolio_upgraded_2026.html)

> **Release status:** Feature-complete upgrade candidate, with **23/23 local automated regression checks passing** on 17 October 2026. Production Core Web Vitals, cross-browser and assistive-technology validation remain outstanding. The canonical site link above is the configured domain, not a claim that this upgraded file has already been deployed there.

## Contents

- [Overview](#overview)
- [Features](#features)
- [Quick start](#quick-start)
- [Controls and keyboard shortcuts](#controls-and-keyboard-shortcuts)
- [Architecture](#architecture)
- [Data exports and privacy](#data-exports-and-privacy)
- [Testing and regression results](#testing-and-regression-results)
- [Performance and limitations](#performance-and-limitations)
- [Deployment](#deployment)
- [Customisation](#customisation)
- [Roadmap](#roadmap)
- [References](#references)
- [Credits and licensing](#credits-and-licensing)

## Overview

The page introduces Kai William Piper as a creative technologist and presents four original project areas:

1. **AI-enabled web tools** — client-side AI prototype interfaces, searchable memory, feedback, telemetry, and debugging workflows.
2. **Real-time simulation prototypes** — Unity/C# and Three.js-oriented systems, agents, procedural behaviour, and performance considerations.
3. **3D modelling and technical art** — Maya/Blender modelling, topology, UV layout, LOD planning, and game-ready exports.
4. **3D printing and fabrication debugging** — FDM calibration, tolerance tests, slicer profiles, and repeatable troubleshooting.

These are **portfolio capability areas**, not automatically verified claims of completed client projects. The expanded workflow descriptions illustrate approaches and should be supplemented with links, screenshots, measurements, and real case studies as those become available.

### Design goals

- Keep the existing content, identity, controls, and static-hosting simplicity.
- Improve usability without requiring account creation or client/server infrastructure.
- Work without external runtime assets; retain readable HTML, CSS, and JavaScript in one file.
- Be accessible by keyboard and respect reduced-motion preferences.
- Provide honest, inspectable demonstrations and measurements instead of unverifiable performance or AI claims.

## Features

| Feature | Implementation | Status |
| --- | --- | --- |
| Responsive portfolio layout | CSS Grid/Flexbox, fluid type, responsive cards | Retained |
| Auto / dark / light themes | CSS custom properties, `data-theme`, safe preference storage | Retained and hardened |
| Live project search | Normalised multi-term search with non-project matches | Improved |
| Category filters | All, AI, 3D, Simulation, Web, 3D printing | Retained |
| Search state in URL | `?q=` and `?filter=`; shareable portfolio views | Expanded |
| Command palette | Native dialog, keyboard commands, filtered actions | Improved |
| Project workflow disclosures | Expandable descriptions for all four original project areas | Added |
| Deterministic agent experiment | Opt-in, seeded Canvas 2D simulation with 60 Hz fixed-step logic | Added |
| Clipboard actions | Website URL, biography, checklist, image prompt, audit, vCard text | Retained |
| File exports | `.vcf`, project JSON, simulation JSON, browser diagnostics JSON | Added |
| Local diagnostics | LCP, CLS, event-latency proxy where browser APIs permit | Improved labelling |
| FAQ | Four visible answers, expand/collapse, matching JSON-LD | Retained |
| Search engine metadata | Canonical, social metadata, semantic HTML, structured data | Retained and revised |
| Print experience | Print CSS that keeps project headings visible | Fixed |
| Accessibility foundations | Skip link, semantic structure, visible focus, keyboard use, reduced motion | Improved |
| No-script content | Core portfolio content remains available without JavaScript | Retained |

### Deterministic agent field

The **Research Lab / Playground** includes a small visual experiment rendered with the browser's Canvas 2D API. Users can change the integer seed, choose **12–120** agents, adjust the speed multiplier between **0.25× and 2×**, start/pause the field, reset its initial conditions, and export a JSON snapshot.

- The simulation is **paused by default**, stops when the tab becomes hidden, and does not run animation when the operating system requests reduced motion.
- Simulation updates use a fixed **1/60-second step** and seeded initial conditions.
- Exported state contains positions, velocities, agent metadata, tick count, logical canvas size, seed, and current speed.
- Repeating a run using the same seed and tick count is intended to reproduce a fixed configuration. **Changes to the speed control during a run are not logged**, so the snapshot alone does not reconstruct arbitrary mid-run speed changes.
- The experiment is a deterministic motion demonstration; **it is not machine learning, reinforcement learning, or evidence of trained intelligence**.

## Quick start

### Option A — Open the HTML directly

Download or clone the project and open `portfolio_upgraded_2026.html` in a current desktop browser. The primary portfolio content does not need a web server. Some browser capabilities, particularly clipboard, URL history manipulation, and sharing, may behave differently on `file://` URLs.

### Option B — Run a local static server (recommended)

Requires Python 3:

```bash
python -m http.server 8000
```

From the folder containing `portfolio_upgraded_2026.html`, open:

```text
http://localhost:8000/portfolio_upgraded_2026.html
```

To use the upgraded page as the site's homepage, copy or rename it to `index.html` in your deployment folder and serve that directory. **This is a copy/rename operation, not a required code build step.**

### Example deep-link search

Once the file is deployed at the configured canonical root, visitors can use addresses such as:

```text
https://kai9987kai.pw/?q=Unity
https://kai9987kai.pw/?filter=ai
https://kai9987kai.pw/?q=simulation&filter=simulation
```

These examples describe supported URL parameters; whether the deployed site currently runs the upgrade must be verified separately.

## Controls and keyboard shortcuts

| Action | How to use it |
| --- | --- |
| Search portfolio | Use the search input at the top |
| Focus search | Press `/` when not typing in an editable field |
| Open command palette | `Ctrl+K` (Windows/Linux) or `⌘K` (macOS) |
| Select a command | Type a query, then `Enter`, or use `ArrowDown` and `ArrowUp` |
| Close command palette | `Escape` or its **Close** button |
| Filter project categories | Choose a category chip under **Work** |
| Restore all project cards | **Clear** or **Reset search and filters**, as appropriate |
| Change colour scheme | Click **Theme** to cycle Auto → Dark → Light |
| Share selected view | **Share current view**, which uses native sharing when available, otherwise the clipboard |
| Download contact card | **Download .vcf** |
| Export project metadata | **Export project areas as JSON** |
| Run simulation | **Start simulation**; use **Pause simulation** to stop |
| Export simulation state | **Export run data** |
| Save local diagnostics | **Export session diagnostics** |
| Open/close FAQ answers | Activate each FAQ row, or the **Open all FAQs** control |

## Architecture

```text
.
├── portfolio_upgraded_2026.html       # All page markup, internal CSS, JSON-LD and JavaScript
├── portfolio_original_baseline.html    # Original HTML for comparison (optional)
├── README.md                           # This document
├── regression_portfolio.py             # Playwright browser regression checks (optional)
├── portfolio_regression_results.json   # Saved regression test results (optional)
├── portfolio_benchmark_trials.json     # Saved local timing trials (optional)
└── PORTFOLIO_UPGRADE_AUDIT.md          # Detailed feature-preservation audit (optional)
```

Only **`portfolio_upgraded_2026.html`** is required to operate the portfolio. The testing and audit files are optional development artefacts; the tree above describes the recommended development package, not a guarantee that every file already exists in a particular GitHub repository.

### Technical implementation

- **HTML5:** Semantic sections, navigation, `details`, `dialog`, accessible control labels, `canvas`, `time`, and JSON-LD.
- **CSS:** Embedded styles, custom properties, responsive breakpoints, light/dark/auto themes, print layout and `prefers-reduced-motion` adjustments.
- **JavaScript:** Vanilla browser APIs; no bundler, framework, backend, CDN-imported runtime script, npm install, or API token.
- **State:** Search/filter state is reflected in query parameters. Theme preference is stored via `localStorage` when permitted and safely falls back when denied.
- **Rendering:** The optional simulation uses Canvas 2D and `requestAnimationFrame`; it does not import Three.js or WebGPU.
- **Instrumentation:** Browser `PerformanceObserver` provides opportunistic in-session metrics. Missing API support is handled as a limitation, not a zero measurement.
- **Downloads:** JSON and vCard files are produced locally using `Blob` and temporary object URLs.

### What is **not** bundled

The site includes content describing Three.js, WebGPU, machine learning, Maya, Unity and other technologies. **Those descriptions and research roadmap panels do not mean those engines, SDKs, models, or GPU capabilities are embedded in the page.** Likewise, this is not a backend search engine, analytics service, or live model-inference demonstration.

## Data exports and privacy

| Download | Filename | Contents |
| --- | --- | --- |
| Contact | `kai-william-piper.vcf` | vCard 4.0 containing published name, title, URLs, description and location |
| Project metadata | `kai-project-areas.json` | Titles, descriptions, tags, workflow text and export timestamp for the four categories |
| Agent state | `agent-simulation-run.json` | Deterministic experiment configuration and exported agent state |
| Diagnostics | `portfolio-session-diagnostics.json` | Locally observable performance-related values and debugging metadata |

The supplied single-file website does **not** implement an analytics endpoint, remote telemetry upload, login, tracking service or third-party runtime. Exported diagnostics are saved by the user's browser when explicitly requested. Theme preference is the intended browser-local persistent setting; visitors should not assume downloaded JSON is anonymous if they later share it with someone else.

## Testing and regression results

The upgrade was checked against the preserved original HTML in a local automated browser suite. **All 23 checks passed** in the captured run dated **17 October 2026**.

Coverage included:

- Presence of original interface elements, five core sections and all four original project cards.
- Search, filtering, empty-state recovery, reset and share-link parameter generation.
- Theme switching when access to browser storage is denied, reproducing and fixing a baseline failure.
- Command palette keyboard handling and focus behaviour.
- FAQ expand/collapse and six original clipboard-copy actions.
- Valid CRLF-separated vCard, project JSON, agent JSON and diagnostics downloads.
- Seeded simulation controls, deterministic state export and reduced-motion suppression.
- Structured-data checks, print heading preservation, lack of added runtime dependencies and no horizontal overflow at a **390 px** viewport.

### Re-run the regression suite

Requires Python 3, Playwright, Beautiful Soup 4 and Chromium:

```bash
python -m pip install playwright beautifulsoup4
python -m playwright install chromium
python regression_portfolio.py
```

Run from a folder containing the Python test script and both `portfolio_original_baseline.html` and `portfolio_upgraded_2026.html`. The script writes `portfolio_regression_results.json` and `browser_performance_comparison.json`, exits non-zero on failed checks, and reports the aggregate result.

**Test-environment caveat:** These checks used Playwright's `page.set_content()` in headless Chromium because direct navigation was restricted in the test environment. They do not certify real deployment, browser history persistence across reloads, production caching, mobile Safari, screen-reader conformance, or field Core Web Vitals.

See [`PORTFOLIO_UPGRADE_AUDIT.md`](PORTFOLIO_UPGRADE_AUDIT.md) for the full preservation matrix, test methodology and outstanding verification work when the audit file is included alongside this README.

## Performance and limitations

The new implementation provides additional features but **does not beat the original in every metric**. The following values were recorded using ten alternating local headless Chromium `page.set_content()` trials, with no network request:

| Measurement | Original | Upgraded | Interpretation |
| --- | ---: | ---: | --- |
| Source document size | 56,903 bytes | 77,442 bytes | Upgrade is larger |
| Gzip level 9 | 14,769 bytes | 20,980 bytes | Upgrade transfers more bytes if compressed similarly |
| Median local harness elapsed time | 43.42 ms | 60.80 ms | Upgrade is slower in this restricted test |
| Median reported DOMContentLoaded | 31.75 ms | 32.25 ms | Approximately similar in this test; not a production navigation comparison |
| External runtime dependencies | 0 | 0 | No regression |
| Automated regression checks | Baseline fails in denied-storage case | 23/23 passing | Candidate improves tested robustness |

The local harness time is **not** Lighthouse, real network loading time, true user-perceived startup time, or a statistically reliable field benchmark. The page's **INP proxy** is not official Interaction to Next Paint. Claims of superior real-world speed require independently measured production or controlled-network data.

Other limitations:

- Portfolio skill percentages are illustrative self-assessments, **not independently validated proficiency scores**.
- The current four project cards are high-level capabilities, not individual evidenced case studies.
- A genuine social preview image, favicon, `robots.txt` and `sitemap.xml` are not provided by the standalone HTML.
- The source's Bournemouth location, canonical domain, contact route and project claims need owner review before publication.
- FAQ and SearchAction structured data do not guarantee rich search results; Google has restricted FAQ display and retired sitelinks search-box presentation.
- Live/production checks are still needed for accessibility, security headers, mobile browsers, browser zoom, high contrast and search indexing.

## Deployment

The site can be deployed on any static host supporting HTML files, including GitHub Pages and conventional web hosting.

1. Copy `portfolio_upgraded_2026.html` to the site's publishing location as `index.html` (or integrate its content with an existing index).
2. Check the configured canonical URL, site metadata, published location and GitHub/contact links in both the visible page and its JSON-LD.
3. Configure your host for HTTPS and appropriate response headers. Prefer a tested Content Security Policy, reasonable caching and compression. Inline styles/scripts require an appropriate CSP hash/nonce strategy if a restrictive CSP is introduced.
4. Add a real favicon, social preview image, `robots.txt` and `sitemap.xml` as separate assets if needed.
5. Test **direct navigation** to the homepage and deep-link queries; verify page behaviour after reload and with JavaScript disabled.
6. Run Lighthouse / PageSpeed Insights, validate structured data and inspect Search Console / Bing Webmaster Tools **on the actual deployed domain**.
7. Confirm content claims, responsive layout, keyboard navigation, contrast, reduced-motion handling and downloads on real devices.

### Deployment checklist

```text
[ ] Preserve a copy of the original site before overwriting it
[ ] Confirm domain, person details, contact routes and social metadata
[ ] Upload upgraded file as index.html
[ ] Add favicon and Open Graph image
[ ] Publish robots.txt and sitemap.xml where appropriate
[ ] Verify HTTPS, security headers, compression and cache policy
[ ] Test URL-search state and download permissions on the deployed origin
[ ] Run production browser, accessibility and speed audits
[ ] Review structured data and request indexing as appropriate
```

## Customisation

The page deliberately has no configuration build step. Edit the document directly:

- **Bio, location and contact information:** update the hero, header, footer, FAQ, vCard generator, JavaScript `profile` object and machine-readable `Person`/`ProfilePage` structured data together.
- **Visual themes:** edit the CSS custom properties near the top of the `<style>` element; keep sufficient contrast in light and dark modes.
- **Project cards:** each project lives inside the `#projects` region as an element with `data-project` and `data-tags`. Keep filter tags accurate; update export assumptions and any corresponding project-area JSON-LD.
- **Categories:** adding a filter chip also requires updating the categories used for card matching and ensuring the search/share URL accepts that category.
- **FAQ:** keep the visible answers aligned with the corresponding `FAQPage` JSON-LD; avoid asserting search-rich-result eligibility.
- **Experiment:** change the Canvas experiment controls and seeded simulation carefully, and re-run deterministic export and reduced-motion tests.
- **Canonical domain:** update it consistently in metadata, links, structured data, JavaScript share/export metadata and the vCard.

**Recommended change workflow:** retain `portfolio_original_baseline.html` as a known-good reference, modify the upgraded HTML, run automated regression checks, and then do a manual production-browser test before deploying.

## Roadmap

These are **future improvements**, not already implemented features:

- **Performance:** compare Lighthouse and real-network startup, reduce CSS/JS payload, review minification, and optimise long-task/interaction costs without removing controls.
- **Evidence-backed projects:** add actual repository references, project screenshots, measurable results, limitations and individual case-study pages.
- **Automated deployment checks:** run headless browser regressions and accessibility audits in CI against an actual served origin.
- **Browser coverage:** test Firefox, Safari, iOS/Android, forced-colour mode, 200–400% browser zoom and screen-reader navigation.
- **Real field instrumentation:** use a maintained Core Web Vitals implementation only if analytics and consent/privacy decisions justify it.
- **Expanded experiments:** investigate WebGPU and GPU-friendly pipelines with careful feature detection and accessible fallback paths; no current WebGPU integration is claimed.

## References

- [WCAG 2.2 — W3C](https://www.w3.org/TR/WCAG22/)
- [Interaction to Next Paint (INP) — web.dev](https://web.dev/articles/inp)
- [web-vitals — GoogleChrome](https://github.com/GoogleChrome/web-vitals)
- [Google FAQ rich-result changes](https://developers.google.com/search/blog/2023/08/howto-faq-changes)
- [Sitelinks search box retirement](https://developers.google.com/search/blog/2024/10/sitelinks-search-box)
- [Structured data documentation — Google Search Central](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data)
- [GitHub Pages documentation](https://docs.github.com/en/pages)

## Credits and licensing

**Site and portfolio:** Kai William Piper — [GitHub](https://github.com/kai9987kai).

This README does **not** assign a new software licence. Consult the repository's existing `LICENSE` file, if one exists; otherwise, add an explicit licence before representing the source code as licensed for reuse.
