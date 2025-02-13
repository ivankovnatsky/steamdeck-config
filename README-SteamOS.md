# steamdeck

## Changes made manually on Steam Deck

* Installed Firefox using UI

On Steam Deck:

```console
# Set password for deck user
passwd
sudo systemctl enable sshd --now

# Increase swap file to 8G to fix RDR2 hanging the system
sudo steamos-readonly disable # Disable the read only FS 
cd /home # There is a "swapfile" located here we'll reuse it 
sudo swapoff -a # Stop swap process 
sudo dd if=/dev/zero of=swapfile bs=1G count=8 # Increase swap to 8gb 
sudo mkswap swapfile # swap ready file again
sudo swapon swapfile # Activate swap
sudo steamos-readonly enable
```

On Air:

```console
ssh-keygen
ssh-copy-id deck@192.168.50.96
ssh deck@192.168.50.96
```

## Install some packages locally

### Syncthing

```console
mkdir -p ~/bin
wget https://github.com/syncthing/syncthing/releases/download/v1.28.0/syncthing-linux-amd64-v1.28.0.tar.gz --directory-prefix ~/bin
cd ~/bin
tar xf syncthing-linux-amd64-v1.28.0.tar.gz
mv syncthing-linux-amd64-v1.28.0/syncthing .
rm -rf syncthing-linux-amd64-v1.28.0*
~/bin/syncthing
```

### Rclone

```console
wget https://github.com/rclone/rclone/releases/download/v1.68.2/rclone-v1.68.2-linux-amd64.zip --directory-prefix ~/bin
cd ~/bin
unzip rclone-v1.68.2-linux-amd64.zip 
mv rclone-v1.68.2-linux-amd64/rclone ~/bin/
rm -rf ~/bin/rclone-v1.68.2-linux-amd64*
```

### dust

```console
wget https://github.com/bootandy/dust/releases/download/v1.1.1/dust-v1.1.1-x86_64-unknown-linux-gnu.tar.gz --directory-prefix ~/bin
cd ~/bin
tar xf dust-v1.1.1-x86_64-unknown-linux-gnu.tar.gz
mv dust-v1.1.1-x86_64-unknown-linux-gnu/dust ~/bin/
rm -rf ~/bin/dust-v1.1.1-x86_64-unknown-linux-gnu
```

### fzf

```console
wget https://github.com/junegunn/fzf/releases/download/v0.58.0/fzf-0.58.0-linux_amd64.tar.gz --directory-prefix ~/bin
cd ~/bin
tar xf fzf-0.58.0-linux_amd64.tar.gz
chmod +x fzf
rm -rf ~/bin/fzf-0.58.0-linux_amd64.tar.gz
```

## Configure

```console
cat <<'EOF' >> ~/.bashrc

if [[ -d ~/bin ]]; then
    export PATH=$PATH:~/bin
fi
EOF
```

## Howtos

### Battery charge level

```console
echo 100 | sudo tee /sys/class/hwmon/hwmon3/max_battery_charge_level
```
