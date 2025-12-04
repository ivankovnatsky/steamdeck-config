# a3

## Disk Configuration

Previously installed both Windows and Bazzite separately on the whole disk. Now splitting the 2TB disk equally between both systems to compare game performance. Starting with Windows installation on unallocated space.

Note: For Bazzite installation, the second partition must be unallocated (not formatted as new volume) for Bazzite to auto-partition it and continue with installation.

### Dual Boot - GRUB Configuration

After Bazzite installation, regenerate GRUB to detect Windows:

```console
ujust regenerate-grub
```

Reference: https://docs.bazzite.gg/General/Installation_Guide/dual_boot_setup_guide/

## OS

Bazzite

## During installation

- Only choosen disk where to install OS
- After initial install and reboot configured Wifi
- Logged in to Steam

## Manual commands before claude

```console
make

# Install claude
npm install -g @anthropic-ai/claude-code

# Signed in to Claude initially but later signed out to avoid having any private data on this machine
# (wanted to ensure Wukong devs/Chinese gov won't be spying)
# Later also ran: `npm uninstall -g @anthropic-ai/claude-code`
```

### Syncthing

- Login to bee
- Add a3-bazzite to devices
- Share steamdeck-config folder
- Accept device on a3-bazzite
- Accept folder

### System Settings

#### Boot Mode (Desktop Mode by Default)

Due to Black Myth: Wukong's better performance in Desktop Mode, configure automatic boot to Desktop:

```console
ujust _toggle-autologin
```

**Note**: This will enable automatic login to Desktop Mode without password prompt. Gaming Mode can still be accessed when needed.

#### Mouse

- Pointer speed: -0.60

### Steam

#### Desktop Mode

- Interface: Start Steam when computer starts - Enabled
- Enabled performance monitor (shows top left)
- Settings → In-Game → In-game FPS counter → Top Left

## Games

### Black Myth: Wukong

Note: Had to tweak in-game settings to force compatibility to use Proton 10.2-2 beta to be able to run it.

Still has locked in resoltuin 2xxx/1xxx something. I can play, but Windows has better still.

#### In-Game Settings

- Display:
  - Sharpening Intensity: 0 (reduces artifacts when moving character, likely due to monkey fur rendering)
- Camera:
  - Camera Shake: 0
