## Permisos, usuarios, grupos
### Permisos y usuarios
> id

> uid User identifier

> gid Group identifier

> groups En cuantos grupos esta el usuario

* group 27 --> Grupo sudo en ubuntu y debian

### Estos datos estan almacenados en la siguiente ruta
```
cat /etc/passwd
```
### Buscar usuario
```
cat /etc/passwd | grep omar
```
### Las contraseñas de los usuarios se guardan en
```
sudo cat /etc/shadow
```
### Ver todos los grupos:
```
cat /etc/group
```
> Los grupos no tienen contraseña

### Permisos: lectura, escritura, ejecución
* r -->lectura
* w -->escritura
* x -->ejecución

### Mostrar permisos de un directorio
```
ls -ld /var/log/installer
```
## root
```
rm -rf / (elimina todo el sistema)
```
## chmod
### Modificar permisos
> utiliza base octal: 01234567

> 000 001 010 011 100 101 110 111

* 000 ---
* 001 --x
* 010 -w-
* 011 -wx
* 100 r--
* 101 r-x
* 110 rw-
* 111 rwx

> x --> 1

> w --> 2

> r --> 4

### Ejemplo permisos de ejecucion
> 1=1
### Ejemplo permisos de ejecución y lectura
> 1+4=5
### Ejemplo permisos ejecución, lectura y escritura
> 1+2+4=7
### Ejemplo permisos usuario, grupo, otros:
> 751
```
chmod 751 prueba.txt
```
### Permisos simbólicos
* u -->user
* g -->group
* o -->others
* a -->all
```
chmod a+rw prueba.txt
chmod o=r prueba.txt
chmod g-w prueba.txt
```
### En una sola linea
> ningun permiso:
```
chmod a= prueba.txt
chmod u=rwx,g=rx,o=r prueba.txt
```
### Es mas fácil usando números
```
chmod 754 prueba.txt
```
## Umask
### Cambiar los permisos por default
> default: rw-rw-r--
### Ejemplo lectura y escritura para usuario y grupos pero ninguno a otros
```
umask 0006
```
> Recomendado usar
```
umask 0002
```
### Restricciones adicionales:
> setuid: como si fueses el dueño

> setgid: como si pertenecieras al grupo

> sticky bit: solo aplica a los directorios (user o group)

* setuid --> 4
* setgid --> 2
* sticky bit --> 1
* 6 --> usuario y grupo
* 7 --> todas las restricciones
chmod 7754 prueba.txt

## sudo
### root consola interactiva
```
sudo -i
```
> ctrl+d para salir (logout)

### Agregar usuarios
```
sudo adduser evelyn
```
### Usuarios especiales (servidor web)
```
cat /etc/passwd | grep www
```
```
adduser --system --disable-login --no-create-home userwebmaster
```
### Eliminar usuario
```
sudo deluser userwebmaster
sudo deluser --remove-all-files omar
sudo deluser --remove-home evelyn
```

## Gestionar grupos
> groups

> groups omar root
```
sudo addgroup usuarios
sudo delgroup usuarios
```
* -a -->append
* -G -->grupos no primarios
### Agregar evelyn a grupo usuarios
```
sudo usermod -aG usuarios evelyn
```
> Reiniciar sesión para que se reflejen los cambios

###Cambiar el grupo principal
```
sudo usermod -g usuarios evelyn
```
### Cambiar nombre de usuario evelyn por ivin
```
sudo usermod -l ivin evelyn
```
### Cambiar el directorio home de un usuario
```
sudo usermod -d /home/ivin evelyn
```
### Cambiar el id de usuario
```
sudo usermod -u 200 evelyn
```
### Bloquear un usuario
```
sudo usermod -L ivin
```
### Desbloquear un usuario
```
sudo usermod -U ivin
```
### Cambiar contraseña a un usuario
```
sudo passwd evelyn
```
## Gestión de propietarios
### Cambiar de dueño
```
sudo chown evelyn prueba.txt
```
### Cambiar dueño y grupo
```
sudo chown evelyn: prueba.txt
```
### Especificar el grupo
```
sudo chown evelyn:usuarios prueba.txt
```
### Solamente el grupo
```
sudo chown :usuarios prueba.txt
```
## Cambiar de usuario en la terminal
### Susbtitute user
```
su
```
### Sin cambiar a su home
```
su evelyn
```
### Cambiar a su home
```
su - evelyn
```
## Sudoers
```
sudo cat /etc/sudoers
```
```
sudo visudo (aqui no se modifica)
```
```
ls /etc/sudoers.d
```
### Especificar comandos permitidos
```
sudo visudo /etc/sudoers.d/evelyn
evelyn ALL=(ALL:ALL) /usr/bin/cat,/sbin/reboot
```