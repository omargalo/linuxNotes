## Procesos
```
ls /proc
pidof gnome-todo
cd /proc/numero de proceso
cat cmdline
```
### Procesos que esta usando el usuario
> ps --> process snapshot
```
ps
ps aux
```
> tty -->teletypewriter
### Estados
* S -->sleep
* I< -->Alta prioridad
* R+ -->Ejecutandose
```
ps x
```
## Procesos en segundo plano
### Abrir aplicacición en segundo plano
```
gnome-aplicacion &
```
### Jobs
```
jobs
```
> ctrl+z --> Detener aplicación
```
fg %1
bg %1
```
### Procesos en tiempo real
```
top
```
## Interrumpir procesos
### kill
#### TSTP Terminal Stop
```
kill -20 app
```
#### Stop
```
kill -19 app
```
#### CONT Continue
```
kill -18 app
```
#### INT Interrupt
```
kill -2 app
```
#### KILL
```
kill -9 app
```
#### Pausar el proceso
```
kill -20 PID
```
#### Reaunudar el proceso
```
kill -18 PID
```
#### Detener el proceso
```
kill -19 PID
```
#### Interrumpir el proceso
```
kill -2 PID
```
#### Mandar señal directo al kernel
```
kill -9 PID
kill -l
```
#### Detener todos los procesos asociados a una apliacion
```
killall firefox
```
## Init
### Procesos init
Es el proceso numero 1 del sistema operativo
> App --> Procesos --> Daemons --> Servicios

> Demonios --> Son procesos que se ejecutan de procesos que no vemos

### Scripts que se ejecutan al iniciar el sistema
```
ls /etc/init.d
```
### Acciones
* start
* stop
* reload
* restart
* status

### Scripts K y S
* K --> kill
* S --> Startup

### Listar demonios
```
ls /etc/init
```
Ejemplo:
```
cd /etc/init.d
./openvpn status
```
```
systemctl status apache
service apache restart
```
### Niveles de init
* init 0 --> ningun demonio activo (apagado)
* init 1 --> unica sesión root, no red, no gui
* init 2 --> multiusuario, no red, no gui
* init 3 --> redes
* init 4 --> configurable (servicios)
* init 5 --> gui
* init 6 --> reiniciar
```
sudo init 5
```
* halt --> Apaga la maquina abruptamente
* poweroff
* reboot

### Es mejor usar
```
sudo shutdown -h now
sudo shutdown -r now
sudo shutdown 20:30 (hh:mm)
```
## Prioridad de procesos
* -100-39
* 140 niveles de prioridad
* -100 --> Mas recursos se asignaran
### Procesos del sistema
* -100 al -1
### Usuarios
* 0 al 39
> rt=-100 (real time)
### Procesos nice
Cede recursos a otro proceso
* valores nice: -20 al 19
* valor nice default: 20
* nice+20=prioridad 39
```
nice -n 10 gnome-todo
sudo nice -n -10 gnome-todo
sudo renice -n -20 -p PID
```