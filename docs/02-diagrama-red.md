# 02-diagrama-red

## Objetivo
Diseñar la red antes de instalar los servicios identificando el nodo Proxmox, el Servidor ASO y el cliente Linux

## Procedimiento



|Elemento|Nombre|IP|Función|Recursos|
|---|---|---|---|---|
|Interfaz de red del host|eth0|10.112.7.80/26|Conecta el ordenador anfitrión a la red del centro.|Adaptador virtual de VirtualBox|
|Gateway del host|gateway del host|10.112.7.65|Puerta de enlace para salir de la red local.|Servicio NAT de VirtualBox|
|DNS del host|DNS del host|10.239.3.7, 10.239.3.8|Servidores DNS configurados para resolver nombres de dominio.|Servicio DNS de VirtualBox|
|Interfaz de Docker|(docker0)|10.10.0.1/16|Red virtual utilizada por Docker. Actualmente aparece como DOWN.||
|Interfaz local|(lo)|127.0.0.1/8|Comunicación interna del propio ordenador.|Interfaz de loopback del sistema; no necesita tarjeta de red física.|
|Proxmox vmbr0 sobre adaptador 1 NAT||Pendiente|Salida de red del nodo Proxmox.|Tarjeta de red virtual 1 de VirtualBox y bridge de Proxmox.|
|Gateway NAT de VirtualBox||10.0.2.2|Puerta de enlace NAT de VirtualBox, si se mantiene esa configuración.|Servicio NAT integrado en VirtualBox; no requiere una tarjeta de red adicional.|
|DNS NAT de VirtualBox|DNS de virtualbox|10.0.2.3|DNS habitual de VirtualBox en modo NAT.||
|Interfaz solo-anfitrión del host||Pendiente de comprobar|Permite la comunicación entre el ordenador anfitrión y el laboratorio.|Adaptador de red virtual de VirtualBox para comunicar el ordenador anfitrión con las máquinas virtuales.|
|Proxmox vmbr1 sobre adaptador 2||Pendiente|Gestión del nodo y conexión con las máquinas invitadas, según el diseño.|Adaptador de red virtual 2 y bridge de proxmox|
|Servidor ASO|(srv-aso)|192.168.56.20/24|Servidor Linux para las prácticas.|CPU, RAM, disco virtual y tarjeta de red virtual|
|Cliente Linux|(cli-linux)|192.168.56.30/24|Cliente Linux para probar los servicios.|CPU, RAM, disco virtual y tarjeta de red virtual|

Gateway y DNS:
- Gateway de gestión: el que corresponda a la red física del centro. Debe consultarse antes de configurar Proxmox.
- Gateway del laboratorio: si las VMs solo se comunican entre sí dentro de una red aislada, no necesitan gateway para esa comunicación. Para acceder a Internet necesitarían una salida configurada.
- DNS: el servidor DNS autorizado para la red correspondiente. No se puede deducir únicamente de la configuración de VirtualBox.
- VLAN: no es necesaria para un laboratorio sencillo; se puede usar una red virtual separada sin VLAN, si el diseño y la configuración lo permiten.

 Puertos necesarios:
|Puerto|Uso|Medida de seguridad|
|TCP|8006|Interfaz web de Proxmox mediante HTTPS|Permitir solo a los equipos autorizados|
|TCP|22|SSH,si se necesita administrar por terminal|Deshabilitar o restringir si no se utiliza|
|TCP|80/443|Servicios web del servidor, si los exige la práctica|Permitir solo las conexiones necesarias|


## Comandos usados

```bash

```

## Evidencias


## Incidencias
Ninguna incidencia importante

## Conclusion
La red se ha planteado antes de instalar los servicios para identificar las conexiones necesarias y reducir el acceso innecesario al laboratorio.

[Volver al indice](../README.md)
