# 03-instalacion-proxmox

## Objetivo
El objetivo es instalar Proxmox en una máquina virtual de virtualbox para disponer de un entorno de virtualizacion.
La instlación se realiza en un entorno virtual de pruebas, de esta forma, se puede practicar la administración de sistemas y la configuración de redes virtuales sin modificar el sistema operativo principal del ordenador.

## Procedimiento
Preparación del entorno: se comprueba que VirtualBox está instalado y que el equipo dispone de recursos suficientes para ejecutar la máquina virtual.

Descarga de la ISO: se obtiene la imagen de instalación de Proxmox VE desde su página web oficial.

Creación de la máquina virtual: se crea una nueva máquina virtual en VirtualBox y se asignan los recursos necesarios, como memoria RAM, procesadores y almacenamiento virtual.

Configuración de la ISO: se monta la imagen ISO de Proxmox VE en la unidad óptica virtual para iniciar el instalador.

Inicio de la instalación: se arranca la máquina virtual y se selecciona la opción de instalación de Proxmox VE.

Configuración inicial: se siguen los pasos del instalador, aceptando las condiciones correspondientes y configurando el almacenamiento, la ubicación, la contraseña de administración y los datos de red solicitados.

Finalización: se completa la instalación y se reinicia la máquina virtual, retirando la ISO si fuera necesario para evitar que vuelva a iniciarse el instalador.

Comprobación: se verifica que Proxmox VE arranca correctamente y que es posible acceder a su interfaz de administración web, siempre que la configuración de red lo permita.

## Comandos usados


```bash

hostnamectl
ip -br addr
pveversion
df -h

```

## Evidencias

## Incidencias
La unica incidencia ha sido que la pantalla se ponia en negro por no configurar bien la maquina virtual pero ya se ha solucionado

## Conclusion
Esta fase constituye la base para continuar con la configuración de la red, la creación de máquinas virtuales y la instalación de los sistemas operativos que formarán parte del proyecto.
Ademas se ha completado sin mayor problema y funciona correctamente

[Volver al indice](../README.md)
