# Things to do after installing Debian 12

## Add superuser rights to main user

```
su -
usermod -aG sudo username
reboot

su -
nano /etc/sudoers
username ALL=(ALL:ALL) ALL
reboot
```

## Install available updates

```
sudo apt update && sudo apt upgrade -y
```

## Add contrib and non-free repos

- Open Software & Updates
- enable DFSG and non-DFSG-compatible software

## Add developer tools

```
sudo apt install git curl
sudo apt install build-essential -y
```

## Add gnome extensions

```
sudo apt install gnome-shell-extension-manager -y
```

## Enable Snap and Flatpak

```
sudo apt install snapd -y
sudo apt install flatpak
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
