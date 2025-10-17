# Lipton Sustainability Pages Guide

## Purpose
Pages in this directory represent the 4 production-ready Lipton Sustainability pages. Each route should assemble sustainability components from `src/components/prod/`, use shared layouts, and reflect the same content that will be integrated into the main Lipton site without style leakage.

## Important Note About Figma Design
The Figma design for this project is not created perfectly. Some things are overlooked:

1. **Containers are not used in Figma but in code they are used** - The component structure with `SusSectionV2`, `sus-container`, and `sus-sec` classes must be respected even though it's not present in Figma.

2. **Sections in Figma are not correctly named** - The actual section names in Figma don't match the 9 sustainability sections we need to create. Use the 9 section names defined in the components guide (SusHero, SusNavigation, etc.) rather than the Figma section names.

3. **The 9 sections need to be created with help of Figma MCP** - Components should be based on the actual Figma design specifications, but adapt the naming and structure to match our component architecture.

## The 4 Sustainability Pages
This project creates 4 specific sustainability pages:

1. **Landing Page** (`landing.astro`) - Main sustainability homepage
2. **Origin Page** (`origin.astro`) - Tea origin and sourcing information
3. **Initiatives 1 Page** (`initiatives-1.astro`) - First set of sustainability initiatives
4. **Initiatives 2 Page** (`initiatives-2.astro`) - Second set of sustainability initiatives

## Directory Snapshot
```
src/pages/prod/
|- landing.astro      // Main sustainability homepage
|- origin.astro       // Tea origin and sourcing
|- initiatives-1.astro // First initiatives page
|- initiatives-2.astro // Second initiatives page
```
The root entry point `src/pages/index.astro` loads sustainability content as well; keep both files in sync so local previews and the exported build show the same experience.

## Layout Requirements
- Use `ProdLayout` for every production route.
- Import `../scss/main.scss` through the layout only; do not add extra CSS references inside the page.
- Keep third-party scripts centralized in the layout. Pages should only include component markup and data.

## Page Component Structure
Each of the 4 sustainability pages follows this structure:

**Landing Page Components:**
- SusHero (variant: landing)
- SusNavigation
- SusHighlight

**Origin Page Components:**
- SusHero (variant: origin)
- SusMediaHighlight
- SusProductHighlight

**Initiatives 1 Page Components:**
- SusHero (variant: initiatives-1)
- SusMediaHighlight
- SusInfoBlock
- SusAchievements
- SusHighlight
- SusPartnership
- SusInfoBlock
- SusVideoHighlight
- SusProductHighlight

**Initiatives 2 Page Components:**
- SusHero (variant: initiatives-2)
- SusMediaHighlight
- SusProductHighlight


## Building a New Sustainability Page
1. Confirm the design system tokens and base styles are current so every section pulls from the shared foundation.
2. Create a `.astro` file inside `src/pages/prod/` following the naming convention above.
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



