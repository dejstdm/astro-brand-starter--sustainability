# Astro Brand Starter

This template delivers production-ready Astro, SCSS, and JavaScript for brand websites. Use it to assemble components that can be copied into other platforms after build. Project conventions and detailed workflows are documented in the `AGENTS.md` files throughout the repo.

## Project Structure
- `src/components/prod/` – Production-ready Astro components
- `src/pages/prod/` – Production routes
- `src/layouts/ProdLayout.astro` – Shared layout that loads global styles and scripts
- `src/scss/` – SCSS architecture (base, layout, components, utils)
- `src/scripts/modules/` – JavaScript modules for production components
- `public/` – Static assets copied as-is to the build output

## Commands
| Command             | Action                                             |
| ------------------- | -------------------------------------------------- |
| `npm install`       | Install dependencies                               |
| `npm run dev`       | Start the local dev server at http://localhost:4321 |
| `npm run build`     | Build the production site to `dist/`               |
| `npm run preview`   | Preview the production build locally               |
| `npm run astro ...` | Run additional Astro CLI commands                  |

## Recommended Workflow
1. `npm install`
2. `npm run dev`
3. Create or update components in `src/components/prod/`
4. Add SCSS and JS modules as needed, following the guidance in `src/scss/AGENTS.md`
5. Surface components on pages in `src/pages/prod/` and verify behaviour
6. Run `npm run build` to confirm the project compiles cleanly

## Component Testing
- Render components directly within production pages during development.
- If you need ad-hoc review, create a temporary route inside `src/pages/prod/` and remove it before shipping.
- There is no separate dev or example component library in this starter.

## Using the Output
- After building, copy the generated HTML, CSS, and JS from `dist/` into your downstream platform (e.g., a CMS theme).
- Reuse the design tokens defined in `src/scss/utils/_variables.scss` to keep styling consistent.

## Additional Resources
- [Astro Documentation](https://docs.astro.build)
- [Astro Discord](https://astro.build/chat)
- [Cursor Rules Tutorial](https://www.youtube.com/watch?v=FpJ48a5S5lU)

