# cw-style

Shared design tokens for the Conceptual Works agency OS. Single source of the
visual language across every node app (MIDA, ARCHIVE, …): Swiss monochrome,
hot-pink reserved for system voice, `--radius: 1px`, Helvetica Neue type.

**Edit here, propagate everywhere.** Apps consume this repo as a git submodule
mounted at `cw-style/` and import the tokens after their framework CSS:

```css
/* src/index.css */
@import "tailwindcss";
@import "tw-animate-css";
@import "shadcn/tailwind.css";
@import "../cw-style/tokens.css";
@import "../cw-style/components.css";
```

Built for Tailwind v4 (`@theme` / `@theme inline`) + shadcn token vars. No
bundled webfont — `--font-sans` falls back to Helvetica Neue / Arial by design.

## Updating tokens

1. Edit `tokens.css` in this repo, run `node scripts/build-v3.mjs` to regenerate
   `tokens-v3.css` (never edit that file by hand), bump `package.json`, commit, tag, push.
2. In each consuming app: `git submodule update --remote cw-style` then commit
   the bumped submodule pointer.

## Tailwind v3 consumers (OSIRIS admin)

`tokens-v3.css` carries the same values as HSL triplets for shadcn/Tailwind v3 apps, scoped to `<html class="cw-style">`. Consumed as a pinned package rather than a submodule:

```
npm install github:conceptualworks/cw-style#v0.3.0
```
then `@import "cw-style/tokens-v3.css";` and `@import "cw-style/components.css";` at the top of `src/index.css`. To roll out a change, bump the ref in each consumer.

## Shared shell (`components.css`)

One definition of the app shell for every app: `.cw-sidebar-brand` (+ `-name`, `-org`),
`.cw-page-header` + `.cw-page-title`, `.cw-nav-item` (active via `.active` or
`aria-current="page"`), and the Hub tiles (`.hub-tile` effects host, `.hub-tile-frame` box, `.hub-tile-live`,
`.hub-tile-locked`, `.hub-corner-*`, `.hub-bar`). Sidebar brand and page header are both
61px tall so their bottom borders meet. It reads only the `--cw-*` aliases, which both
token files define, so it is format-neutral. Accent is CW pink (#E8578F) everywhere.
