# a3w - Windows 11 for Wukong

## Disk Configuration

Previously installed both Windows and Bazzite separately on the whole disk. Now splitting the 2TB disk equally between both systems to compare game performance. Starting with Windows installation on unallocated space.

## Note

Need to download new ISO for US language. Had to use Safari private mode (which uses Cloudflare DNS) - my normal NextDNS doesn't work and MS blocks from downloading ISO otherwise.

Need to run `wipefs --all` on the disk because Windows can't work with Linux disks.

## OS

Windows 11

### Installation

#### First Reboot Blue Screen Issue

After first reboot during Windows installation, may encounter a blue screen recovery error (not BSOD). This happens because the installer creates two Windows boot entries. To resolve:
- Select the Windows entry with the volume indicator beside it
- This will boot correctly and continue the installation process

#### Network Bypass (No LAN/Ethernet Driver)

When Windows couldn't connect to internet during installation (missing LAN drivers):
- Press `Shift + F10` to open command prompt
- Run `oobe\bypassnro`
- This allows completing Windows setup offline

#### Boot Entry Issue After Failed Installation

When installing Windows to replace Linux (Bazzite), if Windows installation fails once, it leaves a broken Windows boot entry:
- After successful Windows installation (on second attempt)
- Run `msconfig`
- Go to Boot tab
- Remove the failed Windows boot entry (not the current working one)
- This prevents boot failures from the orphaned entry

#### User Setup

- Username: ivan
- Same password for simplicity (won't save anything on this machine)
- Security questions: chosen first 3, answers: 1, 2, 3 respectively
- Kept all location and ads settings as is (enabled)

## Post-Installation

### Activation Grace Period

- Run `slmgr -rearm` as Administrator to reset activation grace period (30 days)
- Can be used up to 3 times to defer activation

### Drivers

- ASUS Driver Hub prompted to use it
- It automatically figured out and installed the drivers
- LAN icon appeared, internet connection established
- Started downloading all drivers automatically (NVIDIA driver already installed)
- Need WiFi and Bluetooth drivers for wireless headphones and DS5 controller
- Decided to install all drivers from ASUS Driver Hub
- Had to run ASUS Driver Hub again to ensure MediaTek Bluetooth driver was properly installed
- NVIDIA driver from ASUS wasn't latest
- Downloaded Game Ready Driver and selected it during NVIDIA installation
- Configured Steam FPS display (Settings → In-Game → In-game FPS counter → Top Left)

### Bluetooth Devices

- Paired AirPods
- Paired DualSense 5 (DS5) controller

## Provisioning

### Scoop

```powershell
# Install Scoop
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression

# Install git (needed for bucket management)
scoop install git

# Install dust (disk usage tool)
scoop install dust

# Add extras bucket for hwinfo
scoop bucket add extras

# Install hwinfo (hardware information tool)
scoop install hwinfo
# Added hwinfo to startup to run in sensors mode

# Install CrystalDiskInfo (disk health monitoring)
scoop install crystaldiskinfo

# Install Steam
scoop bucket add games
scoop install steam
```

### Windows Auto Sign-in

- Run `regedit`
- Navigate to `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PasswordLess\Device`
- Set `DevicePasswordLessBuildVersion` to `0`
- Run `netplwiz`
- Uncheck "Users must enter a user name and password to use this computer"
- Apply and enter password twice
- Rebooted to verify auto sign-in works
- Confirmed: no password prompt, Steam launches in Big Picture Mode automatically - ready to play

### Steam Setup

- Started Steam, waited for auto-updates
- Logged in
- Set status to invisible
- Settings → Interface:
  - Enabled "Start Steam when computer starts"
  - Enabled "Start Steam in Big Picture Mode"

## Games

### Black Myth: Wukong

- Started download
- Add Wukong to startup folder for automatic launch (if not already done):
  - Press `Win + R`, type `shell:startup`, press Enter
  - Create shortcut to Black Myth: Wukong executable in this folder

#### In-Game Settings

- Display:
  - Sharpening Intensity: 0 (reduces artifacts when moving character, likely due to monkey fur rendering)
- Camera:
  - Camera Shake: 0
- Graphics:
  - All settings: Cinematic
  - Ray Tracing: Very High
  - Super Resolution: DLSS
  - Super Resolution Sharpness: 60 (reduced from 85 to minimize movement artifacts)
