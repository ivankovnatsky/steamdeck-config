# a3

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

- Desktop Mode: Enabled performance monitor (shows top left)

## Games

### Black Myth: Wukong

Note: Had to tweak in-game settings to force compatibility to use Proton 10.2-2 beta to be able to run it.

Still has locked in resoltuin 2xxx/1xxx something. I can play, but Windows has better still.
