# Publication Notes

Prepared assets for the official Typora theme gallery:

- `submission/typora-theme-gallery/_posts/theme/2026-05-09-Blue-Topaz.md`
- `submission/typora-theme-gallery/media/thumbnails/blue-topaz.png`
- `submission/typora-theme-gallery/media/theme/blue-topaz/blue-topaz-preview.png`

Official Typora submission requirements checked:

- Theme CSS filenames are lowercase and use hyphens.
- Default font size is set on `html`.
- Heading sizes use `rem`.
- The post uses `layout: theme`, `category: theme`, `homepage`, `download`, `author`, `thumbnail`, `typora-root-url`, and `typora-copy-images-to`.
- Thumbnail is 500x400.

Current blocker before public publishing:

- `gh auth status` still reports the `Nicozheng` token as invalid in this Codex session.

Font publishing decision:

- `blue-topaz/PingFangSC-Regular.otf` was removed from the public package because its embedded metadata includes "All rights reserved" and "PingFang is a trademark of Apple Inc."
- `blue-topaz/Bookerly-Regular.ttf` was removed from the public package because redistribution permission is unclear.
- Bookerly and PingFang SC remain in the CSS font stack as local/system font preferences.
