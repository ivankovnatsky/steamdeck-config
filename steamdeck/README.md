# bazzite

## Manually configurtion

### Desktop

* Disable internal display
* Set resoluition to 2560x1440x60Hz
* Set mouse sensitivity to 1/4
* Configure night light 9pm to 6am in GNOME Settings
* Re-arrange dock applications (This should follow windows scheme and I need to
  switch to it for all other machines as well I think):
  * Set files 1
  * Terminal 2
  * Browser/Firefox 3

### Gaming mode / Steam Client

* Configure night mode in Steam client
* Disable UI sounds
* Lower down microphone volume

## 

## Install packages with Brewfile

```console
brew bundle
```

## Configure services

```console
brew services start syncthing
```

## Battery

```console
sudo tee /etc/default/batterylimit <<EOF
# Maximum amount the battery will charge to, including when the device is off.
MAX_BATTERY_CHARGE_LEVEL=80
EOF

sudo systemctl enable batterylimit.service
sudo systemctl start batterylimit.service
```

## Cons

* Very slow downloads
* Doom ETERNAL does not exit cleanly
