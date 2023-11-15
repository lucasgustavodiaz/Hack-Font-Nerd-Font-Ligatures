# Hack Font Nerd Font with Ligatures

This is a patched version of the original [Hack font 3.003](https://github.com/source-foundry/Hack) with the [Nerd Font v3.0.2](https://www.nerdfonts.com/) and Ligatures.

Hack is available on the Nerd Font website, but not the version with ligatures. The ligatured version was provided by [@vikky49](https://github.com/vikky49/patchedFonts-Ligatures).

## Patch applied with [Nerd Font patcher](https://github.com/ryanoasis/nerd-fonts#font-patcher)

Patching the font of your own choosing:

- Use the script
  - Download script and its helper files as [archive](https://github.com/ryanoasis/nerd-fonts/releases/latest/download/FontPatcher.zip) and extract
  - Just downloading the `font-patcher` script is not enough.
  - Requires: Fontforge, Python 3, `python-fontforge` and `argparse` packages
    - Fontforge can be installed as package
    - or on OSX via `brew install fontforge`
    - or as [AppImage](https://github.com/fontforge/fontforge/releases)
  - Usage, recommended:

```bash
  # For Non Mono font with all icons
  python3 font-patcher ./PATH_TO_FONT -c

  # For Mono font with all icons
  python3 font-patcher ./PATH_TO_FONT -c --mono
```

For better results update your terminal icons and oh my posh theme.
