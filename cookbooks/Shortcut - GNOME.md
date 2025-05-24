---
classification: public
tags:
  - Linux
  - Furcadia
---

# Prerequisites
* Furcadia installation path: `/home/icedragon/Furcadia`
* Expected command: `cd ~/Furcadia && ./Furcadia.exe`

# Desktop Entry
* Create a file: `~/.local/share/applications/furcadia.desktop`
  ```ini
  [Desktop Entry]
  Type=Application
  Name=Furcadia
  Exec=Furcadia.exe
  Path=/home/icedragon/Furcadia
  Icon=/home/icedragon/Furcadia/icons/Furcadia.png
  Terminal=false
  ```
* Make the file executable: `chmod +x ~/.local/share/applications/furcadia.desktop`

# Extracting Desktop Icon
## Prerequisites
Install the tools to extract `.ico` files from `Furcadia.exe` and convert them
to `.png`.

```sh
# YUM/DNF (RedHat/Fedora)
sudo dnf install icotools imagemagick

# APT (Debian/Ubuntu)
sudo apt install icoutils imagemagick
```

## Extraction
```sh
cd ~/Furcadia

# Extract all available .ico files from Furcadia.exe into icons/
mkdir icons
wrestool -x -t 14 Furcadia.exe -o icons/

# Convert primary icon into .png format (.ico IS NOT supported)
convert Furcadia.exe_14_108_2048.ico Furcadia.png
```
* This will produce multiple `.png` files with different resolutions/qualities!
* Pick the best looking one, rename it to `Furcadia.png` and leave it that way

## Update Icon Cache
Given the Desktop Entry file above, if the icon hasn't updated, you can run the
following:
```sh
gtk-update-icon-cache ~/.local/share/icons
```
