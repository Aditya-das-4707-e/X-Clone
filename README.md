# X.com (Clone)

A lightweight, static front-end prototype of an X/Twitter-like layout, built with plain HTML and Tailwind CSS. The project demonstrates responsive layout patterns, a sidebar navigation, a main feed, and a right-hand widget column.

This README explains the project structure, how to rebuild the included Tailwind CSS, common troubleshooting tips, and suggested improvements.

---

## Project snapshot

- Static single-page prototype: `index.html`
- Tailwind entry: `src/input.css` (imports Tailwind)
- Compiled CSS: `src/output.css` (committed for convenience)
- Node deps: `package.json` (Tailwind CLI listed)

## Goals

- Practice responsive layout with Tailwind
- Prototype a three-column social feed layout
- Keep the project dependency-light and framework-free

## Setup & development

Prerequisites
- Node.js + npm (optional if you only use the committed `src/output.css`)
- Optional: Python (quick static server)

Install (optional)

```bash
npm install
```

Build Tailwind CSS

```bash
# build once
npx tailwindcss -i ./src/input.css -o ./src/output.css

# dev + watch
npx tailwindcss -i ./src/input.css -o ./src/output.css --watch

# production (minified)
npx tailwindcss -i ./src/input.css -o ./src/output.css --minify
```

Serve locally

```bash
# Python 3 static server
python3 -m http.server 8000

# open http://localhost:8000
```

Suggested `package.json` scripts (optional)

```json
"scripts": {
  "build:css": "npx tailwindcss -i ./src/input.css -o ./src/output.css",
  "watch:css": "npx tailwindcss -i ./src/input.css -o ./src/output.css --watch",
  "build:css:prod": "npx tailwindcss -i ./src/input.css -o ./src/output.css --minify"
}
```

## File map (important files)

- `index.html` — Main UI markup. Contains the 3-column layout and component stubs.
- `src/input.css` — Tailwind entry (only contains the Tailwind import).
- `src/output.css` — Compiled Tailwind CSS (ready-to-use; large file committed to avoid a required build step).
- `package.json` — Lists `tailwindcss` and `@tailwindcss/cli` as dependencies.

If you edit markup and need new utilities (e.g., arbitrary values), rebuild `src/output.css` with the CLI.

## Common troubleshooting

- Divider not visible: avoid `h-[1px]` unless arbitrary values enabled; prefer `h-px` or `<hr class="border-t border-gray-700" />`.
- Hover border shifts neighbors: use `border border-transparent` by default and only change color on hover.
- Icons/text alignment at breakpoints: ensure container alignment (`items-center`) and use responsive utilities (`md:w-fit`, `md:justify-center`, `md:px-0`).

## Accessibility recommendations

- Use semantic markup: wrap navigation with `<nav>` and use anchor tags (`<a>`) inside `<li>` elements.
- Add `aria-label` on navigation and `alt` on images.
- Ensure color contrast meets WCAG AA for interactive states.

## Possible improvements / next steps

1. Semantic navigation & keyboard support
   - Convert `<li>` items into `<a>` links; add `role`/`aria` attributes and keyboard focus styles.
2. Build automation
   - Add `npm` scripts (example above) and optionally a small `dev` script that runs `watch:css` plus a static server.
3. Component cleanup
   - Extract repeated utilities to a small CSS file or use Tailwind's `@apply` to create reusable classes.
4. Tests & CI
   - Add a linting step (HTML/CSS) and a minimal CI workflow that verifies the site builds.

## How I validated the project

- Inspected `index.html` to confirm layout and responsive patterns.
- Verified `package.json` lists Tailwind dependencies.
- Reviewed `src/output.css` to ensure the compiled utilities exist; this means you can open `index.html` without rebuilding.

---

If you want, I can:

- Add the recommended `npm` scripts to `package.json`.
- Convert the sidebar to semantic `<nav>` + `<a>` with improved accessibility.
- Make the nav fully responsive (collapse to icons-only on small screens).

Tell me which follow-ups you'd like and I'll implement them.
