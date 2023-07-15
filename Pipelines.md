## Pipelines
### Toma la salida de un comando y se la pasa como entrada al siguiente comando
```
ls -al /var/log | more
ls -al /var/log | less
```
```
find . -iname "*.txt" | grep "evelyn"
```
```
find . -iname "*.txt" | grep sort
```
```
ls /bin /usr/bin | sort | uniq | less
```
### Conteo de lineas
* wc -w -->palabras
* wc -l -->lineas
* wc -c -->caracteres
```
ls /bin /usr/bin | sort | uniq | less | wc -l
```
## Depurando
### tee
ejemplo:
```
ls /bin /usr/bin | sort | uniq | tee depurado.txt  | less | wc -l
```