# Repository instructions

## Project layout and architecture

- This repository is both an Astro workshop starter and a set of workshop materials. The runnable app lives in `src/`; workshop lessons live in `workshop/`, and the standalone Pages content lives in `docs/`.
- Astro uses server output with the `@astrojs/node` standalone adapter (`astro.config.mjs`). Files under `src/pages/` define routes: `index.astro` is the app home page, and `api/contributions/[username].ts` is the dynamic contributions API route. The API handler is currently a 501 placeholder.
- GitHub Pages currently publishes `docs/` and selected translated workshop files through `.github/workflows/deploy.yml`; it does not build or publish the Astro app. Keep this distinction in mind when changing deployment behavior.

## Commands

Run these from the repository root:

| Purpose | Command |
| --- | --- |
| Install dependencies | `npm install` |
| Start the Astro development server | `npm run dev` |
| Build the Astro app | `npm run build` |
| Preview the production build | `npm run preview` |

There is currently no configured test runner or test script, so there is no single-test command. There are also no lint scripts configured in `package.json`.

## Repository-specific conventions

- Keep Astro page and endpoint routes under `src/pages/`; use Astro's file-based route mapping for new routes.
- The localization workflow is implemented by `.github/workflows/localization-sync.yml` and `scripts/localization_sync.py`. Its supported sources and locale mappings are explicitly constrained in the script; preserve its safe-path checks and source/localized SHA-256 baselines when changing localization behavior. Do not treat generated translations or localization state as source content.
- Translation outputs follow the existing layout: localized READMEs use `README.<locale>.md`, workshop translations live under `workshop/<locale>/`, and docs translations live under `docs/<locale>/`. The workflow records baseline metadata under `localizations/<locale>/.localization-state.json`.
- When localizing documentation, follow `.github/skills/localizations/SKILL.md` and the matching locale rule in `.github/skills/localizations/rules/`; preserve code, commands, URLs, and Markdown structure, and keep same-document heading links aligned with translated headings.
