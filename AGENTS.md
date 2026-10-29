# AGENTS.md

## Project

- Website for **Creative Coding Kortrijk (CCK)**, a community where art and code meet.
- Audience: artists, designers, programmers and curious people of all skill levels who want to join workshops, events and meetups about creative coding.
- The site presents the community's foundations, upcoming workshops (pen plotter, p5.js, Max/MSP) and the team.
- The content is placeholder: `src/pages/about.md` ends with "This is all fake."
- Design source: Figma (link in `README.md`), based on the "Positivus" community landing page.

## Stack & constraints

- **Astro 7** (`astro` ^7.4.0), ES modules (`"type": "module"`), default `astro.config.mjs` with no integrations.
- **TypeScript** via `astro/tsconfigs/base`, with `strictNullChecks` on.
- **Content collections** are defined in `src/content.config.ts` with the `glob` loader and Zod schemas:
  - `workshops`: `title`, `image`
  - `team`: `name`, `function`, `bio`, `pic`
  - `foundations`: `title`, `description`
- Content is Markdown in `src/content/<collection>/`, with images in an `img/` subfolder next to the Markdown files.
- **No CSS framework**: plain CSS in `src/styles/` (`reset.css`, `global.css`, `markdown.css`) plus scoped `<style>` blocks in `.astro` files.
- Design tokens are CSS custom properties on `:root` in `global.css`: colors (`--color-*`), fluid type scale (`--fs-*`) and fluid spacing (`--sp-*`) built with `clamp()`.
- Font: Space Grotesk Variable via `@fontsource-variable/space-grotesk`.
- Layouts: `src/layouts/Base.astro` (header, main, footer) and `src/layouts/Markdown.astro` (for `.md` pages).
- Pages: `src/pages/index.astro`, `about.md`, `news.astro`.
- Current state: `index.astro` renders only `Hero`, and no component calls `getCollection` yet. `news.astro` holds `##TITLE##`/`##DATE##`/`##CONTENT##` placeholders that are not valid Astro.
- Scripts: `npm run dev` (dev server with `--host`), `npm run build`, `npm run preview`.
