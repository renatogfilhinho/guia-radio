### Guia-radio.

#### Guia-radio é uma solução divertida dada a um amigo que queria ouvir a rádio Antena1 seguindo os horários da sua linha de produção.

O processo foi feito em um servidor Proxmox, que possui base Debian, como root.


- Instalar pacotes necessários
```bash
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
- Insira o seguinte conteúdo ao arquivo mpv-antena1.service
```ini
[Unit]
Description=MPV Radio Service for Antena1

[Service]
ExecStart=/usr/bin/mpv -playlist /opt/antena1/listen-radio.m3u
Restart=always
WorkingDirectory=/opt/antena1
User=antena1
ExecStartPre=/bin/sleep 2

[Install]
WantedBy=multi-user.target
```
- Habilite o serviço e recarregue o Systemd
```sh
systemctl enable mpv-antena1.service && systemctl daemon-reload
```
- Por fim, incluir no crontab as necessidades de ínicio e parada do serviço
```sh
crontab -e
```
```ini
...
# m h  dom mon dow   command
0 8 * * 1-5 systemctl start mpv-antena1.service
0 12 * * 1-5 systemctl stop mpv-antena1.service
0 13 * * 1-5 systemctl start mpv-antena1.service
30 17 * * 1-5 systemctl stop mpv-antena1.service
```


