# ssh
### ssh servidor
```
sudo apt install openssh-server
service ssh status
```
### ssh cliente
```
ssh user@ip
```

## Public Key Login
Crear un certificado:
```
ssh-keygen -t rsa -b 4096
cd .ssh/
```
Copiar la llave publica al servidor método 1:
```
cat id_rsa.pub
```
En el servidor copiarla en:
```
.ssh/authorized_keys
```
Método 2:
```
ssh-copy-id -i /home/omar/.ssh/id_rsa.pub user@destinationip
```
## sftp (lo mas seguro)
### Servidor
```
sudo apt install openssh
```
### Cliente
```
sftp user@ip
```
```
get archivo
put archivo
```
## ftp (no es seguro)
### Servidor
```
sudo apt install vsftpd
sudo nano /etc/vsftpd.conf
Habilitar: write_enable=YES
sudo service csftpd restart
```
### Cliente
```
sudo apt install ftp
ftp ip
usuario/password
pwd
ls
```
Para descargar:
```
get archivo.txt
```
Para subir:
```
put archivo.txt
```
