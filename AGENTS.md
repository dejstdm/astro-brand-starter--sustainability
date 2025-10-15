# Lipton Sustainability Pages

## Purpose
This project delivers 4 production-ready Lipton Sustainability pages with isolated styling and components. All sustainability-specific components use the "sus" prefix to prevent style leakage into the main Lipton site. The repository is focused exclusively on sustainability components; development demos and example content have been removed.

## Quick Start
- Install dependencies: `npm install`
- Start the dev server: `npm run dev` (default: http://localhost:4321)
- Build for production: `npm run build` (outputs to `dist/`)
- Preview the build: `npm run preview`
- Run other Astro commands: `npm run astro <command>`

## Source Layout
```
src/
|- components/
|  |- prod/            # Sustainability components (all prefixed with "sus")
|- layouts/
|  |- ProdLayout.astro # Shared layout for sustainability pages
|- pages/
|  |- index.astro      # Entry page that points to sustainability content
|  |- prod/
|     |- homepage.astro
|     |- [3 more sustainability pages]
|- scss/
|  |- base/
|  |- components/      # Sustainability component styles (sus-* prefixed)
|  |- layout/
|  |- utils/
|- scripts/
|  |- modules/         # Sustainability-specific JavaScript modules
public/
|- images/             # All Figma exports go directly here
dist/
```

## Workflow
1. Establish the sustainability design system first by defining tokens in `src/scss/utils/_variables.scss` and aligning base styles in `src/scss/base/` and `src/scss/layout/`.
2. Build the Astro component inside `src/components/prod/` with "sus" prefix (e.g., `SusHero.astro`), referencing the shared design system tokens.
3. Add or update SCSS in `src/scss/components/` with "sus-" prefixed classes and ensure it is imported by `src/scss/main.scss`.
4. Wire any interactivity in `src/scripts/modules/` and expose it through `src/scripts/functions.js`.
5. Surface the component on one of the 4 sustainability pages within `src/pages/prod/` and verify accessibility, responsiveness, and cross-browser behaviour.
6. Run `npm run build` and copy assets from `dist/` when integrating with the main Lipton site.

## Documentation Map
- Component workflow: `src/components/AGENTS.md`
- SCSS structure and tokens: `src/scss/AGENTS.md`
- Production pages and site assembly: `src/pages/prod/AGENTS.md`

## Principles
- Component-driven, production-first implementation for Lipton Sustainability
- Single source of truth for design tokens in `scss/utils`
- Mobile-first, accessible BEM-based styling with "sus-" prefix isolation
- No dev or example components; only files that ship to production belong in the repository
- All sustainability components and styles are prefixed to prevent leakage into main Lipton site
- Components may include multiple options/variants to mimic backend behavior



