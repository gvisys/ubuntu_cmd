# **COMANDOS PARA USAR NO UBUNTU** 
**PARA LIGAR E DESLIGAR A REDE WIFI NO UBUNTU SERVER UTILIZE OS COMANDOS ABAIXO** \
ifconfig wlp2s0 down ** deliga a rede wifi \
ifconfig wlp2s0 up ** liga a rede wifi 

**INSTALAÇÂO DO DOCKER** \
sudo apt-get -y install docker.io 

**CONFIGURAR A REDE VIA TERMINAL**  \

cd /etc/netplan/ \
sudo nano /etc/netplan/01-netcfg.yaml     *** criar arquivo de configuração \

**Colar este conteudo neste arquivo** \
```
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      dhcp4: no
      addresses:
        - 192.168.1.100/24
      gateway4: 192.168.1.1
      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4
```
```
sudo netplan apply
```
**Baixando imagem docker**  \
docker pull ubuntu 

**Construir uma imagem docker**  \
crie um arquivo com nome Dockerfile \
Coloque o conteudo abaixo:
```
FROM ubuntu:24.04
RUN apt -y update
RUN apt -y install wget net-tools iputils-ping nano unzip
WORKDIR /tmp
RUN wget https://downloads.mysql.com/archives/get/p/23/file/mysql-5.7.44-linux-glibc2.12-i686.tar.gz
```

**Executando imagem docker**  \
docker exec -it ubuntu /bin/bash 

**Entrando na imagem docker** \
docker run -it ubuntu


**Arrumando a resolução do anydesk.** \

```
How to fix Anydesk display_server_not_supported error on Linux: 
1. Open terminal on Linux by pressing "Ctrl + Alt + T" 
2. Type " sudo gedit /etc/gdm3/custom.conf " 
3. Uncomment the line " WaylandEnable=false " 
4. Change the line " AutomaticLogin = user1 " to " AutomaticLogin = $USERNAME
5. Uncomment the two lines " AutomaticLoginEnable = true " & " AutomaticLogin = $USERNAME " 
6. Save the document and restart your Linux machine.
```

### ALTERAR O HOSTNAME DO SERVIDOR 
Siga o procedimento abaixo \
Basta você alterar o hostname em dois arquivos – /etc/hostname e /etc/hosts. 

```
sudo nano /etc/hostname
```
Em seguida, vamos atualizar o registro hostname com o novo arquivo /etc/hosts para que o sistema defina o novo hostname na rede.
```
sudo nano /etc/hosts
```
Para completar as formalidades, edite o arquivo de configuração cloud e mude o valor de preserve_hostname para true
```
nano /etc/cloud/cloud.cfg
```
<pre><b>…</b>

<b>…</b>

<b># This will cause the set+update hostname module to not operate (if true)</b>

<b>preserve_hostname: true</b>

<b>…</b>

<b>…</b></pre>

xrdp, xorgxrdp e freexrdp2-x11

#### PARA CORRIGIR ERROS DE ACESSO VIA SSH DE CHAVE

```
sudo nano ~/.ssh/known_hosts
```

