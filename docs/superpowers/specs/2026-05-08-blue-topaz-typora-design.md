# Blue Topaz Typora Theme Design

## Goal

Create four Typora themes that migrate the readable-document parts of Blue Topaz from Obsidian into Typora:

- `blue-topaz.css`: light palette with generated heading numbers.
- `blue-topaz-nonum.css`: light palette without generated heading numbers.
- `blue-topaz-dark.css`: dark palette with generated heading numbers.
- `blue-topaz-dark-nonum.css`: dark palette without generated heading numbers.

The themes should prioritize the writing pane and Markdown document rendering. Obsidian-only surfaces such as sidebars, graph view, panes, tabs, popovers, command palette, and plugin-specific callouts are out of scope.

## Inputs

Reference sources:

- `resources/Blue-Topaz_Obsidian-css/theme.css` and `resources/Blue-Topaz_Obsidian-css/obsidian.css` for Blue Topaz variables, typography, and colors.
- `resources/style-settings.json` for the user's Blue Topaz customization.
- `resources/example_theme/bluetex.css` and `resources/example_theme/bluetex-nonum.css` for Typora selector patterns and bundled font usage.

User customization to apply to all four themes:

- Main, bold, and italic text use the Bookerly-first font stack from `style-settings.json`.
- Main line height is `1.5`.
- Bold color is `#F25F5F`.
- Italic color is `#519A00`.
- Bold italic color is `#B166EC`.
- Remove Obsidian-style heading indicators; numbered variants should use clean generated heading counters only.
- Bottom writing padding follows the customization intent and should be generous enough for comfortable editing.

## Visual Direction

Light themes use Blue Topaz's default light direction:

- Page background: white to very light gray.
- Body text: near-black.
- Heading ladder: blue tones from deep H1 to lighter lower headings.
- Links and accents: Blue Topaz blue, with warm highlights where appropriate.

Dark themes use Blue Topaz's default dark direction:

- Page background: near-black / charcoal.
- Body text: soft gray.
- Heading ladder: H1 yellow-green, H2 green, H3 cyan, then cooler blue/purple for lower levels.
- Dark callout-like note blocks use a very light green tint with a deeper green left bar, matching the heading direction.

All themes should keep the Blue Topaz feel: compact but comfortable spacing, rounded but restrained blocks, visible accent bars, readable tables, soft code backgrounds, and typographic emphasis colors from the user's customization.

## File Structure

The implementation should avoid duplicating the entire CSS four times. Use:

- A shared base file for fonts, layout, Markdown element styling, and Typora UI selectors.
- Small variant files that import the base and set palette plus heading-number behavior.
- A font asset directory copied from `example_theme/blueTex`.

Expected public theme files:

- `blue-topaz.css`
- `blue-topaz-nonum.css`
- `blue-topaz-dark.css`
- `blue-topaz-dark-nonum.css`

Expected support assets:

- `blue-topaz/Bookerly-Regular.ttf`
- `blue-topaz/PingFangSC-Regular.otf`
- `blue-topaz/CascadiaCode.woff2`
- `blue-topaz/MapleMono-NF-CN-Regular.woff2`
- `blue-topaz/blue-topaz-base.css`

## CSS Behavior

Base CSS should define reusable variables for:

- Font stacks.
- Body text, muted text, page background, surface background, border color.
- Heading colors for H1 through H6.
- Link, mark, quote, table, code, selection, checkbox, and alert colors.
- Radius, line height, content width, and bottom padding.

Numbered variants should:

- Reset counters on `#write`.
- Increment and render counters for H2/H3/H4 in a Typora-compatible way.
- Leave H1 unnumbered, matching the current example theme direction.

Non-numbered variants should:

- Import the same base and palette.
- Disable generated heading counter content.

Typora-specific surfaces should include at least:

- `#write`
- headings and anchor behavior
- paragraphs, lists, task checkboxes
- links, strong, emphasis, mark, delete
- inline code and fenced code blocks
- blockquotes
- tables
- horizontal rules
- footnotes and metadata blocks
- outline/sidebar styling where Typora exposes stable selectors, kept secondary to document styling
- GitHub-style alert blocks through Typora's `.md-alert` selectors

## Testing

Verification should include:

- CSS syntax checks by inspection and, if available, simple parser/lint checks.
- A local HTML preview that exercises headings, lists, task items, tables, quotes, code, links, marks, footnotes, images, and alerts against all four theme files.
- Browser screenshots or visual inspection of the preview for light/dark and numbered/non-numbered variants.
- `git diff --check` before completion.

## Licensing Note

The generated CSS should include the Blue Topaz attribution requested in the upstream theme comments:

> Partial style(s) is(are) sourced or adapted from Blue Topaz (https://github.com/PKM-er/Blue-Topaz_Obsidian-css), and I would like to express my appreciation to WhyI (https://github.com/whyt-byte) and pkmer.cn (https://pkmer.cn).

The implementation should not copy large Obsidian-only sections wholesale. It should port the relevant visual language into Typora-specific CSS.
