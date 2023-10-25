VERSIONES ANTERIORES A LA 17.10
Como cambiar las IP's en linux -> \etc\network\interfaces
modificar ficheros en linux -> nano
DHCP -> 
auto enp0s3
iface enp0s3 inet dhcp

Estatica ->
auto enp0s3
iface enp0s3 inet static
address 192.255.255.0
netmask 255.255.255.0
gateway 192.168.1.1

# -> funciona para comentar una linea y decir que esa linea es puro texto y no lo interprete.

Reiniciar todas las interficies
- sudo service network restart
- sudo service network stop
- sudo service network start

Reiniciar solo la interficie
- sudo ifdown enp0s3
- sudo ifup enp0s3

Configuracion del DNS
- fichero/etc/resolv.conf
- nameserver 8.8.8.8

Comprobar la version de una maquina -> lsd_release -a

VERSIONES POSTERIORES A LA 17.10
Estas versiones utilizan netplan.
 
 /etc/netplan/****.yaml
si no existe el fichero -> sudo netplan generate

Establecer IP estatica
dhcp4 : no
Y definir la ip con su / y el gateway
Y despues el nombre del servidor con su IP
USAR ESPACIOS Y NO TAB -> USANDO EL TAB DA ERROR
sudo netplan apply

Establecer IP dinamica
dhcp: yes
sudo netplan apply

