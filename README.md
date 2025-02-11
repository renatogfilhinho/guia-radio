### Guia-radio.

#### Guia-radio é uma solução divertida dada a um amigo que queria ouvir a rádio Antena1 seguindo os horários da sua linha de produção.

O processo foi feito em um servidor Proxmox onde sua base é o Debian, como root.


- Instalar pacotes necessários
```sh
apt install mpv alsa-utils
```
- Criar diretório /opt/antena1 (substitua antena1 pela sua rádio)
```sh
mkdir /opt/antena1
```
- Criar o usuário que executará o serviço (antena1)
```sh
adduser --disabled-login --no-create-home antena1
```
- Atribuir permissões ao usuário antena1 para o diretório /opt/antena1
```sh
chgrp -R antena1 /opt/antena1 && chown -R antena1 /opt/antena1
```
- Incluir o usuário antena1 ao grupo audio
```sh
usermod -aG audio antena1
```
- Criar o arquivo que será o serviço a ser executado
```sh
touch /etc/systemd/system/mpv-antena1.service
``` 

