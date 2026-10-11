# ⬡ IMC TITAN — GNOME Theme
### Titanfall 2 / IMC Interface Aesthetic for Ubuntu

---

A dark military-tech GNOME theme drawing directly from the Titanfall 2 HUD design language:
angular geometry, deep navy blacks, glowing cyan energy accents, orange alert states, and monospaced UI typography. Built for pilots who demand their desktop look like an IMC combat interface.

---

## What's Included

| File | Purpose |
|------|---------|
| `gtk-3.0/gtk.css` | Full GTK3 theme (most GNOME apps) |
| `gtk-3.0/widgets.css` | Extended widget overrides |
| `gtk-4.0/gtk.css` | GTK4 / libadwaita theme |
| `gnome-shell/gnome-shell.css` | Top bar, overview, notifications, OSD |
| `imc-titan-alacritty.toml` | Alacritty terminal color scheme |
| `install-terminal-colors.sh` | GNOME Terminal color profile installer |
| `install.sh` | **Main installer — run this** |

---

## Quick Install

```bash
# 1. Clone or extract this folder somewhere permanent
mkdir -p ~/.local/share/themes
cp -r IMC-Titan-Theme ~/.local/share/themes/IMC-Titan

# 2. Run the installer
cd IMC-Titan-Theme
chmod +x install.sh
./install.sh
```

---

## Manual Installation

### GTK Theme
```bash
mkdir -p ~/.local/share/themes/IMC-Titan/gtk-3.0
mkdir -p ~/.local/share/themes/IMC-Titan/gtk-4.0
cp gtk-3.0/gtk.css gtk-3.0/widgets.css ~/.local/share/themes/IMC-Titan/gtk-3.0/
cp gtk-4.0/gtk.css ~/.local/share/themes/IMC-Titan/gtk-4.0/
cp index.theme ~/.local/share/themes/IMC-Titan/

# Apply
gsettings set org.gnome.desktop.interface gtk-theme "IMC-Titan"
gsettings set org.gnome.desktop.interface color-scheme "prefer-dark"
```

### GTK4 (Flatpak / libadwaita apps)
```bash
mkdir -p ~/.config/gtk-4.0
cp gtk-4.0/gtk.css ~/.config/gtk-4.0/gtk.css
```

### GNOME Shell Theme
Requires the **User Themes** extension:
```bash
sudo apt install gnome-shell-extensions
gnome-extensions enable user-theme@gnome-shell-extensions.gcampax.github.com

mkdir -p ~/.local/share/themes/IMC-Titan/gnome-shell
cp gnome-shell/gnome-shell.css ~/.local/share/themes/IMC-Titan/gnome-shell/

gsettings set org.gnome.shell.extensions.user-theme name "IMC-Titan"
```

### GNOME Terminal Colors
```bash
chmod +x install-terminal-colors.sh
./install-terminal-colors.sh
# Then: Terminal → Preferences → Profiles → Select "IMC-Titan"
```

### Alacritty
```bash
cp imc-titan-alacritty.toml ~/.config/alacritty/
# Add to your alacritty.toml:
echo 'import = ["~/.config/alacritty/imc-titan.toml"]' >> ~/.config/alacritty/alacritty.toml
```

---

## Recommended Fonts

Install for the authentic IMC HUD look:

```bash
# From Google Fonts (download and install manually):
# https://fonts.google.com/specimen/Share+Tech+Mono  ← monospace UI font
# https://fonts.google.com/specimen/Exo+2            ← display/heading font

# Or via package manager (close alternatives):
sudo apt install fonts-liberation fonts-dejavu-core

# After installing fonts, refresh font cache:
fc-cache -fv
```

Apply fonts:
```bash
gsettings set org.gnome.desktop.interface font-name "Exo 2 10"
gsettings set org.gnome.desktop.interface monospace-font-name "Share Tech Mono 11"
gsettings set org.gnome.desktop.interface document-font-name "Exo 2 10"
```

---

## Fine-Tuning with GNOME Tweaks

```bash
sudo apt install gnome-tweaks
gnome-tweaks
```

Navigate to:
- **Appearance** → Shell: `IMC-Titan`, Applications: `IMC-Titan`
- **Fonts** → set Interface and Monospace fonts
- **Window Titlebars** → Placement: Left

---

## Color Reference

| Token | Hex | Use |
|-------|-----|-----|
| bg-darkest | `#080c10` | Terminal bg, panel bg |
| bg-dark | `#0d1117` | Window background |
| bg-panel | `#111922` | Sidebars, menus |
| bg-elevated | `#1c2a3a` | Buttons, cards |
| cyan-base | `#00c8e0` | Primary accent — focus, active |
| cyan-bright | `#40e8ff` | Text on cyan, glow |
| orange-base | `#e05c00` | Warnings, secondary accents |
| accent-green | `#00e080` | Success, health, online |
| accent-red | `#e02040` | Errors, destroy, critical |
| text-primary | `#c8dce8` | Main body text |
| text-secondary | `#6a90a8` | Dimmed labels |

---

## Compatibility

| Component | Status |
|-----------|--------|
| GTK 3.20+ | ✓ Full support |
| GTK 4 / libadwaita | ✓ CSS variables |
| GNOME Shell 44–47 | ✓ (via User Themes ext) |
| GNOME Tweaks | ✓ |
| Nautilus (Files) | ✓ |
| GNOME Terminal | ✓ (color profile) |
| Alacritty | ✓ (TOML config) |
| Flatpak apps | Partial (GTK4 only) |

---

## Troubleshooting

**GTK4 apps not themed:**
Ensure `~/.config/gtk-4.0/gtk.css` exists. Some Flatpak apps ignore system themes by design — override with:
```bash
sudo flatpak override --filesystem=xdg-config/gtk-4.0
```

**Shell theme not applying:**
Confirm User Themes extension is enabled:
```bash
gnome-extensions list --enabled | grep user-theme
```

**Fonts look wrong:**
Install Share Tech Mono and Exo 2 from Google Fonts, then run `fc-cache -fv`.

---

*"The Frontier awaits, Pilot."*
