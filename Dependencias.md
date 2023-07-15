## Dependencias

### Gestor de paquetes
* Ubuntu y Debian --> .deb
* Redhat y Fedora --> .rpm
* Arch --> .pkg

### Bajo nivel
* dpkg
### Alto nivel
* apt
## Repositorios
```
cat /etc/apt/sources.list
```
```
sudo apt update
```
```
apt-cache search gimp
sudo apt install gimp
```

### Actualizar
```
sudo apt install --only-upgrade gimp
sudo apt upgrade
```
### Remover paquetes
```
sudo apt remove gimp
sudo apt autoremove
```
### Instalar .deb
> Old School
```
dpkg -i paquete.deb
```
> Mejor
```
sudo apt install paquete.deb
```
### Buscar paquetes
```
apt list | grep gimp
apt list --installed
apt list --upgradeable
apt show gimp
```
### Old school
```
dpkg --list | grep gimp -->deprecated
dpkg -s gimp -->deprecated
```
### Actualizar el sistema completo:
```
uname -v
uname -r
uname -a
```
```
sudo apt update
sudo apt dist-upgrade
sudo shutdown -r now
```
