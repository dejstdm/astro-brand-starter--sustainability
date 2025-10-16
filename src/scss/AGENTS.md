# Sustainability SCSS Guide

## Architecture Overview
The SCSS layer is organized for Lipton Sustainability pages: variables and utilities feed base styles, layout primitives, and component styles. Each component uses BEM naming with "sus-" prefix and consumes shared design tokens so the compiled CSS can be copied into the main Lipton site without style leakage.

## Directory Layout
```scss
src/scss/
|- main.scss              // Entry point imported by layouts
|- base/
|  |- _fonts.scss         // Font declarations and @font-face rules
|  |- _globals.scss       // Global element defaults
|  |- _normalize.scss     // Normalize baseline
|  |- _typography.scss    // Typography scale
|- layout/
|  |- _container.scss     // Container widths and spacing (NEVER nest containers!)
|  |- _section.scss       // Section wrappers
|- components/            // Component stylesheets will be added here
|- utils/
|  |- _variables.scss     // Design tokens and mixins
```

## Container Rules
**CRITICAL:** Sustainability containers must NEVER be nested inside other containers of any type. Each container variant (`.sus-container`, `.sus-container-wide`, `.sus-container-full`) is a standalone layout element with its own padding and max-width. Use separate sibling containers instead of nesting them.

### Available Containers
- **`.sus-container`** - Default container (950px inner width + 20px padding on each side)
- **`.sus-container-wide`** - Wide container (1080px inner width + 20px padding on each side)  
- **`.sus-container-full`** - Full container (full width, no padding)

## Import Order
`main.scss` must load utilities first, then base, layout, and finally components:
```scss
// UTILS
@use "./utils/variables" as *;

// BASE
@use "./base/fonts";
@use "./base/normalize";
@use "./base/typography";
@use "./base/globals";

// LAYOUT
@use "./layout/container";
@use "./layout/section";

// COMPONENTS
// Component stylesheets will be imported here as they are created
// Example: @use "components/hero";
```
Maintain this sequence so variables and mixins are available before they are used.

## Component Styling Rules
- Every component stylesheet imports variables: `@use "../utils/variables" as *;`
- Scope selectors to the component block with "sus-" prefix (`.sus-hero`, `.sus-testimonial`, etc.).
- Use BEM naming with double underscores for elements and double hyphens for modifiers.
- **CRITICAL: ALL styles must be mobile-first!** Start with mobile styles, then use `@media (min-width: $breakpoint)` queries to enhance for larger screens. NEVER use `max-width` media queries.
- Do NOT add `background-color` to component stylesheets. Use the `sus-page-sec--bg-white` or `sus-page-sec--bg-gray` modifiers in the component markup instead.
- Add the file to `main.scss` immediately after creation to ensure it is bundled.
- All sustainability styles are isolated from main Lipton site using "sus-" prefix.

## Tokens and Utilities
- Brand colors, spacing, breakpoints, and z-index scales live in `_variables.scss`.
- Typography rules (font stacks, weights, heading/body scales) live in `_typography.scss`.
- Update tokens first, then adjust component styles that consume them.

## Workflow for New Sustainability Styles
1. Define or update the shared design system tokens in `_variables.scss`, `_typography.scss`, and related base/layout files before styling components.
2. Create `_sus-component-name.scss` in `src/scss/components/`.
3. Import variables at the top of the file.
4. Write base styles, responsive adjustments, and state modifiers that reference the shared tokens with "sus-" prefix.
5. Import the file in the components block of `main.scss`.
6. Validate in the browser and run `npm run build` to confirm the compiled CSS succeeds and doesn't leak into main site.

## Quality Checklist
- Two-space indentation, no trailing whitespace.
- Avoid unused selectors or deeply nested rules (max three levels).
- Provide brief comments only when explaining non-obvious logic.
- Confirm color contrast and focus states meet WCAG guidance.
- Remove unused files when the related component is deleted.
- All selectors use "sus-" prefix to prevent style leakage into main Lipton site.
- Test that sustainability styles don't affect other parts of the site.



