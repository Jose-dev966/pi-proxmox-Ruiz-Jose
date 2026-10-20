# 02-diagrama-red

## Objetivo
Diseñar la red antes de instalar los servicios identificando el nodo Proxmox, el Servidor ASO y el cliente Linux

## Procedimiento



|Elemento|Nombre|IP|Función|Recursos|
|Nodo proxmox|pve-ruiz||Hipervisor|Maquina virtual en VirtualBox|
|Adaptador 1|puente||Conexión a la red física y posible gestión|Tarjeta de red del anfitrión|
|Adaptador 2|NAT||Salida a internet|Adaptador virtual de VirtualBox|
|Bridge de Proxmox|vmbr0|Sin IP propia|Conectar las máquinas del laboratorio|Bridge interno de Proxmox|
|Servidor ASO|srv-aso|192.168.50.10/24|Servicio principal||
|Cliente Linux|cli-linux|192.168.50.20/24|Pruebas||

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
