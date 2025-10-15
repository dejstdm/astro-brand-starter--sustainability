# Lipton Sustainability Pages Guide

## Purpose
Pages in this directory represent the 4 production-ready Lipton Sustainability pages. Each route should assemble sustainability components from `src/components/prod/`, use shared layouts, and reflect the same content that will be integrated into the main Lipton site without style leakage.

## Directory Snapshot
```
src/pages/prod/
|- homepage.astro    // Primary sustainability homepage
|- [3 more sustainability pages] // Additional sustainability pages
```
The root entry point `src/pages/index.astro` loads sustainability content as well; keep both files in sync so local previews and the exported build show the same experience.

## Layout Requirements
- Use `ProdLayout` for every production route.
- Import `../scss/main.scss` through the layout only; do not add extra CSS references inside the page.
- Keep third-party scripts centralized in the layout. Pages should only include component markup and data.

## Building a New Sustainability Page
1. Confirm the design system tokens and base styles are current so every section pulls from the shared foundation.
2. Create a `.astro` file inside `src/pages/prod/` (e.g., `impact.astro`, `initiatives.astro`).
3. Import `ProdLayout` plus the required sustainability components from `src/components/prod/`.
4. Compose sections inside `<ProdLayout>` following the component wrappers described in `src/components/AGENTS.md` and referencing sustainability design system classes with "sus-" prefix.
5. Verify that any new component styles are imported in `src/scss/main.scss` and that supporting modules are initialized through `src/scripts/functions.js`.
6. Test the page at `npm run dev` and ensure `npm run build` completes without errors and styles don't leak.

## Content & Data
- Hard-coded content is acceptable for the sustainability pages; keep copy inlined inside the component or page.
- Components may include multiple options/variants to mimic backend behavior before real integration.
- All images are manually exported from Figma directly to `public/images/` (no subdirectories).
- When integrating with a CMS, replace static data with `Astro.props` or `Astro.fetch()` calls as needed.
- Use semantic headings (`h1`, `h2`, etc.) to preserve accessibility and SEO.

## Integrating with Main Lipton Site
- Run `npm run build` and copy the HTML, CSS, and JS emitted to `dist/`.
- If the target system requires partials, split the compiled markup along component boundaries.
- Reuse the same design tokens by porting the variables defined in `src/scss/utils/_variables.scss`.
- All sustainability styles are prefixed with "sus-" to prevent leakage into main site styles.

## Quality Checklist
- Page uses only sustainability components and shared layouts.
- No references to removed dev/example routes.
- Navigation links and buttons point to live routes.
- Accessibility review performed (landmarks, headings, focus order).
- Build output verified before delivering assets to main Lipton site.
- All styles use "sus-" prefix to prevent leakage into main site.
- Components with multiple variants properly mimic backend behavior.



