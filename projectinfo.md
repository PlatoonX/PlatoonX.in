# projectinfo.md — PlatoonX Website Specification

**Status:** Master specification — single source of truth
**Audience:** AI coding agent implementing the site
**Scope:** Static, frontend-only marketing website (Home, About Us, Contact)

This document is self-contained. Where information has not been supplied, it is explicitly marked `[TO BE PROVIDED]`. Do not invent facts to fill these gaps.

---

## 1. Project Overview

- **Company name:** PlatoonX
- **Company type:** AI research startup
- **Primary focus:** Fundamental and applied artificial intelligence research, original AI technologies, and real-world applications
- **Geographic positioning:** India — PlatoonX exists to advance India's AI research capability and technological standing globally
- **Website purpose:** Establish PlatoonX's credibility as a serious AI research organization; communicate its goal, vision, mission, and research direction; open a channel for research, academic, and industry collaboration
- **Target audience:**
  - AI/ML researchers and academics evaluating PlatoonX as a research partner
  - Engineers and researchers considering joining PlatoonX
  - Industry and technology organizations exploring collaboration
  - Journalists, investors, and the broader tech community forming an initial impression
- **Brand positioning:** A research-first AI lab — not a software agency, not a consumer product company, not a generic "AI startup" chasing trends. PlatoonX positions itself closer to a research institute with startup execution speed.
- **Website goals:**
  1. Clearly explain what PlatoonX is and why it exists
  2. Communicate research areas and current work honestly (no overstatement)
  3. Convert interested researchers/partners into contacts
  4. Establish a credible, premium, technically confident visual identity
- **Primary call-to-action:** "Collaborate With Us" → routes to Contact page
- **Secondary calls-to-action:** "Learn About Our Research," "About PlatoonX," "View Research Areas"
- **Overall communication style:** Precise, restrained, confident. Research-institute tone rather than marketing-agency tone. Short declarative sentences. No hype adjectives ("revolutionary," "cutting-edge," "game-changing").

PlatoonX is a research-driven organization advancing AI capability in India — not a generic software development company. All copy must reinforce this distinction.

**Source-of-truth positioning (verbatim):**

> **Goal:** Advance India through world-class AI research, technology, and real-world applications.
>
> **Vision:** To make India a global leader in artificial intelligence research and innovation.
>
> **Mission:** To conduct fundamental and applied AI research, create original AI technologies, and translate research into solutions that address India's scientific, industrial, and societal challenges.

No claims about funding, valuation, customers, partnerships, patents, publications, awards, or employee count are to be introduced anywhere on the site unless explicitly supplied.

---

## 2. Website Architecture

Three initial pages only:

### Home (`/home`)
**Purpose:** Introduce PlatoonX, explain what it does, why AI research matters, and drive collaboration.
**Sections:** Hero → Company introduction → Research areas → Current projects → Research philosophy → Vision/mission → Collaboration CTA → Footer.
**Navigation:** Persistent nav bar; smooth-scroll for in-page anchors where relevant.

### About Us (`/about`)
**Purpose:** Deep dive into identity — goal, vision, mission, philosophy, principles, team.
**Sections:** Introduction → Goal → Vision → Mission → Research philosophy → Research principles → Team (placeholder structure) → Collaboration CTA.

### Contact (`/contact`)
**Purpose:** Route different audiences (research, academia, industry, careers, general) to the correct static contact mechanism.
**Sections:** Contact category cards → `mailto:` links → optional social links → footer.

Global nav: Logo · Home · About Us · Contact · optional CTA pill "Collaborate With Us."

---

## 3. Brand Direction

PlatoonX's visual identity **follows the Stripe-inspired design system** defined in `DESIGN-stripe.md` (reproduced and adapted in Section 4), reinterpreted for an AI-research context rather than a fintech context.

The visual language should communicate:
- Precision and scientific rigor
- Computation, intelligence, research depth
- Confidence without hype
- A premium, editorial, engineering-grade aesthetic (the same register that made the Stripe-style system feel authoritative in fintech, redirected toward AI research)
- India-forward technological ambition — subtle, not flag-waving

**Adaptation notes from the source design system to PlatoonX's domain:**
- Where the original system uses **composited dashboard/payment UI mockups**, PlatoonX substitutes **research-oriented composites**: model architecture diagrams, training-curve charts, code/notebook panels, and abstract vector-field or embedding-space visualizations — rendered in the same faux-IDE / faux-console chrome style, at the same scale and elevation.
- Where the original system uses **tabular figures for money**, PlatoonX uses tabular figures for **research metrics** (parameter counts, benchmark scores, dataset sizes) — same `tnum` treatment, same rationale: a quiet, quantitative signal of technical seriousness.
- The **gradient mesh** remains the signature hero backdrop, but its accompanying imagery leans toward abstract computation (neural connections, gradient fields) rather than financial iconography.
- Pricing-card components from the source system are **not used** (PlatoonX has no pricing) — the underlying card tokens are reused instead for **research-area cards** and **project cards** (see Section 15–16).

Avoid: generic SaaS-template look, crypto-site aesthetics, gaming-site aesthetics, marketing-agency polish with no substance. The bar is "serious research lab," not "startup landing page."

---

## 4. Visual Design System

This system is adapted directly from the supplied `DESIGN-stripe.md`. All tokens below are authoritative — implement exactly.

### 4.1 Typography

**Primary font:** `sohne-var` (proprietary) is the source brand's typeface. Since Sohne is proprietary and unlicensed for PlatoonX, use the documented open-source substitute:

- **Primary font (substitute):** **Inter**, weight 300, loaded via Google Fonts or self-hosted `.woff2`, with `font-feature-settings: "ss01"` applied globally on `<body>`.
- **Fallback stack:** `"Inter", "SF Pro Display", system-ui, -apple-system, sans-serif`
- **Secondary/monospace font:** `"JetBrains Mono", "SF Mono", ui-monospace, monospace` — used for code panels, research-metric labels, and technical composites.
- **Performance note:** Self-host Inter as variable `.woff2` with `font-display: swap` and `<link rel="preload">` for the primary weight to avoid render-blocking and layout shift. Avoid loading more than 2 weights (300, 400) to keep payload small — critical on GitHub Pages with no server-side font optimization.

**Type hierarchy** (identical structure to the source system):

| Token | Size | Weight | Line Height | Letter Spacing | Use |
|---|---|---|---|---|---|
| `display-xxl` | 56px | 300 | 1.03 | -1.4px | Hero headline |
| `display-xl` | 48px | 300 | 1.15 | -0.96px | Section opener |
| `display-lg` | 32px | 300 | 1.1 | -0.64px | Card title / sub-section |
| `display-md` | 26px | 300 | 1.12 | -0.26px | Compact card title |
| `heading-lg` | 22px | 300 | 1.1 | -0.22px | Section title |
| `heading-md` | 20px | 300 | 1.4 | -0.2px | Sub-heading |
| `heading-sm` | 18px | 300 | 1.4 | 0 | Mini-section label |
| `body-lg` | 16px | 300 | 1.4 | 0 | Marketing body lead |
| `body-md` | 15px | 300 | 1.4 | 0 | Default UI body |
| `body-tabular` | 14px | 300 | 1.4 | -0.42px | Numeric/metric data (`tnum`) |
| `button-md` | 16px | 400 | 1.0 | 0 | Pill button label |
| `button-sm` | 14px | 400 | 1.0 | 0 | Compact pill label |
| `caption` | 13px | 400 | 1.4 | -0.39px | Helper text, labels |
| `micro` | 11px | 300 | 1.4 | 0 | Fine print |
| `micro-cap` | 10px | 400 | 1.15 | 0.1px | All-caps eyebrow / tag |

**Principles:**
- Display tiers always render at weight 300 — do not bump to 400+.
- Negative tracking scales from -1.4px (56px) down to -0.2px (20px); this is the typographic signature.
- Any numeric research metric (benchmark score, parameter count, dataset size) uses `font-feature-settings: "tnum"` with tightened tracking (`body-tabular`).
- `font-feature-settings: "ss01"` applied globally on `<body>`.

### 4.2 Color System

| Token | Hex | Role |
|---|---|---|
| `primary` | `#533afd` | Signature CTA/accent indigo — sparing use, one filled button per section |
| `primary-deep` | `#4434d4` | Gradient mid-stop / hover |
| `primary-press` | `#2e2b8c` | Pressed button state |
| `primary-soft` | `#665efd` | Chart/diagram accents |
| `primary-bg-subdued-hover` | `#b9b9f9` | Soft tag background |
| `brand-dark-900` | `#1c1e54` | Deep navy — dashboard-style composite fills, dark surfaces |
| `ink` | `#0d253d` | Default body text |
| `ink-secondary` | `#273951` | Secondary text on white |
| `ink-mute` | `#64748d` | Helper text, captions |
| `ink-mute-2` | `#61718a` | Nav-adjacent muted text |
| `on-primary` | `#ffffff` | Text on indigo/dark surfaces |
| `canvas` | `#ffffff` | Default page background |
| `canvas-soft` | `#f6f9fc` | Feature-band off-white |
| `canvas-cream` | `#f5e9d4` | Warm interlude band (e.g., research-philosophy section) |
| `hairline` | `#e3e8ee` | 1px card/table borders |
| `hairline-input` | `#a8c3de` | Form input borders |
| `ruby` | `#ea2261` | Gradient/accent only — never a button |
| `magenta` | `#f96bee` | Gradient accent |
| `lemon` | `#9b6829` | Warm gradient stop |
| `shadow-blue` | `#003770` | Shadow tint base |

**Usage rules:**
- Indigo (`primary`) is reserved for filled CTAs and inline link emphasis — never used as a body-text color.
- Deep navy (`ink`) is the universal body-text color — never pure black.
- Ruby and magenta live only inside the gradient mesh and as accent dots in diagram composites — never as button fills.
- No new accent colors outside this palette.

### 4.3 Layout

- **Max content width:** ~1200px centered container.
- **Section padding:** 64–96px vertical on marketing sections; tightens to 32–48px on dense/comparison sections (e.g., research-area grid).
- **Card internal padding:** 32px (feature/research/project cards), 24px (composite mockup panels).
- **Border radius scale:**

| Token | Value | Use |
|---|---|---|
| `xs` | 4px | Hairline tags, table chrome |
| `sm` | 6px | Form inputs |
| `md` | 8px | Compact cards, alerts |
| `lg` | 12px | Feature/research/project cards |
| `xl` | 16px | Composite mockup chrome |
| `pill` | 9999px | All buttons, tag pills |

- **Spacing scale:** `xxs` 2px · `xs` 4px · `sm` 8px · `md` 12px · `lg` 16px · `xl` 24px · `xxl` 32px · `huge` 64px.
- **Grid behavior:** Research-area and project cards use a 3-up grid at desktop, collapsing to 2-up at tablet (768–1023px) and 1-up at mobile (<768px), matching the source system's pricing-grid collapse pattern.
- **Elevation:**
  - Level 0: flat (default surface)
  - Level 1: `box-shadow: rgba(0,55,112,0.08) 0 1px 3px` — card lift on white
  - Level 2: `box-shadow: rgba(0,55,112,0.08) 0 8px 24px, rgba(0,55,112,0.04) 0 2px 6px` — floating panels, composite mockup chrome
  - Level 3: gradient mesh backdrop — the brand's primary depth medium

### 4.4 Components (reused/relabeled from the source system)

- **`button-primary-pill`** — bg `primary`, text `on-primary`, `button-md` type, padding `8px 16px`, `pill` radius. Pressed state → `primary-press`.
- **`button-secondary`** — bg `canvas`, text `primary`, 1px `primary` border, same pill geometry.
- **`button-on-dark`** — bg `brand-dark-900`, text `on-primary`, same pill geometry — used on dark composite/footer bands.
- **`card-feature-light`** — bg `canvas`, padding 32px, `lg` radius, 1px `hairline` border, optional Level 1 shadow. Used for research philosophy/principles blocks.
- **`card-research-area`** *(relabeled from `card-pricing`)* — bg `canvas`, padding 32px, `lg` radius, 1px `hairline` border; title `heading-lg`, body `body-md`, optional `micro-cap` tag.
- **`card-project`** *(relabeled from `card-pricing`)* — same structure as `card-research-area`, plus a status pill (`pill-tag-soft`) and "Learn more" link (`link-on-light`).
- **`card-cream-band`** — bg `canvas-cream`, text `ink`, padding 32px, `lg` radius — used for the Research Philosophy interlude section.
- **`card-composite-mockup`** *(relabeled from `card-dashboard-mockup`)* — bg `canvas`, `body-tabular` type, padding 24px, `xl`/`lg` radius, Level 2 shadow. Houses a code-panel + architecture-diagram + metrics-chart composite.
- **`text-input`** / **`text-input-focused`** — bg `canvas`, text `ink`, `body-md`, padding `8px 12px`, `sm` radius, `hairline-input` border → focus swaps border to `primary`. *(Only relevant if a static form service is added later per Section 19.)*
- **`nav-bar-on-mesh`** — bg `canvas` or transparent-over-mesh depending on scroll, text `ink`, padding `16px 24px`. Logo left, nav center, CTA pill right.
- **`pill-tag-soft`** — bg `primary-bg-subdued-hover`, text `primary-deep`, `micro-cap` type, padding `4px 8px`, `pill` radius. Used for research-area tags and project status labels.
- **`link-on-light`** — text `primary`, `body-md`, no underline by default, underline on hover/focus.
- **`footer-light`** — bg `canvas`, text `ink-mute`, `caption` type, padding `64px 24px`.

### 4.5 Signature Components

- **Gradient Mesh Backdrop** — pastel cream → sherbet orange → lavender → indigo → ruby pink, blurred horizontally across the upper third of the Home hero. Implemented as SVG or a large optimized background image (WebP), not a flat CSS gradient — organic blob shapes are not achievable with CSS gradients alone. Non-negotiable on the Home hero; may appear more subtly on About/Contact headers.
- **Composited Research Mockup** — the AI-research equivalent of the source system's dashboard composite: a code/notebook panel, a model-architecture or embedding diagram, and a metrics/benchmark chart card, composited at small scale inside `xl`/`lg`-radius containers with Level 2 shadow. This is the site's signature "look at the actual work" visual, used near the Research Areas and Current Projects sections.
- **Tabular-Figure Metric Type** — every research metric (params, benchmark %, dataset size) renders with `tnum`.

### 4.6 Do's and Don'ts

**Do**
- Reserve `primary` for filled CTAs and inline emphasis — one filled button per section band.
- Apply the gradient mesh to the Home hero.
- Render display tiers at weight 300 with negative tracking.
- Use `tnum` on every numeric research metric.
- Apply `ss01` globally on `<body>`.
- Pair research/project claims with a composited visual, never a bare claim.

**Don't**
- Don't bump display weight above 300.
- Don't introduce accent colors outside the documented palette.
- Don't use indigo as body-text color.
- Don't shrink button padding below `8px 16px`.
- Don't render metrics without `tnum`.
- Don't replace the pill button shape with rounded rectangles.
- Don't fabricate benchmark numbers, metrics, or composite content that implies unpublished results.

---

## 5. Futuristic UI Elements

Subtle, professional-only:
- Gradient mesh backdrop (Home hero; lighter variant on About/Contact headers)
- Composited research-mockup panels with faint animated gradient glow (CSS only, low-opacity, slow)
- Scroll-triggered fade-up reveals on section entry (`IntersectionObserver`)
- Magnetic/hover lift on `button-primary-pill` and cards (small `transform: translateY(-2px)` + shadow increase)
- Animated underline on `link-on-light` on hover/focus
- Subtle animated border-glow on the active nav item

All effects must degrade gracefully and never block readability, scrolling, or keyboard navigation.

---

## 6. Animation System

**Page load:** Logo fade/slide-in (200ms), hero headline reveal (staggered line reveal via `opacity`/`transform`, 400–600ms), CTA fade-in after hero text, gradient mesh fades in first (it's the backdrop).

**Scroll:** Fade-up on section entry (`opacity: 0→1`, `transform: translateY(16px)→0`), staggered card entrance (80–120ms stagger per card), no parallax beyond a very subtle mesh drift (optional, disable under reduced motion).

**Hover:** Buttons lift + background shift; nav links get animated underline; research/project cards lift with Level 1→2 shadow transition; contact category cards highlight border color to `primary`.

**Page transitions:** Lightweight CSS-only cross-fade (150–200ms) between Home/About/Contact. No heavy page-transition library (e.g., no full-page wipe animations, no JS-driven route morphing).

**Implementation constraints:** CSS transitions/keyframes, `IntersectionObserver` for scroll reveals, `transform`/`opacity` only for animated properties (GPU-accelerated, no layout thrashing). All animations must respect `prefers-reduced-motion: reduce` by disabling non-essential motion.

---

## 7. Performance Requirements

- Static HTML/CSS/JS only — no server-side processing.
- Minimal JavaScript; no heavy animation frameworks (no GSAP-scale dependency unless explicitly justified — plain CSS/JS is sufficient for this scope).
- No API requests, no database calls, no runtime backend dependency.
- Lazy-load below-the-fold images and composite mockup assets.
- Images compressed and served as WebP/AVIF with a fallback where needed.
- Minimize JS bundle size; avoid render-blocking `<script>`/`<link>` — defer non-critical JS, preload critical fonts only.
- Use GPU-friendly animated properties (`transform`, `opacity`) exclusively.
- No large background videos, no heavy 3D scenes, no large animation libraries.

**Targets:** Lighthouse Performance ≥ 90, Accessibility ≥ 90, Best Practices ≥ 90, SEO ≥ 90. Fast first contentful paint, minimal CLS, minimal main-thread JS work.

Visual richness (gradient mesh, composites, animation) must never come at the cost of these targets — if a tradeoff arises, performance wins.

---

## 8. GitHub Pages Requirements

- **Hosting:** Static hosting via GitHub Pages (project or user/org site).
- **Repository structure:** See Section 25.
- **Build/deploy:** Static build output (from the chosen framework, Section 9) committed to a `gh-pages` branch or `/docs` folder, or deployed via a GitHub Actions workflow (`actions/deploy-pages`).
- **Paths:** All asset references must use relative or base-path-aware paths (respect the repo's `base` config if deployed to a project subpath, e.g., `username.github.io/platoonx/`).
- **Routing:** Since this is a 3-page static site with no dynamic routes, no SPA fallback/rewrite complexity is needed — each page can build to its own static HTML file (`/`, `/about/index.html`, `/contact/index.html`) for clean GitHub Pages compatibility without a router-based 404 workaround.
- **Custom domain (if used):** `CNAME` file at repo root — `[TO BE PROVIDED]` if a custom domain is intended.

---

## 9. Technology Recommendation

**Recommended stack: Astro** (with vanilla CSS or a lightweight utility layer), static output.

**Why Astro over alternatives:**
- **vs. plain HTML/CSS/JS:** Astro gives component reuse (nav, footer, cards) and content structure without sacrificing static output — reduces duplication across 3 pages while staying zero-JS-by-default on the client.
- **vs. React (CRA/plain):** Astro ships zero JavaScript by default and only hydrates interactive islands (e.g., mobile menu, scroll-reveal script) — dramatically better for the strict performance targets in Section 7 than a full React SPA bundle.
- **vs. Next.js static export:** Next.js's static export works but carries React-runtime weight even for static pages unless carefully tree-shaken; Astro is purpose-built for exactly this "mostly-static, a little interactivity" profile and produces smaller bundles out of the box.
- **vs. Vite + vanilla:** Viable alternative if the team prefers zero framework overhead at all; Astro is preferred here because it still supports component-based page composition (useful given repeated card/section patterns) while compiling to the same static output profile.

Astro builds directly to static `dist/` files fully compatible with GitHub Pages, supports partial hydration for the few interactive elements (mobile nav, scroll-reveal, magnetic hover), and has first-class Markdown/content support useful for future pages (Research, Blog, Publications — Section 32).

---

## 10. SEO Specification

### Metadata

| Page | Title | Meta Description |
|---|---|---|
| Home | PlatoonX — AI Research for India | PlatoonX is an AI research startup advancing India through fundamental and applied artificial intelligence research, original AI technologies, and real-world applications. |
| About Us | About PlatoonX — Our Goal, Vision & Mission | Learn about PlatoonX's mission to conduct world-class AI research and build original technologies that address India's scientific, industrial, and societal challenges. |
| Contact | Contact PlatoonX — Research & Partnership Enquiries | Reach PlatoonX for research collaboration, academic partnerships, industry collaboration, or career enquiries. |

### Keywords (natural usage only, no stuffing)
PlatoonX, AI research India, artificial intelligence research, AI technology India, AI innovation, AI research startup, fundamental AI research, applied AI research, original AI technologies, AI research collaboration India.

### Open Graph
`og:title`, `og:description` (mirror the table above per page), `og:image` (a dedicated 1200×630 social card using the gradient-mesh brand treatment — `[TO BE PROVIDED]` asset), `og:url` (canonical per-page URL), `og:type` = `website`, `og:site_name` = `PlatoonX`.

### Twitter/X
`twitter:card` = `summary_large_image`, `twitter:title`, `twitter:description`, `twitter:image` (reuse OG image).

### Structured Data (Schema.org, JSON-LD)
- `Organization` on Home — name, url, logo, `sameAs` (only official links that exist).
- `WebSite` on Home — name, url.
- `AboutPage` on About Us.
- `ContactPage` on Contact.

Do not populate `foundingDate`, `numberOfEmployees`, `award`, or similar fields unless supplied — omit rather than guess.

### Search Engine Files
- `robots.txt` — allow all, reference sitemap.
- `sitemap.xml` — 3 URLs (Home, About, Contact), auto-generated at build time.
- Canonical `<link rel="canonical">` per page.
- Favicon set (`favicon.ico`, `apple-touch-icon.png`, SVG favicon) — `[TO BE PROVIDED]` brand mark.
- `site.webmanifest` for PWA-lite metadata (name, short_name, icons, theme_color `#533afd`, background_color `#ffffff`).

---

## 11. Accessibility

- Semantic HTML throughout (`<nav>`, `<main>`, `<section>`, `<footer>`, proper `<h1>`–`<h3>` hierarchy per page, one `<h1>` per page).
- Full keyboard navigation for nav, mobile menu, and all interactive elements.
- Visible focus states on all interactive elements (`:focus-visible` outline in `primary` or a high-contrast equivalent — never `outline: none` without a replacement).
- Text/background contrast meets WCAG AA minimum (verify `ink-mute` on `canvas` and `on-primary` on `primary` specifically).
- Descriptive `alt` text on all meaningful images; empty `alt=""` on decorative composites.
- Accessible, labeled buttons/links (no bare icon buttons without `aria-label`).
- `prefers-reduced-motion: reduce` disables scroll-reveal transforms, mesh drift, and hover-lift animations — content remains fully visible without motion.
- Screen-reader-friendly nav with proper `aria-expanded` on the mobile menu toggle.
- No information conveyed by animation alone (e.g., status pills must carry text, not just color/motion).

---

## 12. Responsive Design

| Breakpoint | Width | Key Behavior |
|---|---|---|
| Wide | ≥ 1440px | Full gradient mesh edge-to-edge; composite mockup at full multi-panel scale |
| Desktop | 1024–1440px | Default 1200px container; research/project grid 3-up |
| Tablet | 768–1023px | Grid 2-up; composite mockup simplifies to 2 panels |
| Mobile | < 768px | Grid 1-up; hamburger nav; display type steps down 56→36px; composite mockup simplifies to a single panel |

- **Navigation:** Full horizontal nav ≥1024px; hamburger + slide/fade menu below.
- **Typography scaling:** Display tiers stair-step 56 → 48 → 32 → 26 → 22px across breakpoints.
- **Hero layout:** Stacks vertically on mobile; CTA buttons full-width or comfortably tappable (≥44×44px).
- **Footer:** Multi-column at desktop, stacked single-column at mobile.

Mobile is treated as a first-class design target, not a shrunk desktop layout — hero copy length, card density, and composite complexity are all authored for mobile legibility, not just scaled down.

---

## 13. Navigation

- Logo (PlatoonX wordmark) — left.
- Home · About Us · Contact — center/left-aligned per `nav-bar-on-mesh`.
- Optional CTA pill "Collaborate With Us" — right, `button-primary-pill`.
- **Sticky/fixed:** Nav is sticky; background transitions from transparent (over the Home gradient mesh) to solid `canvas` with a `hairline` bottom border once scrolled past the hero.
- **Mobile menu:** Hamburger icon → full-screen or slide-down overlay on `canvas`, with the same nav items stacked, large tap targets.
- **Active-page indication:** Current page nav item shown in `primary` color with a small underline/dot indicator.
- **Smooth scrolling:** Enabled for in-page anchors (e.g., Home → Research Areas).
- **Keyboard accessibility:** Full tab order, `Escape` closes the mobile menu, focus trapped within an open mobile menu.

---

## 14. Home Page Content Specification

| Section | Purpose | Heading (draft) | Supporting Text | CTA | Visual | Animation | Mobile Behavior |
|---|---|---|---|---|---|---|---|
| Hero | Answer "What is PlatoonX?" | "Advancing India through world-class AI research." | One–two sentences restating the Goal in plain language. | "Collaborate With Us" (primary), "About PlatoonX" (secondary) | Gradient mesh backdrop + optional abstract computation graphic | Staggered text reveal, mesh fade-in | Stacked, mesh simplifies, CTAs stack vertically |
| Company Introduction | Explain what PlatoonX does | "A research-first AI lab" | Short paragraph: fundamental + applied research, original technologies, real-world translation. | — | None or a simple icon row | Fade-up on scroll | Single column |
| Research Areas | Show research focus | "Where we focus our research" | Intro line; then grid of `card-research-area` (Section 15) | — | Card grid | Staggered card fade-up | 1-up stack |
| Current Projects | Show active work | "Current research & projects" | Intro line; then grid of `card-project` (Section 16) | "Learn more" per card (if linkable) | Composited research mockup + card grid | Staggered card fade-up | 1-up stack |
| Research Philosophy | Communicate approach/values | "How we do research" | Philosophy points (Section 17) | — | `card-cream-band` interlude | Fade-up | Stacked |
| Vision/Mission Summary | Reinforce identity | "Our goal, vision, and mission" | Verbatim Goal/Vision/Mission | "Read more" → About | Simple typographic layout, no imagery needed | Fade-up | Stacked |
| Collaboration CTA | Convert to contact | "Let's build India's AI future together" | One-line invitation | "Get in Touch" (primary) | Optional light mesh echo | Fade-up + button hover lift | Full-width CTA band |
| Footer | Navigation + contact | — | Section 20 | — | — | None | Stacked columns |

---

## 15. AI Research Areas

Include only areas that plausibly fit PlatoonX's actual direction. Suggested categories (confirm before publishing):

- Machine Learning
- Deep Learning
- Generative AI
- Multimodal AI
- Computer Vision
- Natural Language Processing
- AI Agents
- Edge AI
- Scientific AI
- Physical AI

Each rendered as a `card-research-area`:
- Short description (1–2 sentences, non-committal about completed results)
- `pill-tag-soft` label (area name)
- Hover: Level 0→1 shadow lift, subtle border color shift to `primary`
- Optional technical keyword row in `micro` type

**Governance:** These categories are directional/aspirational unless PlatoonX confirms which are active. Mark unconfirmed categories `[TO BE CONFIRMED]` internally before launch; do not present all ten as simultaneously active without confirmation.

---

## 16. Current Projects

`card-project` structure — extensible list, currently empty of real data:

- Project name — `[TO BE PROVIDED]`
- One-line description — `[TO BE PROVIDED]`
- Research area (tag, references Section 15 categories)
- Status (`pill-tag-soft`: e.g., "In Research," "Early Stage," "Exploratory" — only real statuses, no fabricated "Live" claims)
- Technology — `[TO BE PROVIDED]`
- Research objective — `[TO BE PROVIDED]`
- "Learn more" link — disabled/hidden state if no destination exists yet

If no real projects are supplied at launch, render a clean placeholder state (e.g., "Project details coming soon" card) rather than inventing project names or outcomes.

---

## 17. Research Philosophy

Presented in a `card-cream-band` interlude section. Tone covers:
- Scientific rigor
- Original research over derivative work
- Balance of fundamental and applied AI
- Reproducibility
- Responsible AI development
- Real-world impact
- Building Indian technological capability
- Open scientific thinking
- Long-term research horizon over short-term hype

No claims of specific publications, laboratories, patents, or named institutional partnerships unless supplied.

---

## 18. About Page Content

1. **Introduction** — who PlatoonX is, one paragraph.
2. **Goal** — verbatim from Section 1.
3. **Vision** — verbatim from Section 1.
4. **Mission** — verbatim from Section 1.
5. **Research Philosophy** — Section 17 content, expanded.
6. **Research Principles** — a short bulleted list distilled from the philosophy (e.g., rigor, originality, responsibility, impact).
7. **Team** — placeholder grid structure (avatar placeholder, name placeholder, role placeholder) — do not invent names; render clearly as "Team information coming soon" if empty.
8. **Collaboration CTA** — same treatment as Home's CTA band.

---

## 19. Contact Page

Four distinct static pathways, each its own card/section:

| Pathway | Audience | Mechanism |
|---|---|---|
| Research Collaboration | Researchers, universities, research orgs | `mailto:research@platoonx.[tld]` — `[TO BE PROVIDED]` |
| Industry Partnerships | Organizations seeking AI collaboration | `mailto:partnerships@platoonx.[tld]` — `[TO BE PROVIDED]` |
| Careers | Researchers, engineers, interns | `mailto:careers@platoonx.[tld]` — `[TO BE PROVIDED]` |
| General Enquiries | Everyone else | `mailto:hello@platoonx.[tld]` — `[TO BE PROVIDED]` |

No backend-dependent contact form. Each pathway is a clean `card-feature-light` with a heading, one-line description, and a `button-primary-pill` or `link-on-light` styled `mailto:` action. LinkedIn/GitHub links included only if officially confirmed — `[TO BE PROVIDED]`.

An optional static form service (e.g., Formspree, a GitHub-Pages-compatible form backend) may be added **only if explicitly requested later** — not part of this initial build.

---

## 20. Footer

- PlatoonX logo/name + one-line description
- Navigation column (Home / About / Contact)
- Research column (placeholder for future Research/Projects pages, Section 32)
- Contact column (email links per Section 19)
- GitHub link — `[TO BE PROVIDED]` if an official org account exists
- LinkedIn link — `[TO BE PROVIDED]` if an official account exists
- Copyright line: "© [year] PlatoonX. All rights reserved."
- Privacy Policy link — omitted entirely unless a real policy document exists

Do not fabricate social account links.

---

## 21. Microinteractions

| Element | Hover | Focus | Active | Disabled |
|---|---|---|---|---|
| `button-primary-pill` | Lift + bg → `primary-deep` | Visible outline ring | bg → `primary-press` | Reduced opacity, no pointer |
| `button-secondary` | bg tint shift | Visible outline ring | border deepens | Reduced opacity |
| Nav links | Animated underline | Outline ring | `primary` text | — |
| Research/Project cards | Lift + shadow L0→L1 | Outline ring on focusable child | Slight scale-down on click | — |
| `link-on-light` | Underline appears | Outline ring | Color deepens | — |
| Footer links | Color → `primary` | Outline ring | — | — |
| Contact cards | Border → `primary` | Outline ring | Slight scale-down | — |

---

## 22. Loading Strategy

- Critical CSS inlined for above-the-fold hero (Astro handles this well by default).
- Fonts: preload Inter 300 `.woff2`, `font-display: swap`.
- Images: lazy-load below-the-fold; hero mesh/composite images eagerly loaded but optimized/compressed.
- JavaScript: deferred, minimal — only mobile-menu toggle and scroll-reveal observer logic hydrated as Astro islands.
- No artificial loading screen/splash animation — the site should render its real content as fast as possible; no fake "loading AI…" delays.

---

## 23. Security

- No secrets, API keys, or credentials in frontend code (there is no backend to key into).
- No unnecessary third-party scripts — only Google Fonts (or self-hosted fonts, preferred) and no tracking scripts unless Section 24 conditions are met.
- Dependency minimization — audit `package.json` for unused packages before each release.
- All external links (GitHub, LinkedIn, mailto) use safe attributes (`rel="noopener noreferrer"` on `target="_blank"` links).
- Basic Content-Security-Policy consideration via `<meta http-equiv="Content-Security-Policy">` restricting script/style sources where GitHub Pages allows.

---

## 24. Analytics

Not included by default. Analytics is an optional future feature. If added later, it must be lightweight and privacy-conscious (e.g., a cookieless, GDPR-friendly analytics script) — no heavy tag-manager stacks.

---

## 25. File and Repository Structure

```
platoonx-website/
├── public/
│   ├── favicon.ico
│   ├── apple-touch-icon.png
│   ├── site.webmanifest
│   ├── robots.txt
│   └── og-image.jpg
├── src/
│   ├── components/
│   │   ├── Nav.astro
│   │   ├── Footer.astro
│   │   ├── Button.astro
│   │   ├── ResearchAreaCard.astro
│   │   ├── ProjectCard.astro
│   │   ├── CompositeResearchMockup.astro
│   │   └── GradientMesh.astro
│   ├── layouts/
│   │   └── BaseLayout.astro
│   ├── pages/
│   │   ├── index.astro          (Home)
│   │   ├── about.astro
│   │   └── contact.astro
│   ├── styles/
│   │   ├── tokens.css           (colors, type, spacing, radius variables)
│   │   └── global.css
│   └── content/
│       └── (future: research-areas.json, projects.json for extensibility)
├── astro.config.mjs
├── package.json
├── .github/
│   └── workflows/
│       └── deploy.yml           (GitHub Actions → GitHub Pages)
└── README.md
```

---

## 26. Code Quality Requirements

- Clean, reusable Astro components (one component per UI concern).
- Semantic HTML; no `<div>` soup where a semantic tag exists.
- Clear, consistent naming (`ResearchAreaCard`, not `Card2`).
- No unnecessary abstraction for a 3-page site — keep it simple.
- Responsive CSS via the token system in Section 4, not one-off magic numbers.
- No inline styles except where a computed/dynamic value genuinely requires it.
- No dead code, unused components, or unused dependencies at release.
- Zero console errors/warnings in production build.
- No broken internal or external links (verify before launch).

---

## 27. Browser Support

Modern evergreen browsers: Chrome, Edge, Firefox, Safari, Mobile Safari, Android Chrome. Decorative animations (mesh drift, hover-lift) degrade gracefully (no motion, static fallback) on browsers/contexts that don't support the relevant CSS/JS features — never a broken layout.

---

## 28. Performance Testing (Launch Checklist)

- [ ] Lighthouse run (mobile + desktop) meets Section 7 targets
- [ ] Accessibility audit (axe or Lighthouse a11y pass ≥ 90)
- [ ] SEO audit (Lighthouse SEO pass ≥ 90)
- [ ] Broken-link check across all 3 pages
- [ ] Zero console errors in production build
- [ ] Responsive check at 375 / 768 / 1024 / 1440px
- [ ] GitHub Pages production URL smoke test (not just local build)
- [ ] `prefers-reduced-motion` verified (animations disable correctly)

---

## 29. SEO Content Rules

- Copy clearly and honestly describes PlatoonX.
- Natural AI-research terminology — no keyword stuffing.
- No unsupported claims (funding, customers, results).
- Descriptive `<h1>`–`<h3>` headings per page; one `<h1>`.
- Concise, unique meta descriptions per page (Section 10).
- Consistent company terminology throughout ("PlatoonX," not alternating names).
- Research areas (aspirational/ongoing) clearly distinguished from completed projects (Section 16) in wording — avoid implying finished work where none is confirmed.

---

## 30. Design Rules

### Do
- Use the restrained gradient-mesh + indigo/navy system defined in Section 4.
- Use smooth, GPU-friendly animation only.
- Prioritize readability and performance over decoration.
- Use precise, research-oriented language.
- Keep navigation to 3 items + CTA.
- Make content scannable (short paragraphs, clear headings).

### Don't
- No excessive neon/glow effects beyond the documented mesh and subtle hover states.
- No large video backgrounds.
- No unnecessary 3D scenes.
- No heavy JS animation libraries.
- No fake statistics, invented partnerships, employees, publications, or "production-ready" claims without evidence.
- No pages beyond Home/About/Contact at this stage.
- No backend-dependent functionality (live forms, auth, CMS).

---

## 31. Content Governance

Requires explicit confirmation before publication:
- Team member names/photos/roles
- Email addresses (Section 19 addresses are placeholders — confirm real inboxes before launch)
- Social links (GitHub, LinkedIn)
- Project names/descriptions/status
- Research results or benchmark claims
- Publications
- Partnerships
- Funding information
- Awards
- Company registration details
- Office address
- Careers listings/roles

Use `[TO BE PROVIDED]` markers for all of the above until confirmed; never fabricate placeholders that read as real data.

---

## 32. Future Extensibility

Architecture must allow future pages without rework:
- `/research` — deep dive per research area
- `/projects` — full project index
- `/publications`
- `/careers`
- `/blog`
- `/open-source`
- `/news`

Enabled by: the Astro `src/pages/` file-based routing, the `src/content/` structure reserved for future collections (research-areas.json, projects.json), and the footer's "Research" column already scaffolded (Section 20). None of these pages are implemented now.

---

## 33. Final Acceptance Criteria

The website is complete when:

- [ ] Home page implemented per Section 14
- [ ] About page implemented per Section 18
- [ ] Contact page implemented per Section 19
- [ ] Fully responsive per Section 12
- [ ] Deploys and runs correctly on GitHub Pages (Section 8)
- [ ] No backend of any kind is required
- [ ] No API keys or secrets are exposed
- [ ] SEO metadata present on all pages (Section 10)
- [ ] `sitemap.xml` and `robots.txt` present
- [ ] Open Graph + Twitter metadata present
- [ ] Accessibility requirements met (Section 11)
- [ ] `prefers-reduced-motion` support implemented
- [ ] Animations are smooth and GPU-friendly, causing no jank
- [ ] No unnecessary dependencies remain in `package.json`
- [ ] No broken links anywhere on the site
- [ ] Zero console errors
- [ ] Lighthouse scores ≥ 90 across all four categories
- [ ] Mobile performance and layout verified as first-class (not shrunk desktop)
- [ ] All company claims trace back to Section 1's verbatim Goal/Vision/Mission — nothing fabricated
- [ ] All placeholder/unconfirmed information is clearly marked `[TO BE PROVIDED]`
- [ ] The site communicates PlatoonX as a serious AI research organization advancing India — not a generic software company
- [ ] Visual system matches Section 4 (Stripe-inspired tokens) exactly — colors, type scale, radii, spacing, components

# Logo
use logo from /logo
BGR - PlatoonX - black.png black theme
BGR - PlatoonX - white.png white theme
main logo BGR-PlatoonX - main.png (tab)