## Expresiones regulares
> ^ -->Caret

### Metacaracteres
> ^ . [ ] $ ( ) { } * | \ ?

> Cualquier otro caracter son literales

. -->busca cualquier caracter despues de omar
```
grep 'omar.' /var/log/*.log
```
### Símbolos de anclaje
* ^ --> Comienzo de una linea
* $ --> Final de una linea

Buscar solamente lo que comienze con zip:
```
ls /usr/bin | grep '^zip'
```
Buscar solamente lo que termine con zip:
```
ls /usr/bin | grep 'zip$'
```
Buscar usando varios símbolos:
```
ls /usr/bin | grep '^.zip$'
```
### Expresiones de corchetes
```
ls /usr/bin | grep 'zip[-2]'
ls /usr/bin | grep 'zip[-2abcdef]'
ls /usr/bin | grep 'zip[a-z]'
ls /usr/bin | grep 'zip[0-9a-zA-Z]'
```
### Usando clases
* lower
* upper
* alnum
* alpha
```
ls /usr/bin | grep 'zip[[:lower:]]'
```
### POSIX Extendido
```
echo "holaevelyn" | grep "hola\|evelyn"
```
### Es mejor usar
```
echo "holaevelyn" | grep -E "hola|evelyn"
```
### Operador de elección OR
```
ls /usr/bin | grep -E "gz|gr|xe"
ls /usr/bin | grep -E "^gz|.gr.|xe$"
ls /usr/bin | grep -E "^(gz|.gr.|xe)"
ls /usr/bin | grep -E "(gz|.gr.|xe)$"
```
### Cuantificadores
* h* --> Desde el 0 al infinito (puede haber indeterminadas h)
* h+ --> Desde 1 al infinito (debe haber al menos una h)
* h? --> h es opcional
* {:h}{6} --> Debe haber 6 h
* {6} --> Debe haber 6 elementos
* {6,7} --> Por lo menos 6 elementos maximo 7 elementos
* {6,} --> Desde 6 elementos hasta el infinito
* {,7} --> Desde 0 hasta 7 elementos

Ejemplo para validar una cedula de Identidad:
* 11332173-4
* 11332173-k
* 11332173-K
*  9332173-K

No valida hasta los 10 millones:
```
echo "16123456-k" | grep -E "[0-9]*"
```
Valida hasta los 10 millones:
```
echo "16123456-k" | grep -E "[0-9]{8}"
```
La opción valida seria:
```
echo "16123456-k" | grep -E "[0-9]{7,8}"
```
Ahora que valide el -
```
echo "16123456-k" | grep -E "[0-9]{7,8}-"
```
Ahora que el ultimo digito sea un numero o una k minuscula o mayuscula:
```
echo "16123456-k" | grep -E "[0-9]{7,8}-[0-9kK]"
```
Ahora que valide que no comienze con 0:
```
echo "16123456-k" | grep -E "^[1-9][0-9]{6,7}-[0-9kK]"
```
Ahora que el guion sea opcional:
```
echo "16123456-k" | grep -E "^[1-9][0-9]{6,7}-?[0-9kK]"
```
Ahora que valide con puntos: 16.123.456-K
```
echo "16123456-k" | grep -E "^([1-9][0-9]{6,7}|[1-9][0-9]?\.[0-9]{3}\.[0-9]{3})-?[0-9kK]"
```

