# Zed One Theme for Cursor, VS Code & friends

Port of [Zed](https://zed.dev)’s built-in **One Dark** and **One Light** colors to any editor that runs VS Code extensions (Cursor, VS Code, VSCodium, Windsurf, and similar), with matching editor settings (Lilex font, size, line height, ligatures).

| Theme | Appearance |
|-------|------------|
| **Zed One Dark** | Dark |
| **Zed One Light** | Light |

Colors are taken from Zed’s embedded One Dark / One Light theme (not a generic Atom One Dark clone).

### Language support

**All languages.** This is a full workbench + syntax theme (TextMate scopes + semantic token colors). It is not Python-only.

Python was used while matching Zed screenshots, and the settings snippet includes an optional `python.analysis.semanticHighlighting` key. That line only affects Python/Pylance; you can omit it if you don’t use Python. JS/TS, Rust, Go, JSON, Markdown, etc. all pick up the same palette.

---

## Install

Works the same in **Cursor**, **VS Code**, **VSCodium**, **Windsurf**, and other VS Code–compatible IDEs. Install via VSIX, then merge settings (paths below).

Command Palette shortcuts:

| OS | Shortcut |
|----|----------|
| **macOS** | `Cmd+Shift+P` |
| **Linux / Windows** | `Ctrl+Shift+P` |

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

First download the latest `.vsix` from the [Releases](https://github.com/NusretOzates/zed-one-theme/releases) page (e.g. `zed-one-theme-1.0.3.vsix`).

#### Option A — Install from VSIX in the UI (recommended)

1. Open your editor → Command Palette
2. **Extensions: Install from VSIX...**
3. Pick the downloaded `.vsix` → reload when prompted

#### Option B — Install from VSIX via CLI

1. Download the `.vsix` from [Releases](https://github.com/NusretOzates/zed-one-theme/releases) (same file as above)
2. In a terminal, run one of:

```bash
# VS Code
code --install-extension /path/to/zed-one-theme-1.0.3.vsix

# Cursor
cursor --install-extension /path/to/zed-one-theme-1.0.3.vsix
```

Use the full path to the file you downloaded (or `cd` into that folder first).

### 3. Settings

Command Palette → **Preferences: Open User Settings (JSON)** and merge keys from [`cursor-settings-snippet.json`](cursor-settings-snippet.json) (same snippet works in VS Code and other forks):

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
  "breadcrumbs.enabled": true
}
```

Optional (Python / Pylance only):

```json
"python.analysis.semanticHighlighting": true
```

`settings.json` locations:

| Editor | macOS | Linux | Windows |
|--------|-------|-------|---------|
| **Cursor** | `~/Library/Application Support/Cursor/User/settings.json` | `~/.config/Cursor/User/settings.json` | `%APPDATA%\Cursor\User\settings.json` |
| **VS Code** | `~/Library/Application Support/Code/User/settings.json` | `~/.config/Code/User/settings.json` | `%APPDATA%\Code\User\settings.json` |
| **VSCodium** | `~/Library/Application Support/VSCodium/User/settings.json` | `~/.config/VSCodium/User/settings.json` | `%APPDATA%\VSCodium\User\settings.json` |
| **Windsurf** | `~/Library/Application Support/Windsurf/User/settings.json` | `~/.config/Windsurf/User/settings.json` | `%APPDATA%\Windsurf\User\settings.json` |

Reload: **Developer: Reload Window**. If needed: **Preferences: Color Theme** → **Zed One Dark**.

---

## Checklist

- [ ] Lilex installed
- [ ] Theme installed from VSIX
- [ ] Settings merged
- [ ] Window reloaded

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Theme missing from list | Fully quit and reopen the editor, then **Preferences: Color Theme** → **Zed One Dark**. Reinstall with Option A or B if needed |
| Wrong font / no `->` ligatures | Install Lilex system-wide; fully quit and reopen the editor |
| Colors look like Atom One Dark | Select **Zed One Dark** specifically |
| Linux: font not found | `fc-cache -f` then restart the editor |
| Installed under Cursor but using VS Code | Extensions don’t share across forks — install the VSIX again in that editor |

---

## Uninstall / revert

To undo everything and go back to your previous look:

### 1. Switch theme away from Zed One

Command Palette → **Preferences: Color Theme** → pick any other theme (e.g. **Dark Modern** / **Default Dark Modern**).

Or in `settings.json`, change/remove:

```json
"workbench.colorTheme": "Zed One Dark",
"workbench.preferredDarkColorTheme": "Zed One Dark",
"workbench.preferredLightColorTheme": "Zed One Light"
```

### 2. Remove the theme extension

Extensions sidebar → find **Zed One Theme** → gear → **Uninstall** → reload.

### 3. Revert settings (optional)

In `settings.json`, remove or restore the keys you added from the snippet, especially:

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
