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
sudo apt install git curl wget ca-certificates neofetch htop filezilla -y
sudo apt install build-essential -y
```
## Install Chrome

```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

## Install Brave

```
sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list
sudo apt update
sudo apt install brave-browser
```

## Enable firewall

```
sudo apt install ufw -y
sudo ufw enable
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
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
