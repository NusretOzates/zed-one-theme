# Zed One Theme for Cursor / VS Code

Port of [Zed](https://zed.dev)’s built-in **One Dark** and **One Light** colors to Cursor and VS Code, with matching editor settings (Lilex font, size, line height, ligatures).

| Theme | Appearance |
|-------|------------|
| **Zed One Dark** | Dark |
| **Zed One Light** | Light |

Colors are taken from Zed’s embedded One Dark / One Light theme (not a generic Atom One Dark clone).

---

## Install

### 1. Font (Lilex)

Zed’s default mono font is **Lilex** (`.ZedMono`).

Download: https://github.com/mishamyrt/Lilex/releases/latest → `Lilex.zip`

**macOS** — double-click the `.ttf` files → Install Font, or copy to `~/Library/Fonts/`

**Linux**
```bash
mkdir -p ~/.local/share/fonts/lilex
cp /path/to/Lilex/ttf/*.ttf ~/.local/share/fonts/lilex/
fc-cache -f
```

**Windows** — select the `.ttf` files → right-click → **Install**

### 2. Theme

#### Option A — Install from VSIX (releases)

1. Download the latest `.vsix` from [Releases](../../releases)
2. Cursor / VS Code → Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`)
3. **Extensions: Install from VSIX...**
4. Pick the downloaded file → reload

#### Option B — Clone into extensions folder

```bash
git clone https://github.com/NusretOzates/zed-one-theme.git
```

| OS | Copy / clone into |
|----|-------------------|
| **macOS / Linux** | `~/.cursor/extensions/zed-one-theme/` |
| **Windows** | `%USERPROFILE%\.cursor\extensions\zed-one-theme\` |

Folder layout must be:

```text
zed-one-theme/
├── package.json
└── themes/
    ├── zed-one-dark-color-theme.json
    └── zed-one-light-color-theme.json
```

Then **Developer: Reload Window**.

#### Option C — From this repo with `vsce` (maintainers)

```bash
npx @vscode/vsce package
# then Install from VSIX
```

### 3. Settings

Command Palette → **Preferences: Open User Settings (JSON)** and merge keys from [`cursor-settings-snippet.json`](cursor-settings-snippet.json):

```json
{
  "window.autoDetectColorScheme": true,
  "workbench.preferredDarkColorTheme": "Zed One Dark",
  "workbench.preferredLightColorTheme": "Zed One Light",
  "workbench.colorTheme": "Zed One Dark",

  "editor.fontFamily": "Lilex, Menlo, Monaco, Consolas, 'Courier New', monospace",
  "editor.fontSize": 15,
  "editor.fontWeight": "400",
  "editor.lineHeight": 1.618,
  "editor.fontLigatures": "'calt', 'liga'",
  "editor.semanticHighlighting.enabled": true,

  "terminal.integrated.fontFamily": "Lilex, Menlo, Monaco, Consolas, monospace",
  "terminal.integrated.fontSize": 15,
  "terminal.integrated.fontWeight": "400",

  "editor.minimap.enabled": true,
  "editor.minimap.renderCharacters": false,
  "editor.renderLineHighlight": "line",
  "editor.guides.indentation": true,
  "breadcrumbs.enabled": true,
  "python.analysis.semanticHighlighting": true
}
```

`settings.json` locations:

| OS | Path |
|----|------|
| **macOS** | `~/Library/Application Support/Cursor/User/settings.json` |
| **Linux** | `~/.config/Cursor/User/settings.json` |
| **Windows** | `%APPDATA%\Cursor\User\settings.json` |

Reload: **Developer: Reload Window**. Pick **Zed One Dark** under **Preferences: Color Theme** if needed.

---

## Checklist

- [ ] Lilex installed
- [ ] Theme installed
- [ ] Settings merged
- [ ] Window reloaded

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Theme missing from list | Reload; confirm `package.json` is at the extension root |
| Wrong font / no `->` ligatures | Install Lilex system-wide; fully quit and reopen Cursor |
| Colors look like Atom One Dark | Select **Zed One Dark** specifically |
| Linux: font not found | `fc-cache -f` then restart Cursor |

---

## Uninstall / revert

To undo everything and go back to Cursor’s defaults (or your previous look):

### 1. Switch theme away from Zed One

Command Palette → **Preferences: Color Theme** → pick any other theme (e.g. **Dark Modern**).

Or in `settings.json`, change/remove:

```json
"workbench.colorTheme": "Zed One Dark",
"workbench.preferredDarkColorTheme": "Zed One Dark",
"workbench.preferredLightColorTheme": "Zed One Light"
```

### 2. Remove the theme extension

**If installed via VSIX:** Extensions sidebar → find **Zed One Theme** → gear → **Uninstall** → reload.

**If installed by folder copy**, delete the extension directory:

| OS | Path |
|----|------|
| **macOS / Linux** | `~/.cursor/extensions/zed-one-theme/` (or `zed-one-theme-1.0.3/`) |
| **Windows** | `%USERPROFILE%\.cursor\extensions\zed-one-theme\` |

Then **Developer: Reload Window**.

### 3. Revert settings (optional)

In `settings.json`, remove or restore the keys you added from `cursor-settings-snippet.json`, especially:

- `editor.fontFamily` / `editor.fontSize` / `editor.lineHeight` / `editor.fontLigatures`
- `terminal.integrated.fontFamily` / `terminal.integrated.fontSize`
- the `workbench.*ColorTheme` keys above

If you kept a backup of `settings.json` from before installing, replace the file with that backup.

### 4. Uninstall Lilex (optional)

Only needed if you don’t want the font on the system anymore.

| OS | How |
|----|-----|
| **macOS** | Font Book → find **Lilex** → right-click → **Remove** |
| **Linux** | `rm -rf ~/.local/share/fonts/lilex && fc-cache -f` |
| **Windows** | Settings → Personalization → Fonts → **Lilex** → Uninstall |

---

## Credits

- Color values from [Zed](https://zed.dev) One Dark / One Light (`assets/themes/one/one.json`)
- Font: [Lilex](https://github.com/mishamyrt/Lilex) by Mishamyrt (OFL)
- One Dark lineage: Atom One Dark

Not affiliated with Zed Industries.
