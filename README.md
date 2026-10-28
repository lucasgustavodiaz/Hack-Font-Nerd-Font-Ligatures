# Hack Nerd Font with Ligatures

**Hack’s clean look. The ligatures I love. Nerd Font icons where I need them.**

This is my personal font setup for the terminal: Hack 3.003, with programming ligatures and Nerd Font glyphs patched in. The Nerd Font patcher adds the icons to the ligature-enabled font; it does not need to remove the ligatures.

## What’s in here?

| Folder | What it contains |
| --- | --- |
| `Hack 3.003 Ligatures/` | Base Hack 3.003 fonts with ligatures, from [vikky49/patchedFonts-Ligatures](https://github.com/vikky49/patchedFonts-Ligatures). |
| `Hack NF v3.0.2/` | My fonts patched with Nerd Fonts v3.0.2. |
| `Hack NF v3.2.1/` | My fonts patched with Nerd Fonts v3.2.1. |
| `Hack NF v3.5.1/` | My latest fonts, patched with Nerd Fonts Patcher v3.5.1. |

Each folder version refers to the Nerd Fonts Patcher version, not Hack. The v3.5.1 folder contains both Nerd Font and Nerd Font Mono builds in Regular, Bold, Italic, and Bold Italic styles. The instructions below use a version variable so they can be reused with future patcher releases.

## Make your own

### 1. Get the tools

- Hack 3.003 fonts with ligatures from [`vikky49/patchedFonts-Ligatures`](https://github.com/vikky49/patchedFonts-Ligatures).
- [Nerd Fonts Patcher releases](https://github.com/ryanoasis/nerd-fonts/releases): choose a version and download its complete `FontPatcher.zip`. The script needs the other files in the archive too. For repeatable builds, use the same patcher version and record it in the output folder name.
- FontForge and its Python bindings. On Debian or Ubuntu:

  ```bash
  sudo apt update
  sudo apt install fontforge python3-fontforge
  ```

### 2. Patch the fonts

Run these commands from the directory where you extracted `FontPatcher.zip`. Set `NF_VERSION` to the patcher version you downloaded, then update the input path if yours is different. For the currently included build, use `3.5.1`; when updating the patcher, change the version to match.

```bash
NF_VERSION="3.5.1"
OUTPUT_DIR="$HOME/Hack-NF-v${NF_VERSION}"
mkdir -p "$OUTPUT_DIR"

# Nerd Font: all icons, regular icon widths
python3 font-patcher "$HOME/Hack 3.003 Ligatures/Hack-Regular.ttf" \
  -c -out "$OUTPUT_DIR"

# Nerd Font Mono: all icons, monospaced icon widths
python3 font-patcher "$HOME/Hack 3.003 Ligatures/Hack-Regular.ttf" \
  -c --mono -out "$OUTPUT_DIR"
```

For each remaining base style, replace `Hack-Regular.ttf` in both commands with:

```text
Hack-Bold.ttf
Hack-Italic.ttf
Hack-BoldItalic.ttf
```

The four input files give you Regular, Bold, Italic, and Bold Italic in both Nerd Font and Nerd Font Mono variants. The patcher names the generated files; `--mono` produces names containing `NerdFontMono`. When using a newer patcher, keep the previous build and use a new versioned output folder so the results remain easy to compare.

### 3. Enjoy the result

Install the generated `.ttf` files, select the font in your terminal, and make sure terminal ligatures are enabled. Try a few code ligatures and Nerd Font icons to check everything looks right.

## A couple of notes

- The ligatures come from the input font and are preserved by default. Avoid `--removeligatures`.
- `-c` adds all available icon sets. `--mono` makes the added icon glyphs monospaced; it does not change the original letters.
- The patcher may print glyph-name or table warnings while running. If it finishes with `Done with Patch Sets, generating font...` and reports the output `.ttf`, the font was generated; still, test the result in your terminal.
- Keep the original font licenses and notices when sharing generated files.

## Credits

- [Hack](https://github.com/source-foundry/Hack)
- [Hack with ligatures](https://github.com/vikky49/patchedFonts-Ligatures)
- [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts)
