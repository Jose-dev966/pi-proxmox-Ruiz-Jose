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

### Evidencia 1-virtualbox
![Virtualbox](capturas-o-salidas/03-01-vm-version.png)
![red1](capturas-o-salidas/03-01.2-red.png)
![red2](capturas-o-salidas/03-01.3-red.png)
![pantalla](capturas-o-salidas/03-01.4-pantalla.png)
![almacenamiento](capturas-o-salidas/03-01.5-almacenamiento.png)
![procesador](capturas-o-salidas/03-01.6-procesador.png)

### Evidencia 2-instalador
![instalador](capturas-o-salidas/03-02-instalador.png)

### Evidencia 3-configuracion
![configuracion 1](capturas-o-salidas/03-03-configuración.png)
![configuracion2](capturas-o-salidas/03-03.2-configuracion.png)
![configuracion3](capturas-o-salidas/03-03.3-configuracion.png)
![configuracion4](capturas-o-salidas/03-03.4-configuracion.png)

### Evidencia 4-primer arranque
![primer arranque](capturas-o-salidas/03-04-primer-arranque.png)

### Evidencia 5-interfaz web
![interfazweb1](capturas-o-salidas/03-05-interfaz-web.png)
![interfazweb2](capturas-o-salidas/03-05.2-interfaz-web.png)

### Comandos
![comandos1](capturas-o-salidas/03-comandos.png)
![comandos2](capturas-o-salidas/03.2-comandos.png)
![comandos3](capturas-o-salidas/03.3-comandos.png)
![comandos4](capturas-o-salidas/03.4-comandos.png)

## Incidencias
La unica incidencia ha sido que la pantalla se ponia en negro por no configurar bien la maquina virtual pero ya se ha solucionado

## Conclusion
Esta fase constituye la base para continuar con la configuración de la red, la creación de máquinas virtuales y la instalación de los sistemas operativos que formarán parte del proyecto.
Ademas se ha completado sin mayor problema y funciona correctamente

[Volver al indice](../README.md)
