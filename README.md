# steamdeck

## Changes made manually on Steam Deck

* Installed Firefox using UI
* Installed Syncthing GTK in UI

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
