# Blue Topaz Typora Theme

Blue Topaz for Typora ports the readable writing-pane parts of the Blue Topaz Obsidian theme into four Typora theme variants:

- `blue-topaz.css`: light palette with generated heading numbers.
- `blue-topaz-nonum.css`: light palette without generated heading numbers.
- `blue-topaz-dark.css`: dark palette with generated heading numbers.
- `blue-topaz-dark-nonum.css`: dark palette without generated heading numbers.

The shared styling lives in `blue-topaz/blue-topaz-base.css`. The four entrypoint CSS files import that base file and set palette variables plus heading-number behavior.

## Installation

1. In Typora, open `Preferences` -> `Appearance` -> `Open Theme Folder`.
2. Copy the four `blue-topaz*.css` files into the theme folder.
3. Copy the `blue-topaz/` folder into the same theme folder.
4. Restart Typora and choose one of the Blue Topaz themes from the `Themes` menu.

## Preview

Open `preview/blue-topaz-preview.html` in a browser or serve the repository locally and visit:

```sh
python3 -m http.server 8765
```

Then open `http://127.0.0.1:8765/preview/blue-topaz-preview.html`.

## Attribution

Partial styles are sourced or adapted from Blue Topaz:

- Blue Topaz Obsidian CSS: https://github.com/PKM-er/Blue-Topaz_Obsidian-css
- WhyI: https://github.com/whyt-byte
- pkmer.cn: https://pkmer.cn

Code block colors were also informed by Sublime/Monokai-style palettes during development.

## Font Assets

The public package only bundles fonts with redistributable licensing that should be suitable for a theme package. Bookerly and PingFang SC remain in the CSS font stack as local/system font preferences, but their font files are not bundled.
