# Repository Guidelines

## Project Structure & Module Organization
- `frontend/` holds the Vite + React (TypeScript) UI. Core entry points: `src/main.tsx`, `src/App.tsx` (custom client-side router), and page-level views in `src/pages/`. Shared UI lives in `src/components/`; global styles in `src/index.css` and `src/styles/`. Reference text assets sit in `src/guidelines/`.
- `server/` is currently a placeholder for future API work—coordinate before adding runtime code. The root `README.md` captures the product vision.

## Build, Test, and Development Commands
- Install deps: `cd frontend && npm install`.
- Run locally: `npm run dev` (served by Vite; use `--host` when testing on LAN or mobile).
- Production build: `npm run build` (validates TypeScript usage and produces `dist/`).

## Coding Style & Naming Conventions
- Language: TypeScript + React functional components; prefer hooks and props over shared globals.
- Indentation: 2 spaces; keep imports ordered logically (react, third-party, local).
- Styling: Tailwind utility classes in JSX; keep long class strings readable by grouping related utilities. Reuse shared pieces via `src/components/` and keep page layout concerns in `src/pages/`.
- Naming: PascalCase for components/files (`GlassCard.tsx`), camelCase for variables/hooks (`useRouterHook`), kebab-case for CSS files.

## Testing Guidelines
- No automated tests are present yet. When adding, colocate component tests as `ComponentName.test.tsx` (Vitest + React Testing Library recommended) inside `frontend/src/`. Aim to cover routing logic in `App.tsx` and interactive components (e.g., `ContactModal`, `Header`). Keep tests deterministic (mock timers/network) and avoid reliance on external assets.

## Commit & Pull Request Guidelines
- Commit history uses short, descriptive phrases (e.g., `create a monorepo setting`). Keep messages in present tense and scoped to a single change set.
- PRs should include: a concise summary, before/after screenshots or GIFs for UI changes, notes on testing performed (or gaps), and links to any related issue/ticket. Call out breaking changes or new environment assumptions explicitly.

## Security & Configuration Tips
- Do not commit secrets or environment-specific endpoints; prefer `.env.local` patterns (not yet present) and document expected variables in the PR.
- If introducing backend code under `server/`, include minimal health checks and input validation from the outset.
