# SEO-optimisedpage

> A fast, single-file, SEO-focused landing page for **Kai William Piper**, a Bournemouth-based creative technologist working across **3D asset pipelines**, **Unity/Three.js simulations**, **AI-enabled web tools**, and **3D printing workflows**.

[![Static HTML](https://img.shields.io/badge/build-static%20HTML-111827?style=for-the-badge&logo=html5&logoColor=white)](#)
[![No Framework Required](https://img.shields.io/badge/framework-none-2563eb?style=for-the-badge)](#)
[![SEO Focused](https://img.shields.io/badge/SEO-structured%20data-16a34a?style=for-the-badge)](#)
[![Accessible UX](https://img.shields.io/badge/accessibility-keyboard%20friendly-7c3aed?style=for-the-badge)](#)

---

## Overview

`SEO-optimisedpage` is a lightweight portfolio/landing page designed to be easy to deploy, easy to crawl, and easy to iterate. The project is intentionally simple: the core deliverable is `index.html`, with HTML, CSS, JavaScript, metadata, structured data, interactive UI, and conversion-focused content kept in one portable file.

The page is built around four priorities:

1. **Search visibility** — semantic HTML, canonical URL discipline, structured data, descriptive headings, and clear topical focus.
2. **Performance** — no required build step, no external framework dependency, minimal runtime overhead, and Core Web Vitals awareness.
3. **Accessibility** — skip link, keyboard navigation, focus states, landmarks, readable contrast, and reduced-motion support.
4. **Conversion** — clear profile positioning, project areas, contact routes, portfolio credibility, and copy-friendly calls to action.

---

## Current features

### SEO and discoverability

- Descriptive `<title>` and meta description.
- Canonical URL and `hreflang="en-gb"`.
- Open Graph and Twitter/X card metadata.
- Crawl-friendly semantic sections and headings.
- JSON-LD structured data for:
  - `WebSite`
  - `Person`
  - `ProfilePage`
  - `BreadcrumbList`
  - `ItemList`
  - `FAQPage`
- Visible FAQ content kept consistent with FAQ structured data.
- Search-intent-driven copy for creative technology, 3D, AI, simulation, web tooling, and 3D printing.

### User experience

- Responsive single-page layout.
- Sticky navigation with active section highlighting.
- On-page search.
- Project filters for AI, 3D, simulation, web, and 3D printing.
- Command palette with `Ctrl`/`⌘` + `K`.
- Copy buttons for links, short bio, checklist, hero prompt, and audit summary.
- Theme control with dark, light, and system modes.
- Toast/status messages for user actions.
- Print-friendly styles.

### Performance and quality

- Single static file: no bundler, package manager, or server framework required.
- System font stack to avoid external font loading.
- Minimal JavaScript with progressive enhancement.
- Local Core Web Vitals-style readouts for LCP, CLS, and interaction latency estimates.
- Reduced layout shift through stable structure and lightweight UI.
- No required third-party scripts.

### Accessibility

- Skip-to-content link.
- Semantic landmarks: `header`, `main`, `section`, `footer`, `nav`.
- Keyboard-operable controls.
- Clear `:focus-visible` styling.
- ARIA labels/status regions where useful.
- Reduced-motion handling via `prefers-reduced-motion`.
- Larger tap targets for interactive controls.

---

## Quick start

### 1. Clone the repository

```bash
git clone https://github.com/kai9987kai/SEO-optimisedpage.git
cd SEO-optimisedpage
```

### 2. Run locally

The page is static HTML, but serving it locally gives a more realistic test environment than opening the file directly.

**Python**

```bash
python -m http.server 8080
```

Then open:

```text
http://localhost:8080
```

**Node.js**

```bash
npx serve .
```

---

## Deployment

### GitHub Pages

1. Make sure the landing page is named `index.html`.
2. Commit and push changes.
3. Go to **Settings → Pages**.
4. Choose the branch and root folder.
5. Save and wait for GitHub Pages to publish.
6. Enable HTTPS when using a supported domain.

### Custom domain checklist

Create or update:

```text
CNAME
```

Add your domain name inside it, for example:

```text
kai9987kai.pw
```

Then confirm the same domain in the GitHub Pages settings.

---

## Recommended file structure

```text
SEO-optimisedpage/
├── index.html          # Main single-file landing page
├── README.md           # Project documentation
├── CNAME               # Optional: custom domain for GitHub Pages
├── robots.txt          # Optional: crawler rules
└── sitemap.xml         # Optional: canonical URLs for search engines
```

For a minimal setup, only `index.html` is required.

---

## Optional `robots.txt`

```txt
User-agent: *
Allow: /

Sitemap: https://kai9987kai.pw/sitemap.xml
```

---

## Optional `sitemap.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://kai9987kai.pw/</loc>
    <lastmod>2026-05-18</lastmod>
    <changefreq>monthly</changefreq>
    <priority>1.0</priority>
  </url>
</urlset>
```

Update `lastmod` whenever meaningful page content changes.

---

## SEO checklist

Before deploying, confirm:

- [ ] The canonical URL matches the live deployment URL.
- [ ] The page title is unique and describes the profile clearly.
- [ ] The meta description reads naturally and includes the main service areas.
- [ ] Only one primary `h1` is used.
- [ ] Headings are ordered logically.
- [ ] JSON-LD matches visible page content.
- [ ] Contact links work.
- [ ] GitHub/profile links use the correct destination.
- [ ] `robots.txt` does not block the page.
- [ ] `sitemap.xml` contains the canonical URL.
- [ ] The page is submitted in Google Search Console and Bing Webmaster Tools.

---

## Performance targets

Aim for these Core Web Vitals targets on real mobile and desktop data:

| Metric | Good target | What it means |
|---|---:|---|
| LCP | ≤ 2.5s | Main content loads quickly |
| INP | ≤ 200ms | Interactions feel responsive |
| CLS | ≤ 0.1 | Layout remains visually stable |

Suggested checks:

```bash
# Optional Lighthouse run if you have Chrome + Lighthouse installed
npx lighthouse http://localhost:8080 --view
```

Also test the live page with:

- PageSpeed Insights
- Lighthouse in Chrome DevTools
- Search Console Core Web Vitals report
- WebPageTest or similar waterfall tools

---

## Accessibility checklist

- [ ] Can the whole page be navigated using only the keyboard?
- [ ] Is focus always visible?
- [ ] Do buttons and links have meaningful names?
- [ ] Does the page work with reduced motion enabled?
- [ ] Are colour contrast levels readable in light and dark mode?
- [ ] Are tap targets comfortable on mobile?
- [ ] Does the page structure make sense in a screen reader outline?

Recommended tools:

- Lighthouse Accessibility audit
- axe DevTools
- WAVE
- Browser keyboard testing
- Screen reader smoke test with NVDA, VoiceOver, or Narrator

---

## Structured data validation

After deployment, test the live page with:

- Google Rich Results Test
- Schema.org validator
- Google Search Console URL Inspection

When editing structured data, keep the JSON-LD honest. Do not add awards, reviews, organisations, jobs, or claims that are not visible or accurate on the page.

---

## Editing guide

### Change the profile text

Search inside `index.html` for:

```text
Kai William Piper
```

Update the visible text first, then update matching metadata and JSON-LD.

### Change the canonical domain

Update every instance of:

```text
https://kai9987kai.pw/
```

Check:

- `<link rel="canonical">`
- Open Graph URL
- JSON-LD `url`
- `robots.txt`
- `sitemap.xml`
- Copy button text in JavaScript

### Add a new project area

Update:

1. The visible project card.
2. The filter chips if a new category is needed.
3. The JSON-LD `ItemList` if the project should be represented in structured data.
4. The command palette list if users should be able to jump to it quickly.

---

## Content strategy

The page should stay focused on one clear identity:

> Bournemouth creative technologist building production-minded 3D, simulation, AI, web, and 3D printing workflows.

Useful search phrases to support naturally:

- Creative technologist Bournemouth
- 3D modelling Maya Blender portfolio
- Unity simulation developer
- Three.js interactive simulation
- AI web tools portfolio
- Technical artist UK
- 3D printing workflow and prototyping
- Single-file web tools

Avoid keyword stuffing. Write for humans first, then use clean structure to help search engines understand the page.

---

## Roadmap

Potential next improvements:

- [ ] Add real project case studies with screenshots and measurable outcomes.
- [ ] Add an Open Graph preview image.
- [ ] Add downloadable vCard file instead of copy-only vCard text.
- [ ] Add `robots.txt` and `sitemap.xml` to the repository.
- [ ] Add a lightweight `/assets/` folder only if visual proof is needed.
- [ ] Add a GitHub Actions workflow to run HTML validation and Lighthouse CI.
- [ ] Add a changelog section for SEO/content updates.
- [ ] Track Search Console query data and rewrite sections around real impressions.

---

## Validation workflow

Use this after every meaningful content update:

```bash
# 1. Serve locally
python -m http.server 8080

# 2. Open the local site
# http://localhost:8080

# 3. Check the basics manually
# - links
# - keyboard navigation
# - mobile layout
# - command palette
# - copy buttons
# - theme toggle

# 4. Run optional audits
npx lighthouse http://localhost:8080 --view
```

Then deploy and inspect the live URL in Search Console.

---

## No build step required

This repository deliberately avoids unnecessary complexity. There is no required:

- npm install
- bundler
- framework runtime
- CSS preprocessor
- database
- backend server

That keeps the page portable, fast, easy to host, and simple to debug.

---

## References

- [Google Search Central: SEO Starter Guide](https://developers.google.com/search/docs/fundamentals/seo-starter-guide)
- [Google Search Central: Core Web Vitals and search results](https://developers.google.com/search/docs/appearance/core-web-vitals)
- [web.dev: Web Vitals](https://web.dev/articles/vitals)
- [W3C: WCAG 2.2](https://www.w3.org/TR/WCAG22/)
- [GitHub Docs: Managing a custom domain for GitHub Pages](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [GitHub Docs: Securing GitHub Pages with HTTPS](https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https)

---

## License

Add the correct license for the repository. If this is intended to be open source, consider adding an `MIT`, `Apache-2.0`, or `GPL` license file depending on how you want others to use the work.

---

## Maintainer

**Kai William Piper**  
Creative Technologist — Bournemouth, UK  
GitHub: [@kai9987kai](https://github.com/kai9987kai)
