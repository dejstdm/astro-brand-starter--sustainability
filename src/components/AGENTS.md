# Sustainability Components Guide

## Directory Policy
- All sustainability components reside in `src/components/prod/`.
- Name files with "Sus" prefix in PascalCase (e.g., `SusHeroBanner.astro`, `SusImpactCard.astro`).
- Keep component-specific assets close to the component; do not recreate `examples` or `dev` folders.
- All components are isolated from the main Lipton site using "sus" prefix.

## Image Organization
- All images are manually exported from Figma directly to `public/images/` (no subdirectories).
- All images are stored in the root `public/images/` folder.
- Reference images in components using relative paths: `/images/hero-bg.jpg`.
- Only use images that exist in the `public/images/` folder - no external or generated images.

## Production Component Workflow
1. Confirm the shared design system tokens, typography, and spacing rules are defined so the component can consume them consistently.
2. Map the HTML structure and required data.
3. Create the `.astro` file under `src/components/prod/`.
4. Follow the standard wrapper classes with "sus-" prefix (`sus-page-sec-v2`, `sus-container`, `sus-sec`).
5. Hook up SCSS and JavaScript if needed.
6. Surface the component on a sustainability page for verification.

## Baseline Template
```astro
---
const { variant } = Astro.props;
---
<SusSectionV2 background="white" taper="none">
  <div class="sus-component-name sus-sec">
    
    <!-- Centered header (if needed) -->
    <div class="sus-container-wide">
      <div class="sus-component-name__header">
        <h2 class="sus-component-name__title">Title</h2>
        <p class="sus-component-name__subtitle">Subtitle</p>
      </div>
    </div>

    <!-- Main content -->
    <div class="sus-container">
      <div class="sus-component-name__content sus-sec__content">
        <!-- component content -->
      </div>
    </div>
    
  </div>
</SusSectionV2>
```

Replace `component-name` with the kebab-case slug for your component. All classes must be prefixed with "sus-" to prevent style leakage.

**Background Control:** Use the `background` prop on `SusSectionV2` component to control section backgrounds. Available options: `"primary"`, `"pink"`, `"orange"`, `"green"`, `"yellow"`, `"image"`.

**Taper Control:** Use the `taper` prop to add diagonal borders. Available options: `"both-right"`, `"both-left"`, `"top-right"`, `"top-left"`, `"none"`.

**Container Rule:** NEVER nest containers! Use `.sus-container-wide` for centered headers and `.sus-container` for content. They should be siblings, not nested.

## Checklist
- Uses the `SusSectionV2` component with `sus-container`, `sus-sec`, and `sus-sec__content` structure.
- Class names follow BEM with "sus-" prefix (`sus-component-name`, `sus-component-name__element`, `sus-component-name--modifier`).
- Props typed via the frontmatter `Astro.props` object when needed.
- No inline `<style>` or `<script>` blocks; use SCSS modules and JS modules instead.
- Images load from `public/images/` (all images in root folder, no subdirectories).
- All images are manually exported from Figma directly to `public/images/`.
- Only use existing images from the `public/images/` folder - no external sources.
- Component may include multiple variants/options to mimic backend behavior.

## Styling
- Create the SCSS file under `src/scss/components/_sus-component-name.scss`.
- Import `@use "../utils/variables" as *;` at the top of each component stylesheet.
- Add the new file to `src/scss/main.scss` under the components section.
- Keep selectors scoped to the component block with "sus-" prefix.
- All sustainability styles are isolated from main Lipton site.

## JavaScript Integration
- Place component logic in `src/scripts/modules/` (e.g., `sus-component-name.mjs`).
- Export an init function and import it from `src/scripts/functions.js`.
- In modules, guard DOM queries so unused components do not throw errors.
- Avoid leaking globals; attach helpers to the returned object if needed.
- Use "sus-" prefixed selectors to target sustainability components only.

## Testing
- Render the component on one of the 4 sustainability pages in `src/pages/prod/` or a temporary internal route.
- Verify mobile, tablet, and desktop behaviour.
- Confirm keyboard navigation and semantic markup meet accessibility expectations.
- Test that styles don't leak into other parts of the site (verify "sus-" prefix isolation).

## Maintenance
- Keep props and slots documented in component comments when helpful.
- When removing a component, delete its SCSS and JS counterparts.
- Re-run `npm run build` after major changes to check for linting or compile issues.



