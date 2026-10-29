# AGENTS.md

## Project

- Website for Creative Code Kortrijk (CCK), a new creative coding club in Kortrijk, Belgium.
- For artists, designers, programmers and anyone curious about art and code, from beginners to professionals.
- The site presents the club's workshops, foundations (core values), team members and news.
- Visitors can hunt for the hidden digits of a 4-digit code on the site and enter them on the `/code` page.
- Built by a team of three students (Mauro, Niels, Snezhana) using Git and GitHub Flow.
- Design: [Figma](https://www.figma.com/design/Qepjp5d40858EedDBt96Yu/CCK?node-id=403-244&t=3JWw8tYXLN9YaCl4-0).

## Stack & constraints

- [Astro](https://astro.build) 7 with TypeScript (`astro/tsconfigs/base`, `strictNullChecks`).
- Content is Markdown in content collections, configured in `src/content.config.ts` with the `glob` loader and Zod schemas:
  - `workshops` (`src/content/workshops/`): `title`, `image`
  - `foundations` (`src/content/foundations/`): `title`, `description`
  - `team` (`src/content/team/`): `name`, `function`, `bio`, `pic`
  - `news` (`src/content/news/`): `title`, `date`
- A missing frontmatter field makes the build fail.
- Images live in an `img/` folder per collection and are referenced by relative path in the frontmatter.
- Detail pages use the entry `id` as dynamic route parameter (`/workshops/<id>`, `/foundations/<id>`, `/team/<id>`).
- Layouts: `src/layouts/Base.astro` and `src/layouts/Markdown.astro`.
- Each collection has a list component and a card component in `src/components/` (e.g. `Workshops` / `WorkshopCard`).
- Starter code contains placeholders in the form `##WHAT-SHOULD-BE-HERE##`.
- No CSS framework: plain CSS in `src/styles/` plus scoped `<style>` blocks, with CSS custom properties.
- Font: Space Grotesk via `@fontsource-variable/space-grotesk`.
- Markdown linting via `.markdownlint.json` (MD013 and MD041 disabled).
- Scripts: `npm run dev`, `npm run build`, `npm run preview`.
- Deployed to GitHub Pages.
