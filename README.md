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
"""
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
"""
