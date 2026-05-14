herramientas utiles:
sudo apt install curl htop net-tools tcpdump -y
instalacion de   ---apache---   --- extensiones---
sudo a2enmod log_config
sudo systemctl restart apache2

activacion de logs detallados    -probarlo->servidor
sudo a2enmod log_config
sudo systemctl restart apache2

(Estos son totalmente legítimos y forman parte de cualquier análisis de disponibilidad) --consultar---
sudo sysctl -w net.ipv4.tcp_syncookies=1
sudo sysctl -w net.ipv4.tcp_max_syn_backlog=2048
sudo sysctl -w net.ipv4.tcp_fin_timeout=15

monitorizacion:
curl -I http://IP_DEL_SERVIDOR
watch -n 1 "netstat -tn | grep ':80' | wc -l"
ver el trafico:
sudo tcpdump -i eth0 port 80 -w captura.pcap

contramedidas  --este importa--:
*mod_reqtimeout:
sudo a2enmod reqtimeout
sudo nano /etc/apache2/mods-enabled/reqtimeout.conf
*valores:
RequestReadTimeout header=20-40,MinRate=500
*limitaciones de conexiones por IP
sudo apt install libapache2-mod-evasive






