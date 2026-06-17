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
```

Built for Tailwind v4 (`@theme` / `@theme inline`) + shadcn token vars. No
bundled webfont — `--font-sans` falls back to Helvetica Neue / Arial by design.

## Updating tokens

1. Edit `tokens.css` in this repo, commit, push.
2. In each consuming app: `git submodule update --remote cw-style` then commit
   the bumped submodule pointer.
