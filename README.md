### Guia-radio.

#### Guia-radio é uma solução divertida dada a um amigo que queria ouvir a rádio Antena1 seguindo os horários sa sua linha de produção.


- Instalar pacotes necessários
- Criar diretório /opt/antena1 (substitua antena1 pela sua rádio)
```sh
sudo mkdir /opt/antena1
```
  
- Criar o usuário que executará o serviço (antena1)
```sh
sudo adduser --disabled-login --no-create-home antena1
```
- Atribuir permissões ao usuário antena1 para o diretório /opt/antena1
- 
