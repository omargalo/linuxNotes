## Redirecciones
* standard output --> mensajes de exito --> 1
* standard error --> mensajes de error --> 2
* standard input --> mensajes de entrada --> 0
```
ls -al /dev/stdout
ls -al /dev/stderr
ls -al /dev/stdin
```
## File Descriptor
Herramienta dentro de linux para asignar un indice a cada archivo para que pueda ser gestionado.
```
ls -al sgsgsg 2> salida.txt
```
### Redireccionar la salida y el error a un solo archivo
```
ls -al &> salida.txt
```
Deprecated
```
ls -al > salida.txt 2>&1
```
### Concatenar
```
ls -al &>> salida.txt
```
## Dispositivo Virtual Null (descartar mensajes)
Muy utilizado en shell scripting

Ejemplo: muestra todos los archivos .log pero sin mostrar los errores de Permission denied
```
find /var/log -iname *.log 2> /dev/null
```
### stdin
Mandar datos por medio de archivos:
```
cat < hola.txt
```
```
ls > salida.txt
sort < salida.txt
sort < salida.txt > ordenado.txt
```