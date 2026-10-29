# AGENTS.md

## Project

- Website for **Creative Code Kortrijk (CCK)**, a new creative coding club in Kortrijk, Belgium.
- Audience: artists, designers, students and anyone curious about coding as a creative medium
  (generative art, pen plotters, p5.js, Max/MSP, ...).
- The site presents the club's **workshops**, its **foundations** (what the club stands for), its
  **team**, and **news**. A hidden 4-digit code puzzle (`/code` page) is planned.
- Built by a team of three students (Mauro, Niels, Snezhana) as the Web 3 "Git Party" assignment,
  using Git and GitHub Flow: feature branches (`feature/...`) and pull requests into `main`.
- Design: Figma file linked in `README.md`.

## Stack & constraints

- **Astro 7** (`astro` ^7.4.0), ES modules (`"type": "module"`), TypeScript config extends
  `astro/tsconfigs/base` with `strictNullChecks`.
- No UI framework integrations and no CSS framework: plain `.astro` components and plain CSS in
  `src/styles/` (`reset.css`, `global.css`, `markdown.css`).
- Font: `@fontsource-variable/space-grotesk`, imported in `src/layouts/Base.astro`.
- Layouts: `src/layouts/Base.astro` (Header + Footer) and `src/layouts/Markdown.astro`.
- Pages in `src/pages/`: `index.astro`, `about.md`, `news.astro`. Detail pages use the collection
  entry `id` as dynamic route parameter.
- Content lives in **content collections**, defined in `src/content.config.ts` with the `glob`
  loader and Zod schemas. A missing frontmatter field makes the build fail.
  - `workshops` (`src/content/workshops/`): `title`, `image`.
  - `foundations` (`src/content/foundations/`): `title`, `description`.
  - `team` (`src/content/team/`): `name`, `function`, `bio`, `pic`.
  - `news` (`src/content/news/`): not defined yet.
  - Images sit in an `img/` folder next to the markdown and are referenced relatively.
- Components in `src/components/`: one list component and one card component per collection
  (`Workshops`/`WorkshopCard`, `Foundations`/`FoundationsCard`, `Team`/`TeamCard`), plus `Header`,
  `Footer`, `Hero`, `ArrowLink` and `Code`.
- The starter code contains placeholders written as `##WHAT-SHOULD-BE-HERE##`.
- Scripts: `npm run dev` (dev server, `--host`), `npm run build`, `npm run preview`.
- Deployment target: GitHub Pages via a GitHub Actions workflow (not set up yet).
