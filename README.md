### Guia-radio.

#### Guia-radio é uma solução divertida dada a um amigo que queria ouvir a rádio Antena1 seguindo os horários da sua linha de produção.

O processo foi feito em um servidor Proxmox (Não é indicado, mas ele queria), onde sua base é o Debian.


- Instalar pacotes necessários
```sh
sudo apt install mpv alsa-utils
```
- Criar diretório /opt/antena1 (substitua antena1 pela sua rádio)
```sh
sudo mkdir /opt/antena1
```
  
- Criar o usuário que executará o serviço (antena1)
```sh
sudo adduser --disabled-login --no-create-home antena1
```
- Atribuir permissões ao usuário antena1 para o diretório /opt/antena1
```sh
sudo chgrp -R antena1 /opt/antena1 && sudo chown -R antena1 /opt/antena1
```
- Incluir o usuário antena1 ao grupo audio
```sh
sudo usermod -aG audio antena1
```
- 

