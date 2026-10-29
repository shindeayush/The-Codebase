# Tailwind CSS Roadmap: From Zero to Responsive Interfaces and Design Systems

*Created: 29 October 2026 · Tailwind CSS v4 track · 7 weeks · 42 sessions · approximately 133 guided hours*

## Start here

This standalone roadmap takes you from basic HTML/CSS to building **responsive, accessible and maintainable interfaces with Tailwind CSS v4**. It follows the same **Learn → Build → Done When** format as the Java, Go, C++, Bootstrap and other roadmaps in this collection. Your final outcome is a deployable multi-page website and a reusable CSS-first design system.

Tailwind is a **utility-first CSS framework**, not an interactive component library, a JavaScript framework, or a back end. You use classes for styling; HTML semantics, JavaScript, native browser controls or an accessible component library must supply behavior. You do **not** need to learn React first.

**Prerequisites:** HTML tags and forms; elementary CSS selectors, box model, Flexbox, Grid and responsive design; elementary JavaScript for the interactive sections. If you are new to CSS, do the optional bridge sessions before Day 1. Learning Tailwind does **not** replace learning CSS.

**By the end:** A Git repository with all exercises, a `journal.md`, seven weekly deliverables, two formal checkpoints, screenshots/QA notes, build instructions and one publishable capstone. Treat each "Day" as one **study session**, not necessarily a calendar day.

### Working on Windows, Linux and macOS

| Operating system | Terminal/editor | Notes |
|---|---|---|
| Windows 10/11 | PowerShell or Windows Terminal; VS Code | Native Windows is supported; no WSL required. Use forward slashes in npm commands and normal Windows filesystem paths. |
| Linux | Bash/Zsh; VS Code | Install Node.js and Git using their official/recommended methods. A browser is needed for responsive testing. |
| macOS | Terminal/Zsh; VS Code | Use a supported Node.js installation and a modern browser with DevTools. |

Install a **currently supported Node.js LTS** and Git; check that your installed versions satisfy Vite's requirements (Vite can change its minimum Node version). Run `node --version`, `npm --version` and `git --version`. Install the VS Code **Tailwind CSS IntelliSense** extension if available, and learn how to inspect CSS in your browser's DevTools. Pin dependency versions through your `package-lock.json` and commit it.

### Recommended setup A — Vite + Tailwind CSS v4

This is the recommended path for the main roadmap. The commands work in PowerShell, Bash and Zsh:

```sh
npm create vite@latest tailwind-roadmap -- --template vanilla
cd tailwind-roadmap
npm install
npm install tailwindcss @tailwindcss/vite
```

Edit `vite.config.js` to include the Tailwind Vite plugin:

```js
import { defineConfig } from 'vite'
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
  plugins: [tailwindcss()],
})
```

In `src/style.css` (or the CSS file your Vite starter imports), replace the starter CSS with:

```css
@import "tailwindcss";
```

Ensure the starter's `src/main.js` imports `./style.css`. Place this in `index.html` inside `<body>`:

```html
<main class="mx-auto max-w-3xl px-4 py-16">
  <h1 class="text-4xl font-bold tracking-tight">Hello Tailwind</h1>
  <p class="mt-4 text-slate-700">My first utility-first page.</p>
  <a href="#practice" class="mt-6 inline-block rounded-lg bg-indigo-600 px-5 py-3 font-semibold text-white hover:bg-indigo-700 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">
    Start practising
  </a>
  <section id="practice" class="mt-12"><h2 class="text-2xl font-semibold">Practice</h2></section>
</main>
```

Run:

```sh
npm run dev
```

Visit the local URL printed by Vite and confirm the heading is large, the link has a colored background and the page remains readable on a phone-sized viewport.

### Alternative setup B — Plain HTML + Tailwind CLI

If you want a framework-free, build-to-CSS workflow, use the separate v4 CLI package:

```sh
mkdir tailwind-cli-lab
cd tailwind-cli-lab
npm init -y
npm install tailwindcss @tailwindcss/cli
```

Create `src/input.css` with `@import "tailwindcss";`. Create `src/index.html` and link the generated stylesheet with `<link href="./output.css" rel="stylesheet">`. Keep a terminal running:

```sh
npx @tailwindcss/cli -i ./src/input.css -o ./src/output.css --watch
```

Open `src/index.html` in a browser, or use a local static server. This produces CSS at build time; you are not required to load Tailwind from a runtime CDN. **Do not confuse Tailwind v4 with older tutorials:** the CLI package is `@tailwindcss/cli`, Vite uses `@tailwindcss/vite`, and a `tailwind.config.js` file or `npx tailwindcss init -p` is **not required** for the normal v4 CSS-first workflow.

### Optional foundation bridge — four extra sessions (not counted among the 42)

| Prep | Learn | Build | Done when |
|---|---|---|---|
| P1 | HTML documents, semantic elements, form labels, links, tables and images. | One plain HTML landing page without CSS. | Heading order is logical; navigation and form labels make sense. |
| P2 | CSS selectors, cascade, specificity, computed styles and the box model. | Hand-code two cards with CSS. | Explain how padding, margin and border affect total dimensions. |
| P3 | Flexbox, Grid, media queries, responsive viewport and DevTools. | Make a two-column layout collapse to one column. | It works at 320 px and 1280 px with no horizontal scrollbar. |
| P4 | Basic JS events, DOM, Git, terminal and browser debugging. | Make a working disclosure button and commit it. | Clicking and pressing Enter/Space work and state is visible. |

### How a session works

Five sessions each week take roughly **3 hours**. The sixth is a **4-hour project/review**. That is `5 × 3 + 4 = 19 hours/week`, or about **133 hours over seven weeks**.

| Minutes | Step | What you do |
|---:|---|---|
| 10 | Start | Re-type a utility or reproduce a layout detail from memory; review the previous `journal.md` entry. |
| 40 | Learn | Read the listed Tailwind topic in the official docs, and inspect what the resulting CSS does. |
| 90 | Build | Write the exercise without copying a complete solution. Work mobile-first. |
| 30 | Break it | Introduce one layout, state, class-scanning or keyboard bug, diagnose it in DevTools, then fix it. |
| 10 | Save | Run the relevant build/QA check, commit changes and record **learned / confused / next step**. |

**Completion rule:** A session counts only when you demonstrate the **Done when** condition, explain the choices, and commit the work. On review days, build a small cohesive project rather than collecting disconnected snippets. If a checkpoint fails, repeat the weak exercises before progressing.

---

## Complete session roadmap

### Week 1: Days 1–6 — HTML, CSS, and the utility-first mental model

**Weekly deliverable:** A small, mobile-first personal profile page and product-card gallery.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | How Tailwind v4 works: utilities, scanning, generated CSS, Preflight and where CSS still matters. | Set up Vite and add a semantic profile page; style one heading, paragraph and action link. | `npm run dev` serves the page; generated styles work; you can explain the build pipeline. |
| 2 | Spacing and sizing: padding, margin, gap, width, max-width, min-height, box model, `mx-auto`. | Recreate a measured card mockup without inline styles; compare spacing at narrow/wide viewports. | Card dimensions and whitespace match your measurements; no accidental horizontal scrolling. |
| 3 | Typography: font family, weight, line height, tracking, text wrapping and hierarchy. | Create a type specimen with page title, section headings, prose, labels and fine print. | The page is readable at 200% zoom with no clipped or overlapping text. |
| 4 | Colors, backgrounds, borders, ring, radius, shadows and contrast. | Build four product cards with consistent image, copy, badges and calls to action. | Cards communicate states without color alone and text remains legible. |
| 5 | CSS fundamentals behind utility classes: display, cascade, specificity, computed styles, Preflight. | Reproduce a layout first in plain CSS and again with utilities; inspect both in DevTools. | You can explain five utility-to-CSS mappings and identify where a reset changed defaults. |
| 6 | **Project and review** — reproduce a design by eye, test widths and explain the utility-first approach. | **Profile and product gallery:** hero, short bio, responsive cards, focusable navigation and footer. | No horizontal overflow at 320/375/768/1280 px; keyboard navigation works; commit and tag `tw-w1`. |

**Weekly review questions:** What CSS rules do these classes generate? Which breakpoint or state caused the hardest bug? Does the layout work with long text, keyboard-only input and zoom? What evidence proves the deliverable works?

### Week 2: Days 7–12 — Responsive layouts and composition

**Weekly deliverable:** A polished, mobile-first marketing landing page with an adaptive product grid.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Mobile-first variants and breakpoints: unprefixed utilities, `sm:`, `md:`, `lg:` and `xl:`. | Build a one/two/three-column catalog and write down the breakpoint behavior before testing. | A mobile-first layout behaves intentionally at 320, 640, 768, 1024 and 1440 px. |
| 8 | Flexbox: axes, wrapping, `justify-*`, `items-*`, grow/shrink and overflow. | Implement responsive navigation links, pricing row and a media object. | Alignment survives long labels and a 200% zoom view. |
| 9 | Grid: explicit columns, spans, gaps, auto-flow and responsive card composition. | Create a feature area with one featured card and six equal cards; avoid fragile fixed heights. | Cards preserve reading order and never overlap at target viewport sizes. |
| 10 | Position, sticky, z-index, overflow and stacking contexts. | Make a sticky page header, an in-page jump menu and a notification chip. | Anchored headings are visible, focus is not hidden and there is no unintended clipping. |
| 11 | Images and media: `object-cover`, aspect ratio, responsive dimensions, loading and alt text. | Build a responsive editorial collage and product-image gallery with real dimensions. | Images keep their proportions, alt text is meaningful and layout shift is limited. |
| 12 | **Project and review** — combine responsive structure, typography and image layouts. | **Marketing landing page:** navigation, hero, feature grid, testimonials, pricing and CTA. | Screenshots at four widths match a mobile-first wireframe; Lighthouse/DevTools finds no serious layout issue; tag `tw-w2`. |

**Weekly review questions:** What CSS rules do these classes generate? Which breakpoint or state caused the hardest bug? Does the layout work with long text, keyboard-only input and zoom? What evidence proves the deliverable works?

### Week 3: Days 13–18 — State variants, interaction and accessible UI

**Weekly deliverable:** A usable forms-and-interaction pattern gallery with keyboard-accessible controls.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Pseudo-class variants: `hover:`, `focus:`, `focus-visible:`, `active:`, `disabled:`. | Create buttons, links and field controls with visible focus, hover and disabled styles. | All actionable elements can be found by Tab and show a clear focus indicator. |
| 14 | Form utilities and native controls: labels, field spacing, outlines and error/help text. | Create a signup form with email, password, select, checkbox and inline validation messages. | Each input has a label; invalid inputs include text feedback and correct focus order. |
| 15 | Group and peer variants, checked states and data/ARIA attribute variants. | Style a disclosure panel, checked-option card and form field with `group-*`, `peer-*` and `aria-*`. | States are driven by real input/ARIA attributes, not color-only decoration. |
| 16 | Motion and transition utilities: duration, easing, transforms and `motion-reduce:`. | Implement subtle button, card and disclosure transitions with a reduced-motion fallback. | Disabling animation preference removes nonessential motion without hiding content. |
| 17 | Accessible menus and dialogs: Tailwind styles vs behavior; native elements and focus management. | Style a `<dialog>` or accessible disclosure and wire minimal JavaScript for open/close behavior. | Escape/close works, focus is returned appropriately and there is no keyboard trap. |
| 18 | **Checkpoint 0 and project** — solve an interaction design from a blank page. | **Component pattern gallery:** buttons, form, alerts, accordion and one dialog or equivalent. | Pass 12 manual tests covering keyboard, 200% zoom, invalid data and contrast; log findings; tag `tw-p0`. |

**Weekly review questions:** What CSS rules do these classes generate? Which breakpoint or state caused the hardest bug? Does the layout work with long text, keyboard-only input and zoom? What evidence proves the deliverable works?

### Week 4: Days 19–24 — Tailwind v4 customization and design systems

**Weekly deliverable:** A documented mini design system shared across two pages.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | CSS-first configuration with `@theme`: tokens for colors, fonts, spacing, radii and shadows. | Create `--color-brand-500`, a display font and a custom shadow; use the generated utilities. | Changing one token updates at least five components, with no broad search-and-replace. |
| 20 | CSS variables vs theme variables; design scales, semantic naming and contrast. | Define brand, surface, muted, success and danger styles and document their use. | Every text/background pair used in components passes your contrast audit. |
| 21 | Dark mode with `dark:`: media-query default versus manual `@custom-variant` selector. | Implement light/dark/system controls and persist user choice in browser storage. | Reload preserves explicit choice; system mode follows OS; no unreadable theme state appears. |
| 22 | Arbitrary values, properties and selector variants: when to use brackets and when to create tokens. | Build a hero with one justified one-off value; refactor repeated exceptions into tokens. | The resulting class list has no repeated arbitrary value that should be a shared token. |
| 23 | Custom CSS, `@layer`, `@utility`, and `@apply` trade-offs; component extraction without losing clarity. | Create one custom `@utility` and two reusable design-system patterns; document usage and escape hatches. | Custom utility works with a responsive or state variant; specificity stays predictable. |
| 24 | **Project and review** — design-system refactor and accessibility audit. | **Mini design system:** buttons, inputs, product cards, navigation and alert across two themed pages. | Tokens apply consistently in both themes; style guide explains variants; tag `tw-w4`. |

**Weekly review questions:** What CSS rules do these classes generate? Which breakpoint or state caused the hardest bug? Does the layout work with long text, keyboard-only input and zoom? What evidence proves the deliverable works?

### Week 5: Days 25–30 — Real-world components and framework integration

**Weekly deliverable:** A responsive storefront or admin dashboard using maintainable components.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Source scanning and complete class names: why `bg-${color}-500` fails; `@source` basics. | Break a dynamic-class example intentionally, then replace it with a finite class-to-style mapping. | Production build contains every required style and no incorrect runtime interpolation. |
| 26 | Component architecture: structure/variant separation; React/Vue/Svelte or HTML partials. | Extract a typed or documented button component with solid/outline/danger variants. | One component renders all variants and a class-string inspection proves they are statically detectable. |
| 27 | Complex responsive patterns: sidebar, tables, scroll areas and data-heavy cards. | Build a dashboard with collapsible sidebar, metric cards and readable 20-row table. | Data remains operable at 320 px without breaking table headings or focus. |
| 28 | Container queries: adapting card content to its parent rather than viewport alone. | Put the same card inside narrow and wide dashboard panels using `@container` variants. | Cards change layout as container width changes even at a fixed viewport width. |
| 29 | Third-party headless UI, form controls and component kits: behavior vs styling; license/a11y review. | Style one headless primitive or native control; compare it with a DIY equivalent. | Behavior tests pass, dependency choices are documented and users can operate by keyboard. |
| 30 | **Project and review** — realistic UI assembly and code review. | **Storefront/dashboard v1:** filtered-looking catalog or dashboard shell, dialogs, responsive layout, theme toggle. | A second person can change a token and add a card; run production build and tag `tw-w5`. |

**Weekly review questions:** What CSS rules do these classes generate? Which breakpoint or state caused the hardest bug? Does the layout work with long text, keyboard-only input and zoom? What evidence proves the deliverable works?

### Week 6: Days 31–36 — Quality, performance and production workflows

**Weekly deliverable:** A production-ready component gallery with documented accessibility, performance and build checks.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | DevTools inspection, browser rendering, specificity debugging and utility conflict diagnosis. | Find and fix five deliberate bugs: missing style, overflow, specificity, focus and hover-only UI. | Your bug log names the root cause, reproducible case and a preventive check for each. |
| 32 | Accessible responsive QA: WCAG concepts, contrast, alt text, screen readers, 200% and 400% zoom. | Audit two representative flows with keyboard and an automated accessibility checker. | Fix critical violations and document what automation cannot verify. |
| 33 | Fonts, images, lazy loading, critical experience and CSS output inspection. | Optimize your project assets and compare build output and browser audit before/after. | README records image sizes, CSS output size and measured results without invented scores. |
| 34 | Integrations in practice: Vite plugin vs CLI vs PostCSS; Next.js and Angular use cases. | Build the same two-component demo via CLI and Vite; outline the PostCSS steps for Next/Angular. | Both demo builds produce working styles; you can explain why their configuration differs. |
| 35 | Legacy Tailwind v3 to v4 migration: CSS `@import`, config differences, old directives and plugin changes. | Take a small v3 tutorial snippet and write a v4 migration checklist without blindly copying commands. | Checklist flags `tailwind.config.js`, `@tailwind` directives and `npx tailwindcss init -p` as version-sensitive. |
| 36 | **Checkpoint 1 and project** — quality gate before capstone. | **Production UI package:** responsive component gallery, CSS-first theme, docs and QA results. | Fresh install and production build succeed; 20 visual/interaction checks pass; tag `tw-p1`. |

**Weekly review questions:** What CSS rules do these classes generate? Which breakpoint or state caused the hardest bug? Does the layout work with long text, keyboard-only input and zoom? What evidence proves the deliverable works?

### Week 7: Days 37–42 — Capstone, deployment and handoff

**Weekly deliverable:** A polished five-page responsive website, tested and deployed with a reusable Tailwind design system.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Product thinking: audience, content hierarchy, scope, page inventory and acceptance criteria. | Write a one-page plan for a real portfolio, nonprofit, small business or catalog site. | Plan has five pages, three core user tasks and testable mobile/accessibility criteria. |
| 38 | Information architecture and page construction. | Build home and catalog pages with navigation, editorial imagery and clear CTAs. | At least two pages are functional, responsive and keyboard navigable. |
| 39 | Page templates and shared components. | Build detail, about and contact pages using the same tokenized navigation, cards and footer. | All five pages share consistent visual language; links are valid. |
| 40 | Product polish and honest functionality: loading/empty/error messages, form validation and dialogs. | Add search/filter interaction or contact-form client validation; simulate empty and invalid states. | No fake backend claims; user sees clear state feedback and form errors are announced or easy to locate. |
| 41 | Production release: optimize assets, run build checks, write README and deploy to static hosting. | Publish the site to a static host and add a short demo or GIF/screenshots plus environment notes. | Public URL (if hosting available) or locally reproducible static build works from README alone. |
| 42 | **Final capstone review** — independent tester, issue triage and release. | Have someone test three user journeys; fix top issues; tag `tailwind-v1.0` and document remaining limits. | A new reader can clone/build/run; mobile, dark mode, keyboard and semantic-HTML checks are demonstrated. |

**Weekly review questions:** What CSS rules do these classes generate? Which breakpoint or state caused the hardest bug? Does the layout work with long text, keyboard-only input and zoom? What evidence proves the deliverable works?

---

## Checkpoints — do not skip

| Gate | After | Required proof | If you cannot pass |
|---|---|---|---|
| **Checkpoint 0: accessible fundamentals** | Session 18 | Build a simple responsive form and card layout from a blank HTML page; show keyboard focus, one error state, a disclosure, reduced-motion handling and 12 documented checks. | Repeat Days 13–17 and retest. Focus on correct HTML behavior before styling complexity. |
| **Checkpoint 1: production-ready patterns** | Session 36 | Fresh install, production build, one `@theme` design system, theme toggle, complete static class strings, 20 manual QA checks and a written explanation of source scanning. | Repeat the specific failed topics from Weeks 4–6, then rerun the gate. |
| **Final capstone** | Session 42 | Five-page mobile-first site, live URL or reproducible static build, accessibility/zoom checks, screenshots at four widths, README and `tailwind-v1.0` tag. | Fix blockers and re-test; shipment is not complete merely because the page looks good on your monitor. |

### Memory-only practice tests

Before each gate, spend 30 minutes with your notes closed. You should be able to:

1. Explain what `px-4`, `max-w-3xl`, `md:grid-cols-2` and `focus-visible:ring-2` roughly translate to in CSS.
2. Create a two-column responsive layout without copying classes from old files.
3. Explain the difference between a mobile-first breakpoint and a container query.
4. Explain why constructing `bg-${color}-500` at runtime can fail, then replace it with literal class mappings.
5. Explain what `@theme`, `@source`, `@utility` and `@custom-variant` do in Tailwind CSS v4.
6. Distinguish visual styling from interaction, validation and security; Tailwind does not implement those by itself.

## Daily deliberate-debug exercises

Choose at least one each day and document the root cause (not only the fix):

- Remove a required class from your source and find why the expected visual style disappeared.
- Produce a narrow-screen overflow using a long string, wide image or inflexible grid; fix the real sizing constraint.
- Remove `focus-visible` feedback from a button and try keyboard navigation; fix the user-visible regression.
- Switch dark mode or browser color preference and find any component with insufficient contrast.
- Write `bg-${color}-500` in JavaScript and compare compiled CSS with an explicit class mapping.
- Observe what Preflight changes on native headings, lists and form elements. Restore deliberate semantics and styling.
- Introduce a loading, empty, disabled or invalid state, then verify that meaning is communicated without color alone.

## Capstone specification: five-page responsive site

Choose a **realistic site** rather than a generic screenshot clone: personal portfolio, community organization, small business, product catalog, design studio, or documentation microsite. It should contain:

- **Home:** clear value proposition, hero image, accessible navigation, CTA and responsive feature cards.
- **Catalog / Work:** mobile-first grid with filters or visual categories (implement functionality honestly if interactive).
- **Detail:** structured item details, responsive media, related items and helpful states.
- **About:** readable editorial content, team/process cards and a clear call to action.
- **Contact:** labelled form, explicit validation, success/error behavior (client-only demo or real backend identified accurately).
- **Shared UI:** footer, nav, typography scale, `@theme` tokens, focus styles, light/dark or system preference, and meaningful mobile behavior.

**Hard acceptance criteria:**

- Test 320, 375, 768, 1024 and 1440 CSS pixel widths; note any justified exceptions.
- Test keyboard Tab/Shift+Tab, Enter/Space activation and modal/dialog Escape where applicable.
- Audit text contrast and non-text focus indicators; no content relies on hover alone.
- Test 200% browser zoom and a narrow viewport; important controls remain discoverable.
- Turn on reduced motion and verify that essential content/interaction is still available.
- Run `npm run build` from a fresh clone after installing dependencies; check final styles on the built site, not only in dev mode.
- Record accessibility-audit findings and manual fixes. Automated checkers help but **cannot certify full WCAG compliance**.
- Add a README: setup, run/build commands, screenshots, page list, design token decisions, browser checks and known limits.
- Do not put API keys, passwords, private customer details or secrets in the repository.

## Tailwind CSS v4 reference recipes

The following are **short patterns** to understand, not full apps. Work through them before copying them into a capstone.

### A. CSS-first design tokens

```css
@import "tailwindcss";

@theme {
  --color-brand-500: #4f46e5;
  --color-brand-600: #4338ca;
  --font-display: ui-sans-serif, system-ui, sans-serif;
}
```

```html
<button class="rounded-lg bg-brand-500 px-4 py-2 font-display font-semibold text-white hover:bg-brand-600 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-brand-500">
  Save changes
</button>
```

### B. Manual dark mode (CSS selector instead of OS-only preference)

```css
@import "tailwindcss";
@custom-variant dark (&:where(.dark, .dark *));
```

```html
<div class="bg-white text-slate-900 dark:bg-slate-950 dark:text-white">
  This panel supports a manual dark theme.
</div>
```

Set or remove the `dark` class on the root `<html>` element. If a user can choose light/dark/system, synchronize the selection with storage and OS preference; test the initial render for flashing or incorrect theme.

### C. Avoid dynamic class-name construction

```js
// Incorrect: the scanner cannot reliably see complete class names.
const broken = `bg-${status}-500`

// Correct: the exact class strings exist in source.
const statusClasses = {
  good: 'bg-emerald-500 text-white',
  bad: 'bg-rose-600 text-white',
}
const classes = statusClasses[status] ?? 'bg-slate-500 text-white'
```

When class strings live in an external source directory that automatic detection skips, read the `@source` documentation. Do not assume an old v3 `content` glob is the normal v4 solution.

### D. Responsive grid and a container query

```html
<div class="grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-3">
  <article class="rounded-xl border p-5 shadow-sm">First card</article>
  <article class="rounded-xl border p-5 shadow-sm">Second card</article>
  <article class="rounded-xl border p-5 shadow-sm">Third card</article>
</div>

<div class="@container">
  <article class="flex flex-col gap-4 @md:flex-row">
    <div class="rounded-lg bg-slate-200 p-6">Photo placeholder</div>
    <p class="text-sm">Changes at a container width, not a viewport width.</p>
  </article>
</div>
```

### E. One custom utility

```css
@import "tailwindcss";

@utility content-auto {
  content-visibility: auto;
}
```

Use sparingly and document where browser layout/performance trade-offs have been tested. Prefer semantic tokens over dozens of unexplained one-off arbitrary values.

## Integrating Tailwind with other frameworks

Tailwind is usable without a JavaScript framework. After Week 4, optionally reuse your design system in a framework you already know:

| Stack | Typical v4 setup path | Extra learning needed |
|---|---|---|
| Plain HTML + Vite | `tailwindcss` + `@tailwindcss/vite` | None beyond HTML, CSS and minimal JS. |
| React + Vite | Add the Tailwind Vite plugin and CSS import | React props, components and state. |
| Vue + Vite | Add the Tailwind Vite plugin and CSS import | Vue templates and reactive state. |
| SvelteKit | Follow current SvelteKit/Tailwind Vite integration instructions | Svelte components and runes. |
| Next.js | `tailwindcss`, `@tailwindcss/postcss`, `postcss`; import from global CSS | React and Next.js App Router. |
| Angular | Follow Tailwind's current Angular/PostCSS integration guide | Angular templates, CLI and standalone components. |

**Important version boundary:** Do not mix installation steps from Tailwind v2/v3 tutorials with Tailwind v4 without checking the v4 [upgrade guide](https://tailwindcss.com/docs/upgrade-guide). Some examples still use `tailwind.config.js`, `@tailwind base`, or `npx tailwindcss init -p`; these are not the default v4 installation path.

## Official resources and suggested use

| Source | Link | When to use |
|---|---|---|
| Tailwind introduction and installation | https://tailwindcss.com/docs/installation/using-vite | Setup, Day 1 and troubleshooting. |
| Tailwind CLI installation | https://tailwindcss.com/docs/installation/tailwind-cli | Alternative setup and Day 34. |
| Styling with utility classes | https://tailwindcss.com/docs/styling-with-utility-classes | Weeks 1–2. |
| Responsive design | https://tailwindcss.com/docs/responsive-design | Week 2. |
| State variants | https://tailwindcss.com/docs/hover-focus-and-other-states | Week 3. |
| Dark mode | https://tailwindcss.com/docs/dark-mode | Day 21. |
| Theme variables | https://tailwindcss.com/docs/theme | Week 4. |
| Source detection | https://tailwindcss.com/docs/detecting-classes-in-source-files | Day 25 and debugging. |
| Custom CSS and utilities | https://tailwindcss.com/docs/adding-custom-styles | Day 23. |
| Functions and directives | https://tailwindcss.com/docs/functions-and-directives | Advanced customization. |
| Tailwind v4 upgrade guide | https://tailwindcss.com/docs/upgrade-guide | Day 35 and older tutorials. |
| MDN HTML/CSS | https://developer.mozilla.org/en-US/docs/Web/CSS | CSS foundations and browser debugging. |
| Web Content Accessibility Guidelines | https://www.w3.org/WAI/standards-guidelines/wcag/ | Keyboard, zoom, contrast and audits. |
| Vite guide | https://vite.dev/guide/ | Dev server and production builds. |

All core docs above are available free online. If your installed package version differs from the documentation's current version, follow your installed version's release notes. A premium component product or paid design template is **not required** for this roadmap.

## What comes next

- Build the same capstone with Bootstrap, then compare utility-first and component-first CSS approaches.
- Apply the design system to React, Next.js, Vue, Svelte or Angular and test rendering of all class variants.
- Create a small, accessible UI component library with documented variants and visual regression tests.
- Learn deeper browser CSS concepts: cascade layers, container queries, modern color spaces, custom properties, and web performance.

---

*Success is based on demonstrated builds and checkpoints, not calendar speed. This roadmap teaches Tailwind CSS v4 styling and front-end fundamentals; it does not claim to replace professional accessibility review, back-end development, or full JavaScript framework training.*
