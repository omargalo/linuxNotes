# Notas generales

## VMWare 17

Agregar la siguiente linea en el archivo .vmx
```
ulm.disableMitigations="TRUE"
```

## Arch
```
sudo pacman -Syu
sudo pacman -S open-vm-tools
sudo pacman -S neofetch
```
## Debian

### Agregar usuario al grupo sudo
```
su -
usermod -aG sudo omar
exit
reboot
```
### Comandos extras
```
sudo apt install
free -h
sudo !!
```

### Install deb package
```
sudo apt install package.deb
```
### Eliminar archivos
```
rm archivo
rm -r directorio
rm -rf directorio
```

## nano

### Crear o editar archivo
```
nano prueba.txt
```
### Mostrar las ultimas lineas de un archivo
```
head -n 10 prueba.txt
tail -n 10 prueba.txt
```
### Muestra lo último que esta llegando al archivo
```
tail -f prueba.txt
```
## Redireccionamiento
```
cat ejemplo.txt > prueba.txt
```
### Reemplaza el contenido del archivo
```
echo hola omar > prueba.txt
```
### Agrega contenido al archivo
```
echo hola omar >> prueba.txt
```

## grep
> Global regular expression print

> -i -->indistinct mayus minus
```
grep -i evelyn *.txt
```
### Buscar en ruta absoluta
```
grep -i -r evelyn /home/omar
```
### Buscar en ruta relativa (donde me encuentro)
```
grep -i -r evelyn .
```
### Buscar en directorios
```
find -type
find -type f
find -type f -iname "archivo*"
find -type f -iname "*.txt" > archivosencontrados.txt
```

## Encadenando operadores

### Ejecuta todos
```
mkdir prueba ; cd prueba ; echo listo
```
### Ejecuta si el anterior es exitoso
```
mkdir prueba && cd prueva && echo listo
```
### Solo si el de la izquierda falla
```
mkdir prueba || cd prueva || echo listo
```
### Pasar el resultado a otro operador
```
find | more
```
### Ingresando muchos comandos en lista
```
mkdir prueba && \
cd prueba && \
echo "listo"
```
## Sistema de archivos

### Directorios principales

* bin --> Binario aplicaciones
* boot --> Inicio del sistema
* dev --> Devices archivos de dispositivos
* etc --> Editable Text Configuration
* home --> Directorios de usuarios
* lib --> Dependencias de aplicaciones
* mnt --> Montar dispositivos externos
* proc --> Procesos que estan corriendo
* var --> Archivos que se actualizan constantemente
* sbin --> Binarios y aplicaciones de root
* root --> Home del usuario root

### Atajos útiles

|Teclas  |Acción|
|:-------|:----:|
|ctrl+r||
|ctrl+a|Inicio de linea|
|ctrl+e|Fin de linea|
|alt+b|Inicio de palabra|
|alt+f|Fin de palabra|
|ctrl+c|Cancelar ejecución|
|ctrl+l|Clear|
|ctrl+w|Elimina palabra anterior al cursor|

## Alias

### Crear un alias
```
nano .bashrc
alias ll="ls -al"
source .bashrc
```
### Eliminar un alias
```
unalias ll
```
## Accesos simbólicos (acceso directo)
```
ln -s  ejemplo.txt enlace_ejemplo.txt
```

## Wildcards

* ? * []
* *cualquier caracter o numero de caracteres
* ?=solo 1 caracter
* []=[13] 1 o 3 [1-4] 1 al 4 [!12] Negación

## Expansiones
```
echo prueba{1..5}.txt
```
> prueba1.txt prueba2.txt ... prueba5.txt
```
echo /*/log/*.log*
```

## Expansiones Aritmeticas
```
echo $((3+3))
```
> ** potencia
```
mkdir [2013-2023]-[01..12]
```
## Command substitution
### Pasar un argumento
```
nano $(grep -lr "evelyn" ./*)
```
## Comillas dobles

> "" un unico argumento
```
touch "hola evelyn.txt"
```
> No es buena practica usar espacio es los nombres de lo archivo
```
echo "hola evelyn $(which mv)"
```
> Deprecated
```
echo "hola evelyn `which mv`
```

## Caracter de escape \
```
echo "\$(which mv)"
echo "hola \"evelyn\""
```
### Tabulador
```
echo -e "hola evelyn \t omar"
```
### Nueva linea
```
echo -e "hola evelyn \n omar"
```
### Emite un sonido
```
echo -e "hola evelyn \a omar"
```
