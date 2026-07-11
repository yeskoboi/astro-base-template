# astro-base-template

Personal Astro starter template. Basic, stable scaffolding meant to rarely change — project-specific content (colors, fonts, header/footer content, page structure) is intentionally NOT included here; only the architecture is.

## Scaffolding a new project from this template

```bash
npm create astro@latest . -- --template yeskoboi/astro-base-template --install --no-git --no-ai --yes --skip-houston
```

Run from inside the new project's empty target directory (use `.` as shown). Flags:
- `--install` — installs dependencies immediately (includes `@astrojs/check` + `typescript`, already in this template's `package.json`).
- `--no-git` — do NOT let the scaffolder init git; that's a deliberate separate step (see below), so `.gitignore` can be reviewed and the first commit is intentional.
- `--no-ai` — skips create-astro's own generic AI-agent scaffold files.
- `--yes` — accepts defaults for anything not explicitly flagged (TypeScript strict is already the create-astro v5+ default).
- `--skip-houston` — skips the CLI's animated mascot intro. Cosmetic only.

After scaffolding, as an explicit separate step:

```bash
git init && git branch -M main
git add -A
git commit -m "Initial commit: scaffold from astro-base-template"
```

## What's included

- `src/styles/tokens.css` — spacing scale (`2xs`→`3xl`, numeral-prefixed, not doubled letters), type scale, layout tokens. Colors are placeholders — replace with the project's actual palette.
- `src/styles/global.css` — reset / base / utilities structure (see comments for the reasoning behind the split). `::selection` and `-webkit-font-smoothing` fixes included. `@font-face` block left empty/commented — add the project's actual font here, this template is intentionally font-agnostic.
- `src/layouts/BaseLayout.astro` — `<html>/<head>/<body>` shell, `<Header />` / `<main><slot /></main>` / `<Footer />`, optional `title` prop (defaults to `"Astro"`).
- `src/components/Header.astro` / `Footer.astro` — empty stubs. Fill in per-project; intentionally has no content since that's never reusable across projects.
- `package.json` — `build` runs `astro check && astro build`; `check` script available standalone.

## Conventions (apply to whatever gets built on top of this)

- No Tailwind, no Tailwind-style naming conventions (no numeric spacing scales, no `base`/`2xl` labels borrowed from Tailwind specifically) — plain T-shirt sizing, numeral-prefixed once a scale needs many steps (`2xl`, `3xl`, not `xxl`, `xxxl`).
- Plain `.astro` components by default; reach for a framework (`@astrojs/react` etc.) only when a specific component needs real client-side interactivity, using Astro islands (`client:*` directives) so the rest of the page ships zero JS.
- Reusable pieces of UI → `src/components/`. Page-shell wrappers using `<slot />` → `src/layouts/`.
