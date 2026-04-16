# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
pnpm install        # install dependencies
pnpm dev            # start dev server (http://localhost:5173)
pnpm build          # production build (outputs to .vercel/output via adapter-vercel)
pnpm preview        # preview production build
pnpm check          # TypeScript + Svelte type checking
pnpm lint           # Prettier + ESLint checks
pnpm format         # auto-format with Prettier
```

No test suite is configured.

## Architecture

This is a **SvelteKit 5 personal portfolio site**, fully prerendered (static), deployed to Vercel.

**Routing** — File-based via `src/routes/`. Each section (skills, experience, education, projects) has its own route with `export const prerender = true` in the `+page.ts`. The home page (`+page.svelte`) imports and renders all section components inline rather than navigating to sub-routes.

**Data** — All portfolio content (work history, skills list, skill icons) lives in `src/lib/db/data.js` as plain JS exports. There is no backend or database. To update experience, education, or skills, edit this file.

**Component layers:**
- `src/lib/components/ui/` — shadcn-svelte components (card, carousel, sheet, button, separator). Managed via `components.json` config. Add new ones with the shadcn-svelte CLI.
- `src/lib/components/navigationMenu/` — custom sticky nav with responsive Sheet drawer for mobile and dark/light mode toggle via `mode-watcher`.
- `src/routes/*/` — each route folder contains a `*.svelte` component with the actual section UI (e.g., `skills/skills.svelte`), imported wherever needed.

**Styling** — Tailwind CSS v4 via `@tailwindcss/vite`. Theme CSS variables (OKLCH) defined in `src/app.css`. Dark mode toggled by adding `.dark` class to `<html>` — see `navigationMenu.svelte` for the toggle logic which manually syncs `mode-watcher` with the class.

**Skills carousel** — `skills.svelte` accepts an `enableCarousel` prop; the home page passes `true`, the `/skills` route passes nothing (renders a flat grid).

**Static assets** — Images live under `src/public/images/` and are imported directly in Svelte files (Vite handles hashing). The resume PDF is also imported this way for the nav download link.
