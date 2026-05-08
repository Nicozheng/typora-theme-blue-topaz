# Blue Topaz Typora Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build four Typora themes that port Blue Topaz document styling into light/dark and numbered/non-numbered variants.

**Architecture:** Use one shared Typora CSS base for typography, Markdown elements, and Typora UI selectors. Each public theme file imports the base and sets only palette variables plus heading counter behavior, keeping the four variants small and consistent.

**Tech Stack:** CSS for Typora themes, bundled local font assets, static HTML preview for verification, Git for checkpoints.

---

## File Structure

- Create `blue-topaz/blue-topaz-base.css`: shared `@font-face` declarations, document layout, Markdown element styling, Typora UI polish, alert/callout-like blocks, and numbered/non-numbered counter rules keyed by CSS variables.
- Create `blue-topaz.css`: light numbered public Typora theme entrypoint.
- Create `blue-topaz-nonum.css`: light non-numbered public Typora theme entrypoint.
- Create `blue-topaz-dark.css`: dark numbered public Typora theme entrypoint.
- Create `blue-topaz-dark-nonum.css`: dark non-numbered public Typora theme entrypoint.
- Copy font assets from `resources/example_theme/blueTex/` into `blue-topaz/`.
- Create `preview/blue-topaz-preview.html`: static verification page with four render panes.
- Create `preview/blue-topaz-preview.css`: preview-only layout CSS that imports the four theme files into scoped panes.

## Task 1: Create Theme Assets

**Files:**
- Create: `blue-topaz/Bookerly-Regular.ttf`
- Create: `blue-topaz/PingFangSC-Regular.otf`
- Create: `blue-topaz/CascadiaCode.woff2`
- Create: `blue-topaz/MapleMono-NF-CN-Regular.woff2`

- [ ] **Step 1: Copy font assets**

Run:

```bash
mkdir -p blue-topaz
cp resources/example_theme/blueTex/Bookerly-Regular.ttf blue-topaz/Bookerly-Regular.ttf
cp resources/example_theme/blueTex/PingFangSC-Regular.otf blue-topaz/PingFangSC-Regular.otf
cp resources/example_theme/blueTex/CascadiaCode.woff2 blue-topaz/CascadiaCode.woff2
cp resources/example_theme/blueTex/MapleMono-NF-CN-Regular.woff2 blue-topaz/MapleMono-NF-CN-Regular.woff2
```

Expected: the four files exist under `blue-topaz/`.

- [ ] **Step 2: Verify copied assets**

Run:

```bash
ls -lh blue-topaz/Bookerly-Regular.ttf blue-topaz/PingFangSC-Regular.otf blue-topaz/CascadiaCode.woff2 blue-topaz/MapleMono-NF-CN-Regular.woff2
```

Expected: all four font files are listed with non-zero sizes.

- [ ] **Step 3: Commit assets**

Run:

```bash
git add blue-topaz/Bookerly-Regular.ttf blue-topaz/PingFangSC-Regular.otf blue-topaz/CascadiaCode.woff2 blue-topaz/MapleMono-NF-CN-Regular.woff2
git commit -m "Add Blue Topaz Typora font assets"
```

Expected: a commit containing only the copied font assets.

## Task 2: Build Shared Typora Base CSS

**Files:**
- Create: `blue-topaz/blue-topaz-base.css`

- [ ] **Step 1: Create the base CSS**

Write `blue-topaz/blue-topaz-base.css` with:

```css
/*
Partial style(s) is(are) sourced or adapted from Blue Topaz (https://github.com/PKM-er/Blue-Topaz_Obsidian-css), and I would like to express my appreciation to WhyI (https://github.com/whyt-byte) and pkmer.cn (https://pkmer.cn).
*/

@font-face {
  font-family: "Bookerly";
  src: url("Bookerly-Regular.ttf");
}

@font-face {
  font-family: "PingFang SC";
  src: url("PingFangSC-Regular.otf");
}

@font-face {
  font-family: "Cascadia Code";
  src: url("CascadiaCode.woff2");
}

@font-face {
  font-family: "Maple Mono NF CN";
  src: url("MapleMono-NF-CN-Regular.woff2");
}

:root {
  --bt-font-text: Bookerly, "Inter", "Segoe UI", "LXGW WenKai Screen", "LXGW WenKai Screen R", "霞鹜文楷 GB", "LXGW WenKai", "PingFang SC", "Segoe UI Emoji", serif;
  --bt-font-code: "Maple Mono NF CN", "Cascadia Code", "JetBrains Mono", Consolas, Monaco, "Microsoft YaHei Mono", monospace;
  --bt-line-height: 1.5;
  --bt-content-width: 960px;
  --bt-bottom-padding: 10em;
  --bt-radius-s: 5px;
  --bt-radius-m: 7px;
  --bt-radius-l: 10px;
}
```

Then add the shared document selectors for `html`, `body`, `#write`, headings, links, lists, blockquotes, tables, emphasis, inline code, fenced code, checkboxes, metadata blocks, footnotes, alerts, outline/sidebar, print rules, and heading counter behavior.

- [ ] **Step 2: Verify CSS syntax by searching for accidental placeholders**

Run:

```bash
rg -n "TBD|TODO|PLACEHOLDER|undefined" blue-topaz/blue-topaz-base.css
```

Expected: no matches.

- [ ] **Step 3: Commit base CSS**

Run:

```bash
git add blue-topaz/blue-topaz-base.css
git commit -m "Add shared Blue Topaz Typora base CSS"
```

Expected: a commit containing the base CSS.

## Task 3: Build Four Public Theme Entrypoints

**Files:**
- Create: `blue-topaz.css`
- Create: `blue-topaz-nonum.css`
- Create: `blue-topaz-dark.css`
- Create: `blue-topaz-dark-nonum.css`

- [ ] **Step 1: Create light numbered entrypoint**

Write `blue-topaz.css`:

```css
@import url("blue-topaz/blue-topaz-base.css");

:root {
  --bt-number-headings: "";
  --bt-bg: #ffffff;
  --bt-bg-alt: #e9e9e9;
  --bt-surface: #fcfcfc;
  --bt-surface-alt: #f3f3f3;
  --bt-text: #0e0e0e;
  --bt-muted: #7f7f7f;
  --bt-border: #dddddd;
  --bt-accent-rgb: 70, 142, 235;
  --bt-accent: #468eeb;
  --bt-accent-hover: #237add;
  --bt-strong: #F25F5F;
  --bt-em: #519A00;
  --bt-strong-em: #B166EC;
  --bt-h1: hsl(216, 88%, 26%);
  --bt-h2: hsl(212, 100%, 33%);
  --bt-h3: hsl(210, 86%, 39%);
  --bt-h4: hsl(208, 58%, 49%);
  --bt-h5: hsl(209, 70%, 62%);
  --bt-h6: hsl(209, 65%, 72%);
  --bt-code-bg: #e6e6e671;
  --bt-code-text: #e95d00;
  --bt-quote-bg: #468eeb14;
  --bt-quote-border: #468eeb;
  --bt-green-note-bg: #79c95512;
  --bt-green-note-border: #2f7f2e;
}
```

- [ ] **Step 2: Create light non-numbered entrypoint**

Write `blue-topaz-nonum.css` using the *same* light variables as `blue-topaz.css`, but set:

```css
--bt-number-headings: none;
```

- [ ] **Step 3: Create dark numbered entrypoint**

Write `blue-topaz-dark.css` with:

```css
@import url("blue-topaz/blue-topaz-base.css");

:root {
  --bt-number-headings: "";
  --bt-bg: #202020;
  --bt-bg-alt: #444444;
  --bt-surface: #151515;
  --bt-surface-alt: #000000;
  --bt-text: #c6c6c6;
  --bt-muted: #8a8a8a;
  --bt-border: #343434;
  --bt-accent-rgb: 45, 130, 204;
  --bt-accent: #2d82cc;
  --bt-accent-hover: #55a2d6;
  --bt-strong: #F25F5F;
  --bt-em: #519A00;
  --bt-strong-em: #B166EC;
  --bt-h1: hsl(78, 62%, 47%);
  --bt-h2: hsl(118, 42%, 49%);
  --bt-h3: hsl(180, 53%, 48%);
  --bt-h4: hsl(216, 69%, 68%);
  --bt-h5: hsl(258, 79%, 77%);
  --bt-h6: hsl(290, 85%, 81%);
  --bt-code-bg: #2b2b2b;
  --bt-code-text: #ffb86c;
  --bt-quote-bg: #79c95512;
  --bt-quote-border: #2f7f2e;
  --bt-green-note-bg: #79c95512;
  --bt-green-note-border: #2f7f2e;
}
```

- [ ] **Step 4: Create dark non-numbered entrypoint**

Write `blue-topaz-dark-nonum.css` using the same dark variables as `blue-topaz-dark.css`, but set:

```css
--bt-number-headings: none;
```

- [ ] **Step 5: Commit public themes**

Run:

```bash
git add blue-topaz.css blue-topaz-nonum.css blue-topaz-dark.css blue-topaz-dark-nonum.css
git commit -m "Add Blue Topaz Typora theme variants"
```

Expected: a commit containing the four theme entrypoints.

## Task 4: Create Verification Preview

**Files:**
- Create: `preview/blue-topaz-preview.html`
- Create: `preview/blue-topaz-preview.css`

- [ ] **Step 1: Create preview CSS**

Write `preview/blue-topaz-preview.css` with a four-pane layout and scoped imports:

```css
@import url("../blue-topaz.css");

body {
  margin: 0;
  background: #111;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}
```

Then add pane wrappers that allow visual comparison of all four generated themes. If selector scoping becomes unreliable with `@import`, use four iframes in the HTML instead.

- [ ] **Step 2: Create preview HTML**

Write `preview/blue-topaz-preview.html` with four iframes, each loading the same sample Markdown-like HTML document but linked to one of the four theme files.

The sample content must include H1-H6, paragraphs, links, bold, italic, bold italic, mark, delete, ordered and unordered lists, task checkboxes, blockquotes, tables, inline code, fenced code, metadata block, footnote-like text, horizontal rule, images, and `.md-alert` variants.

- [ ] **Step 3: Open preview locally**

Run:

```bash
open preview/blue-topaz-preview.html
```

Expected: browser opens the preview page. If `open` is unavailable, use the in-app browser or a static file URL.

- [ ] **Step 4: Commit preview**

Run:

```bash
git add preview/blue-topaz-preview.html preview/blue-topaz-preview.css
git commit -m "Add Blue Topaz Typora preview"
```

Expected: a commit containing the preview files.

## Task 5: Verify and Finalize

**Files:**
- Modify only if verification finds issues: theme CSS files and preview files.

- [ ] **Step 1: Run repository checks**

Run:

```bash
git diff --check
rg -n "TBD|TODO|PLACEHOLDER|undefined" blue-topaz*.css blue-topaz preview docs
```

Expected: no whitespace errors and no placeholder matches.

- [ ] **Step 2: Inspect generated theme files**

Run:

```bash
ls -lh blue-topaz.css blue-topaz-nonum.css blue-topaz-dark.css blue-topaz-dark-nonum.css blue-topaz/blue-topaz-base.css
```

Expected: all five CSS files are present and non-empty.

- [ ] **Step 3: Review visual output**

Use the browser preview to check:

- Light headings are blue.
- Dark headings are green/cyan/purple in the Blue Topaz direction.
- Bold, italic, and bold italic use the user's customization in all four panes.
- Numbered themes show H2/H3/H4 counters.
- Non-numbered themes do not show generated counters.
- Dark quote/alert blocks use very light green tint and deeper green left bar.

- [ ] **Step 4: Commit any verification fixes**

If any CSS or preview adjustments were needed, run:

```bash
git add blue-topaz.css blue-topaz-nonum.css blue-topaz-dark.css blue-topaz-dark-nonum.css blue-topaz/blue-topaz-base.css preview/blue-topaz-preview.html preview/blue-topaz-preview.css
git commit -m "Polish Blue Topaz Typora themes"
```

Expected: either a polish commit exists, or no changes remain after verification.
