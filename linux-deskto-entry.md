# 🖥️ Linux Desktop Entry Guide
### Creating `.desktop` Files for Every File Type on Arch Linux + Hyprland

> A complete reference for integrating AppImages, JARs, scripts, binaries, and more into your Hyprland desktop environment.

---

## 📖 Table of Contents

1. [Linux File Types Overview](#linux-file-types-overview)
2. [What is a Desktop Entry?](#what-is-a-desktop-entry)
3. [Desktop Entry Anatomy](#desktop-entry-anatomy)
4. [File Type: Native Binary (ELF)](#1-native-binary-elf)
5. [File Type: AppImage](#2-appimage)
6. [File Type: JAR (Java)](#3-jar-java)
7. [File Type: Shell Script (.sh)](#4-shell-script-sh)
8. [File Type: Python Script (.py)](#5-python-script-py)
9. [File Type: Flatpak](#6-flatpak)
10. [File Type: Snap](#7-snap)
11. [File Type: Wine / .exe (Windows Apps)](#8-wine--exe-windows-apps)
12. [File Type: Electron App](#9-electron-app)
13. [File Type: Web App (Browser Shortcut)](#10-web-app-browser-shortcut)
14. [File Type: Terminal-only App](#11-terminal-only-app)
15. [Icons — Finding & Setting Them](#icons--finding--setting-them)
16. [Automating Desktop Entry Creation](#automating-desktop-entry-creation)
17. [Hyprland-Specific Tips](#hyprland-specific-tips)
18. [Troubleshooting](#troubleshooting)
19. [Quick Reference Cheatsheet](#quick-reference-cheatsheet)

---

## Linux File Types Overview

Linux has **7 fundamental file types** (visible via `ls -l` first character):

| Symbol | Type | Description |
|--------|------|-------------|
| `-` | Regular file | Text, binary, scripts, images, JARs, etc. |
| `d` | Directory | Folder |
| `l` | Symbolic link | Shortcut/alias to another file |
| `c` | Character device | Hardware like keyboard, tty |
| `b` | Block device | Storage like `/dev/sda` |
| `p` | Named pipe (FIFO) | Inter-process communication |
| `s` | Socket | Network/IPC communication |

For desktop entries, we care about **regular files** and their **formats**:

| Format | Extension | Needs | Desktop Entry? |
|--------|-----------|-------|----------------|
| Native Binary | none / `.bin` | Nothing | ✅ Yes |
| AppImage | `.AppImage` | FUSE | ✅ Yes |
| JAR | `.jar` | JRE/JDK | ✅ Yes |
| Shell Script | `.sh` | bash/zsh/sh | ✅ Yes |
| Python Script | `.py` | python | ✅ Yes |
| Flatpak | none | flatpak runtime | ✅ Auto-generated |
| Snap | none | snapd | ✅ Auto-generated |
| Wine App | `.exe` | wine | ✅ Yes |
| Electron App | none / `.js` | Node/Electron | ✅ Yes |
| Web App | URL | Browser | ✅ Yes |

---

## What is a Desktop Entry?

A `.desktop` file is a plain-text configuration file that tells your desktop environment (Hyprland, GNOME, KDE, etc.) how to launch an application. It shows up in:

- App launchers (like `rofi`, `wofi`, `fuzzel`)
- Right-click menus
- `xdg-open` associations
- Taskbars and docks

**Two locations for desktop files:**

```
~/.local/share/applications/     # Per-user (recommended, no sudo)
/usr/share/applications/         # System-wide (requires sudo)
```

---

## Desktop Entry Anatomy

```ini
[Desktop Entry]
# Required fields
Type=Application               # Application | Link | Directory
Name=My App                    # Display name
Exec=/path/to/launch/command   # Command to run

# Highly recommended
Icon=/path/to/icon.png         # Icon path or icon theme name
Comment=A short description    # Tooltip text
Categories=Utility;            # See freedesktop.org for full list

# Optional but useful
Terminal=false                 # true = open in terminal
StartupNotify=true             # Show loading indicator
StartupWMClass=MyApp           # Helps Hyprland match window to icon
MimeType=text/plain;           # File associations
Keywords=tool;utility;         # Search keywords for launchers
NoDisplay=false                # true = hide from launcher
```

### Common Categories

```
AudioVideo, Audio, Video, Development, Education, Game,
Graphics, Network, Office, Science, Settings, System, Utility
```

---

## 1. Native Binary (ELF)

These are compiled executables — the most common type on Linux.

```bash
# Check if a file is ELF binary
file /usr/bin/firefox
# Output: ELF 64-bit LSB executable...
```

**Desktop Entry:**

```ini
[Desktop Entry]
Type=Application
Name=My App
Exec=/opt/myapp/myapp
Icon=/opt/myapp/myapp.png
Comment=My native application
Categories=Utility;
Terminal=false
StartupNotify=true
StartupWMClass=myapp
```

**Install:**
```bash
nano ~/.local/share/applications/myapp.desktop
# paste content, then:
chmod +x ~/.local/share/applications/myapp.desktop
update-desktop-database ~/.local/share/applications/
```

---

## 2. AppImage

AppImages are self-contained portable apps. They require FUSE to run.

**Setup FUSE (one-time):**
```bash
sudo pacman -S fuse2
```

**Make AppImage executable:**
```bash
chmod +x MyApp.AppImage
```

**Recommended: Use `appimaged` or manage manually**
```bash
# Extract icon and desktop file from AppImage (optional)
./MyApp.AppImage --appimage-extract
# Files will be in squashfs-root/
```

**Desktop Entry:**

```ini
[Desktop Entry]
Type=Application
Name=MyApp
Exec=/home/nprime/Applications/MyApp.AppImage --no-sandbox
Icon=/home/nprime/.local/share/icons/myapp.png
Comment=MyApp AppImage
Categories=Utility;
Terminal=false
StartupNotify=true
```

**Pro tip — organize AppImages:**
```bash
mkdir ~/Applications
mv MyApp.AppImage ~/Applications/
chmod +x ~/Applications/MyApp.AppImage
```

**Auto-integrate AppImages with `appimaged`:**
```bash
# Install from AUR
yay -S appimaged
systemctl --user enable --now appimaged
# Now any AppImage in ~/Applications is auto-added to launcher
```

---

## 3. JAR (Java)

JAR files require a Java Runtime Environment (JRE) or JDK.

**Check Java is installed:**
```bash
java -version
archlinux-java status
```

**Basic Desktop Entry:**

```ini
[Desktop Entry]
Type=Application
Name=BurpSuite Pro
Exec=/usr/bin/java -javaagent:/home/nprime/projects/burpsuite_pro_v2025.10.4/BurpLoaderKeygen117.jar -jar /home/nprime/projects/burpsuite_pro_v2025.10.4/burpsuite_pro_v2025.10.4.jar
Icon=/home/nprime/.local/share/icons/burpsuite.png
Comment=Burp Suite Professional
Categories=Network;Security;
Terminal=false
StartupNotify=true
StartupWMClass=burpsuite
```

**With specific Java version:**

```ini
[Desktop Entry]
Type=Application
Name=My Java App
Exec=/usr/lib/jvm/java-21-openjdk/bin/java -Xmx4g -jar /opt/myapp/myapp.jar
Icon=myapp
Comment=Java application
Categories=Utility;
Terminal=false
```

**With wrapper script (recommended for complex args):**

```bash
# Create wrapper: ~/Applications/launch-myapp.sh
#!/bin/bash
export JAVA_HOME=/usr/lib/jvm/java-21-openjdk
$JAVA_HOME/bin/java -Xmx4g -jar /opt/myapp/myapp.jar "$@"
```

```bash
chmod +x ~/Applications/launch-myapp.sh
```

```ini
[Desktop Entry]
Type=Application
Name=My Java App
Exec=/home/nprime/Applications/launch-myapp.sh
Icon=myapp
Terminal=false
```

---

## 4. Shell Script (.sh)

**Make executable first:**
```bash
chmod +x /path/to/script.sh
```

**Desktop Entry:**

```ini
[Desktop Entry]
Type=Application
Name=My Script
Exec=/home/nprime/scripts/myscript.sh
Icon=utilities-terminal
Comment=My shell script
Categories=Utility;
Terminal=false
```

**If the script needs a terminal:**

```ini
[Desktop Entry]
Type=Application
Name=My Script (Terminal)
Exec=alacritty -e /home/nprime/scripts/myscript.sh
Icon=utilities-terminal
Comment=My shell script
Categories=Utility;
Terminal=false
```

> Note: Set `Terminal=false` and specify your terminal emulator in `Exec=` for Hyprland — this gives you control over which terminal opens.

**Common terminal emulators for Exec:**
```bash
Exec=alacritty -e script.sh
Exec=kitty script.sh
Exec=foot script.sh
Exec=wezterm start script.sh
```

---

## 5. Python Script (.py)

**Make executable:**
```bash
chmod +x /path/to/script.py
# Add shebang at top of script:
#!/usr/bin/env python3
```

**Desktop Entry:**

```ini
[Desktop Entry]
Type=Application
Name=My Python App
Exec=/usr/bin/python3 /home/nprime/scripts/myapp.py
Icon=python
Comment=Python application
Categories=Development;Utility;
Terminal=false
StartupNotify=true
```

**With virtual environment:**

```bash
# Wrapper script: ~/scripts/launch-pyapp.sh
#!/bin/bash
source /home/nprime/myapp/venv/bin/activate
python /home/nprime/myapp/main.py
```

```ini
[Desktop Entry]
Type=Application
Name=My Python App
Exec=/home/nprime/scripts/launch-pyapp.sh
Icon=python
Terminal=false
```

---

## 6. Flatpak

Flatpak apps auto-generate desktop entries at install. But here's how to create/customize:

**Install a Flatpak:**
```bash
flatpak install flathub org.example.App
# Desktop entry auto-created at:
# /var/lib/flatpak/exports/share/applications/
```

**Custom Desktop Entry for Flatpak:**

```ini
[Desktop Entry]
Type=Application
Name=My Flatpak App
Exec=flatpak run org.example.App
Icon=org.example.App
Comment=Flatpak application
Categories=Utility;
Terminal=false
```

**Override Flatpak with custom flags:**

```ini
[Desktop Entry]
Type=Application
Name=Firefox (Flatpak)
Exec=flatpak run --env=MOZ_ENABLE_WAYLAND=1 org.mozilla.firefox
Icon=org.mozilla.firefox
Terminal=false
```

---

## 7. Snap

Similar to Flatpak — auto-generates desktop entries.

```bash
sudo pacman -S snapd  # if needed
snap install myapp
# Desktop entry at: /var/lib/snapd/desktop/applications/
```

**Custom Desktop Entry:**

```ini
[Desktop Entry]
Type=Application
Name=My Snap App
Exec=snap run myapp
Icon=/snap/myapp/current/meta/gui/icon.png
Comment=Snap application
Categories=Utility;
Terminal=false
```

---

## 8. Wine / .exe (Windows Apps)

Run Windows `.exe` files on Linux with Wine.

**Install Wine:**
```bash
sudo pacman -S wine wine-mono
```

**Desktop Entry:**

```ini
[Desktop Entry]
Type=Application
Name=My Windows App
Exec=wine /home/nprime/.wine/drive_c/Program\ Files/MyApp/myapp.exe
Icon=/home/nprime/.local/share/icons/myapp.png
Comment=Windows application via Wine
Categories=Utility;
Terminal=false
StartupWMClass=myapp.exe
```

**With environment variables (Wayland fix):**

```ini
[Desktop Entry]
Type=Application
Name=My Windows App
Exec=env WINEPREFIX=/home/nprime/.wine wine /path/to/myapp.exe
Icon=wine
Terminal=false
```

**Using Lutris or Bottles (recommended for complex apps):**
```bash
yay -S lutris
# or
flatpak install com.usebottles.bottles
```

---

## 9. Electron App

Electron apps are essentially Chromium-based desktop apps. They usually come as `.AppImage` or pre-built binaries.

**Desktop Entry:**

```ini
[Desktop Entry]
Type=Application
Name=My Electron App
Exec=/opt/myelectronapp/myelectronapp --enable-features=UseOzonePlatform --ozone-platform=wayland
Icon=/opt/myelectronapp/resources/app/icon.png
Comment=Electron application
Categories=Utility;
Terminal=false
StartupWMClass=myelectronapp
```

> The `--ozone-platform=wayland` flags are important for Hyprland (Wayland compositor).

**Common Electron Wayland flags:**
```bash
--enable-features=UseOzonePlatform
--ozone-platform=wayland
--enable-features=WaylandWindowDecorations
```

---

## 10. Web App (Browser Shortcut)

Create a desktop shortcut that opens a website as a standalone app window.

**Using Chrome/Chromium:**

```ini
[Desktop Entry]
Type=Application
Name=Gmail
Exec=chromium --app=https://mail.google.com --class=Gmail
Icon=gmail
Comment=Gmail Web App
Categories=Network;Email;
Terminal=false
StartupWMClass=Gmail
```

**Using Firefox:**

```ini
[Desktop Entry]
Type=Application
Name=YouTube
Exec=firefox --new-window https://youtube.com
Icon=youtube
Comment=YouTube in Firefox
Categories=AudioVideo;Network;
Terminal=false
```

---

## 11. Terminal-only App

For CLI tools you want quick access to from a launcher.

```ini
[Desktop Entry]
Type=Application
Name=btop
Exec=alacritty -e btop
Icon=utilities-system-monitor
Comment=Resource monitor
Categories=System;Monitor;
Terminal=false
Keywords=monitor;cpu;ram;
```

```ini
[Desktop Entry]
Type=Application
Name=Java Switcher
Exec=alacritty -e java-switch
Icon=java
Comment=Switch Java versions
Categories=Development;System;
Terminal=false
Keywords=java;jdk;switch;
```

---

## Icons — Finding & Setting Them

### Option 1: Use theme icon name (best)
```ini
Icon=firefox          # uses system icon theme
Icon=utilities-terminal
Icon=text-editor
```

Find available icons:
```bash
find /usr/share/icons -name "*.png" | grep -i "java"
ls /usr/share/icons/hicolor/256x256/apps/
```

### Option 2: Absolute path to image
```ini
Icon=/home/nprime/.local/share/icons/myapp.png
```

Store custom icons here:
```bash
mkdir -p ~/.local/share/icons/hicolor/256x256/apps/
cp myapp.png ~/.local/share/icons/hicolor/256x256/apps/
gtk-update-icon-cache ~/.local/share/icons/hicolor/
```

### Option 3: Extract icon from AppImage
```bash
./MyApp.AppImage --appimage-extract
# Icon will be in squashfs-root/
cp squashfs-root/myapp.png ~/.local/share/icons/
```

### Option 4: Extract icon from JAR
```bash
jar xf myapp.jar icon.png
# or
unzip myapp.jar "*.png" -d ./extracted/
```

### Download icons
```bash
# papirus icon pack (excellent coverage)
sudo pacman -S papirus-icon-theme
```

---

## Automating Desktop Entry Creation

### Universal Desktop Entry Creator Script

Save as `~/scripts/mkdesktop.sh`:

```bash
#!/bin/bash

# Universal Desktop Entry Creator
# Usage: mkdesktop.sh

GREEN='\033[0;32m'
CYAN='\033[0;36m'
YELLOW='\033[1;33m'
NC='\033[0m'

DESKTOP_DIR="$HOME/.local/share/applications"
mkdir -p "$DESKTOP_DIR"

echo -e "${CYAN}=== Desktop Entry Creator ===${NC}"
echo ""

read -p "App Name: " NAME
read -p "File path (binary/jar/AppImage/script): " FILE_PATH
read -p "Icon (path or theme name): " ICON
read -p "Comment/Description: " COMMENT
read -p "Categories (e.g. Utility;Development;): " CATEGORIES

# Detect file type and build Exec command
EXT="${FILE_PATH##*.}"
EXEC=""

case "$EXT" in
    jar)
        read -p "Java version (leave blank for system default): " JAVA_VER
        if [ -n "$JAVA_VER" ]; then
            JAVA_BIN="/usr/lib/jvm/java-${JAVA_VER}-openjdk/bin/java"
        else
            JAVA_BIN="java"
        fi
        read -p "Extra java args (e.g. -Xmx4g or javaagent): " JAVA_ARGS
        EXEC="$JAVA_BIN $JAVA_ARGS -jar $FILE_PATH"
        ;;
    AppImage|appimage)
        chmod +x "$FILE_PATH"
        EXEC="$FILE_PATH"
        ;;
    py)
        EXEC="/usr/bin/python3 $FILE_PATH"
        ;;
    sh|bash)
        chmod +x "$FILE_PATH"
        EXEC="$FILE_PATH"
        ;;
    exe)
        EXEC="wine $FILE_PATH"
        ;;
    *)
        chmod +x "$FILE_PATH" 2>/dev/null
        EXEC="$FILE_PATH"
        ;;
esac

echo ""
read -p "Open in terminal? (y/N): " TERM_CHOICE
TERMINAL="false"
[[ "$TERM_CHOICE" =~ ^[Yy]$ ]] && TERMINAL="true"

# Sanitize name for filename
FILENAME=$(echo "$NAME" | tr ' ' '-' | tr '[:upper:]' '[:lower:]')
DESKTOP_FILE="$DESKTOP_DIR/${FILENAME}.desktop"

cat > "$DESKTOP_FILE" << EOF
[Desktop Entry]
Type=Application
Name=$NAME
Exec=$EXEC
Icon=$ICON
Comment=$COMMENT
Categories=${CATEGORIES:-Utility;}
Terminal=$TERMINAL
StartupNotify=true
EOF

chmod +x "$DESKTOP_FILE"
update-desktop-database "$DESKTOP_DIR" 2>/dev/null

echo ""
echo -e "${GREEN}✓ Created: $DESKTOP_FILE${NC}"
echo ""
echo -e "${CYAN}Contents:${NC}"
cat "$DESKTOP_FILE"
```

```bash
chmod +x ~/scripts/mkdesktop.sh
# Install globally
sudo cp ~/scripts/mkdesktop.sh /usr/local/bin/mkdesktop
```

**Usage:**
```bash
mkdesktop
# Follow the prompts — it auto-detects file type!
```

---

## Hyprland-Specific Tips

### 1. Wayland environment variables

Add to `/etc/environment` or `~/.config/hypr/hyprland.conf`:

```bash
# /etc/environment
MOZ_ENABLE_WAYLAND=1          # Firefox
QT_QPA_PLATFORM=wayland       # Qt apps
GDK_BACKEND=wayland           # GTK apps
ELECTRON_OZONE_PLATFORM_HINT=wayland  # Electron apps
```

### 2. Window rules for desktop entry apps

In `~/.config/hypr/hyprland.conf`:

```ini
# Match by StartupWMClass value
windowrulev2 = float, class:^(burpsuite)$
windowrulev2 = size 1280 800, class:^(burpsuite)$
windowrulev2 = workspace 2, class:^(burpsuite)$
```

Find the class name of a running window:
```bash
hyprctl clients | grep -i "class"
# or
xprop WM_CLASS  # click on window
```

### 3. App launcher setup (wofi/rofi/fuzzel)

```bash
# wofi reads ~/.local/share/applications automatically
wofi --show drun

# rofi
rofi -show drun

# fuzzel
fuzzel
```

### 4. Force Wayland in desktop entry

```ini
[Desktop Entry]
Exec=env GDK_BACKEND=wayland myapp
# or for electron:
Exec=myapp --ozone-platform=wayland --enable-features=UseOzonePlatform
```

### 5. XDG autostart (launch app on login)

```bash
cp ~/.local/share/applications/myapp.desktop ~/.config/autostart/
```

---

## Troubleshooting

### Desktop entry not showing in launcher
```bash
# Rebuild desktop database
update-desktop-database ~/.local/share/applications/

# Validate desktop file
desktop-file-validate ~/.local/share/applications/myapp.desktop

# Check for errors
cat ~/.local/share/applications/myapp.desktop
```

### App launches but no icon
```bash
# Rebuild icon cache
gtk-update-icon-cache -f -t ~/.local/share/icons/hicolor/

# Check icon path is correct
ls -la /path/to/your/icon.png
```

### App won't launch from launcher but works in terminal
```bash
# Test exec command directly
bash -c "your-exec-command-here"

# Check permissions
chmod +x /path/to/executable
chmod +x ~/.local/share/applications/myapp.desktop

# Use absolute paths — launchers don't inherit your shell PATH
which java  # get full path
# Use /usr/bin/java not just java in Exec=
```

### Wayland/XWayland issues
```bash
# Check if app is running on Wayland or XWayland
hyprctl clients | grep -A5 "AppName"
# xwayland: 1 = running on XWayland
# xwayland: 0 = native Wayland
```

### JAR won't launch from desktop entry
```bash
# Always use absolute path to java
Exec=/usr/bin/java -jar /full/path/to/app.jar
# NOT: Exec=java -jar app.jar (relative path won't work)
```

---

## Quick Reference Cheatsheet

```bash
# Create desktop entry
nano ~/.local/share/applications/myapp.desktop

# Validate it
desktop-file-validate ~/.local/share/applications/myapp.desktop

# Refresh launcher
update-desktop-database ~/.local/share/applications/

# Find window class (for Hyprland rules)
hyprctl clients | grep class

# Find icon names
find /usr/share/icons -name "*.png" | grep -i "appname"

# Make file executable
chmod +x /path/to/file

# Install icon theme
sudo pacman -S papirus-icon-theme

# Auto-create desktop entry
mkdesktop
```

### Exec= format per file type

| File Type | Exec= Example |
|-----------|---------------|
| Binary | `Exec=/opt/app/app` |
| AppImage | `Exec=/home/user/Apps/App.AppImage` |
| JAR | `Exec=/usr/bin/java -jar /opt/app/app.jar` |
| JAR + agent | `Exec=/usr/bin/java -javaagent:/path/agent.jar -jar /path/app.jar` |
| Shell script | `Exec=/home/user/scripts/app.sh` |
| Python | `Exec=/usr/bin/python3 /home/user/scripts/app.py` |
| Wine .exe | `Exec=wine /home/user/.wine/drive_c/app/app.exe` |
| Flatpak | `Exec=flatpak run org.app.Name` |
| Snap | `Exec=snap run appname` |
| Terminal app | `Exec=alacritty -e appname` |
| Web app | `Exec=chromium --app=https://example.com` |

---

## Resources

- [Freedesktop Desktop Entry Spec](https://specifications.freedesktop.org/desktop-entry-spec/latest/)
- [Arch Wiki — Desktop Entries](https://wiki.archlinux.org/title/Desktop_entries)
- [Arch Wiki — Hyprland](https://wiki.archlinux.org/title/Hyprland)
- [Arch Wiki — Java](https://wiki.archlinux.org/title/Java)
- [XDG Base Directory Spec](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html)

---

*Made for Arch Linux + Hyprland | Covers all major Linux application formats*