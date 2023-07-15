## Redes
```
ip r
ip route
ping ip address
ping -c 4 ip address
```

## curl
### Descargar sitio web
```
curl www.google.com.mx
```
### Descargar archivos
```
curl -O link.iso
```
### Acciones
* GET-->listar
* POST-->crear
* PUT-->reemplazar
* PATCH-->actualizar
* DELETE-->eliminar

Ejemplo:
```
curl https://jsonplacholder.typicode.com/posts
```
```
curl -X POST -d '{"data": "estos son datos"}' -H "Content-Type: application/json" https://jsonplacholder.typicode.com/posts
```
```
curl -X PUT \
-d '{"data": "estos son datos"}' \
-H "Content-Type: application/json" \
https://jsonplacholder.typicode.com/posts/1
```
## wget
```
wget link
wget -c link
wget link -P Downloads/
wget -b link
wget -i urls.txt
```