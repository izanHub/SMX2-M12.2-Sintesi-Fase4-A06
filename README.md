

## VERSIONES ANTERIORES A LA 17.10

Utilizaremos el comando **"nano \etc\network\interfaces"** para entrar en la configuracion de las redes.
El comando **nano** se utiliza para entrar o modificar el archivo.


Para hacer que nos asignen una IP dinamica por DHCP, escribiremos lo siguiente en el fichero **interfaces**.
- auto enp0s3
- iface enp0s3 inet dhcp

[(E+200U)"imagen"]

Para asignar una IP estatica , escribiremos lo sigueiente en el fichero **interfaces**.
- auto enp0s3
- iface enp0s3 inet static
- address 192.255.255.0
- netmask 255.255.255.0
- gateway 192.168.1.1

Aqui hos dejamos una representación de como queda todo en la terminal.

[(E+200U)"imagen"]

(#) -> funciona para comentar una linea y decir que esa linea es puro texto y no lo interprete.

Una vez hagamos los cambios que queremos tenemos la opcion de reiniciar todas las interfaces, pero esto puede ser un tanto bruto en algunos casos, este reinicio se ejecuta con estos comandos.
- sudo service network restart
- sudo service network stop
- sudo service network start

Tambien tenemos la opcion de reiniciar solo la interfaz que queremos, esta seria la mejor opcion, y se realizaria de la siguiente forma
- sudo ifdown enp0s3
- sudo ifup enp0s3

Para configurar el servidor DNS desberemos poner la siguiente direccion **fichero/etc/resolv.conf**, dentro de esta deberemos escribir lo siguiente:
- nameserver 8.8.8.8

[(E+200U)"imagen"]

## VERSIONES POSTERIORES A LA 17.10

Estas versiones utilizan netplan.
 
Para encontrar el fichero en el cual debemos modificar la IP, tendremos que escribir el siguiente comando **/etc/netplan/****.yaml**.

En caso de que no exista el fichero usaremos el comando **sudo netplan generate** para generar un fichero.

Para establecer una IP estatica deberemos seguir los siguientes pasos:
- dhcp4 : no (En caso de que usemos IPv6 lo pondremos en el dhcp6)
- address 192.255.255.0/24
- gateway 192.168.1.1

Despues de establecer la ip con la mascara y el gateway, establecermos el servidor, en este caso deberemos poner el nombre y la IP:
- Google: 8.8.8.8

Para apolicar todos estos cambios usaremos el comando **sudo netplan apply**

Aqui hos dejamos una representación de como queda todo en la terminal.

[(E+200U)"imagen"]

Para establecer una IP dinamica simplemente tendremos que poner "yes" en el apartado del dhcp y escribir el comando **sudo netplan apply** para aplicar los cambios, tras hacer esto se nos asignara una IP automaticamente.

Aqui hos dejamos una representación de como queda todo en la terminal.

[(E+200U)"imagen"]