# Inventario investigado y viabilidad

## Contexto de la observacion

- Fecha y sistema utilizado: PENDIENTE.
- Modalidad, equipo anfitrion y VM VirtualBox si procede: PENDIENTE.
- Version de Proxmox prevista: PENDIENTE.

## Inventario inicial

| Area | Dato observado y evidencia | Especificacion y fuente | Limite o diferencia | Justificacion |
|---|---|---|---|---|
| CPU |Intel Pentium G4560 a 3,50 GHz, 2 núcleos y 4 hilos.|Intel confirma estas características y la compatibilidad con Intel VT-x. Ficha oficial de Intel.|Es un procesador antiguo y tiene pocos núcleos físicos.| |
| RAM |8 GB de RAM DDR4 a 2400 MHz, según las anotaciones tomadas del equipo.|Proxmox recomienda contar con memoria adicional para las máquinas virtuales y contenedores, aparte de la necesaria para el sistema. Requisitos oficiales de Proxmox.|8 GB es una cantidad limitada para ejecutar varias máquinas simultáneamente| |
| Almacenamiento |Unidad identificada en las notas como /dev/sda, con aproximadamente 465,8 GB visibles. El modelo parece ser Toshiba DT01ACA050, pendiente de confirmar.|Documentación oficial de Toshiba. El modelo DT01ACA050 corresponde a una unidad de 500 GB.|La capacidad visible no equivale necesariamente al espacio libre. Si se confirma que es un HDD, será más lento que un SSD.| |
| Red |arjeta Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet. En las anotaciones, eth0 aparecía como DOWN.|La documentación de Proxmox contempla una interfaz de red para la gestión y la conectividad del nodo.|La interfaz aparecía desactivada en el sistema observado. Debe comprobarse su funcionamiento después de instalar Proxmox.| |
| Plataforma |Arquitectura x86-64. En las notas aparece el kernel Linux 6.5.0-15-generic.|La ficha de Intel confirma que el procesador admite Intel 64 y VT-x.|No se ha confirmado el modelo de la placa base, la versión de BIOS/UEFI ni que la virtualización esté activada en el firmware.| |

## 1. Puedo instalar Proxmox en este equipo?

Contrastar el inventario con requisitos oficiales de la version prevista.
Responder por separado y justificar con datos y fuentes:

- Puedo instalar y arrancar Proxmox: PENDIENTE.
  
  En principio, sí, aunque hay comprobaciones pendientes.

El procesador Intel Pentium G4560 utiliza arquitectura de 64 bits y admite Intel VT-x, una característica importante para ejecutar máquinas virtuales. El equipo dispone de 8 GB de RAM y una unidad de almacenamiento que, según las anotaciones, tiene aproximadamente 465,8 GB visibles.

Estos datos indican que el equipo puede servir para realizar una instalación de prueba de Proxmox VE. Sin embargo, antes de confirmar que podrá arrancar correctamente, hay que comprobar que la virtualización está activada en BIOS/UEFI, que el disco funciona correctamente y que el instalador reconoce la tarjeta de red.

La compatibilidad con Intel VT-x indicada por el fabricante no demuestra por sí sola que esta función esté activada en el firmware.
- Puedo ejecutar el servidor ASO y el cliente del proyecto: PENDIENTE.
  
  Sí, previsiblemente para un laboratorio educativo básico, con limitaciones.

Se plantea utilizar un servidor srv-aso y un cliente cli-linux. El procesador tiene dos núcleos físicos y la memoria RAM total es de 8 GB, por lo que será necesario utilizar máquinas virtuales ligeras y evitar ejecutar demasiadas tareas al mismo tiempo.

La viabilidad dependerá de la RAM que necesite realmente cada sistema operativo, del espacio disponible en el disco y de la carga de trabajo. No se puede garantizar un funcionamiento fluido hasta realizar una prueba con ambas máquinas encendidas.
- Condiciones o comprobaciones pendientes: PENDIENTE.
  
 Confirmar la versión exacta de Proxmox VE que se instalará.

Comprobar que Intel VT-x está activado en BIOS/UEFI.

Confirmar el modelo y el estado del disco.

Comprobar el espacio libre real del almacenamiento.

Verificar que la tarjeta de red funciona y que se dispone de conexión.

Realizar una prueba con srv-aso y cli-linux funcionando simultáneamente. 

## 2. Que limitaciones tendre con este hardware?

Analizar RAM, CPU, disco y red para las cargas previstas. Identificar lo
medido y lo estimado. En VirtualBox, investigar host real y VM: version,
RAM reservada al anfitrion, vCPU, VDI, espacio fisico y red local.
No se utiliza el Proxmox del centro como recurso.

### Reparto de recursos

| Elemento | CPU/vCPU | RAM | Disco | Justificacion |
|---|---|---|---|---|
| Proxmox |CPU compartida|2 GB reservados como estimación inicial|16 GB como referencia de planificación|El nodo necesita recursos para su propio sistema y los servicios de gestión.|
| srv-aso |2 vCPU|2 GB|16 GB|signación inicial para un servidor de prácticas ligero.|
| cli-linux |1 vCPU|1 GB|10 GB|Asignación inicial para un cliente Linux ligero.|
| Plantilla, ISOs y copias | No aplica | No aplica |10 GB|Espacio inicial estimado para instaladores y archivos de apoyo. Las copias importantes deberían guardarse también en otro dispositivo.|
| Margen de operacion |CPU compartida|1 GB como margen orientativo|10 GB como margen orientativo|Se reserva un margen para evitar trabajar con todos los recursos comprometidos.|

Mostrar calculos de RAM y disco, reparto de vCPU, unidades y supuestos.
Explicar las cargas que pueden funcionar simultaneamente.

Cálculo de RAM

Proxmox: 2 GB.

srv-aso: 2 GB.

cli-linux: 1 GB.

Margen orientativo: 1 GB.

Total previsto: 2 + 2 + 1 + 1 = 6 GB.

Margen restante: 8 − 6 = 2 GB.

Este cálculo es orientativo. Los 2 GB restantes no deben considerarse memoria libre garantizada, porque el consumo real depende del sistema, los servicios, la caché y la configuración de Proxmox. Además, algunos sistemas operativos pueden necesitar más memoria de la propuesta.

Cálculo de disco

Para planificar el espacio se utilizan los siguientes valores:

Proxmox: 16 GB.

srv-aso: 16 GB.

cli-linux: 10 GB.

Plantillas, ISOs y copias: 10 GB.

Margen de operación: 10 GB.

Total planificado: 16 + 16 + 10 + 10 + 10 = 62 GB.

Si la unidad es realmente de 500 GB comerciales, su capacidad aproximada puede aparecer como unos 465,8 GiB en el sistema. Restando de forma orientativa 62 GiB, quedarían unos 403,8 GiB, antes de tener en cuenta particiones, formato, metadatos y otros usos.

Por tanto, no se puede afirmar que ese sea el espacio libre real. Hay que comprobarlo con lsblk y df -h y revisar cómo se repartirá el disco durante la instalación.

Los discos virtuales pueden configurarse con aprovisionamiento fino (thin provisioning), en cuyo caso su tamaño máximo no significa que todo ese espacio esté ocupado físicamente desde el principio. Aun así, si las máquinas crecen demasiado, pueden agotar el almacenamiento real.

| Limitacion | Evidencia o estimacion | Consecuencia | Medida y limite que permanece |
|---|---|---|---|
|RAM |8 GB según las notas; reparto inicial de 6 GB más margen.|Si las máquinas consumen demasiada memoria, pueden ir lentas o producirse intercambios con disco.|Utilizar sistemas ligeros, ajustar la RAM y cerrar máquinas que no se estén usando. La memoria física sigue limitada a 8 GB.|
|CPU |Pentium G4560 con 2 núcleos y 4 hilos.|Varias tareas exigentes pueden competir por el procesador.|Ejecutar solo las máquinas necesarias y evitar cargas pesadas simultáneas.|
|DISCO|Aproximadamente 465,8 GB visibles; modelo y estado pendientes de confirmar.|Si es un HDD, las máquinas pueden arrancar y responder más lentamente. Un fallo del disco puede dejar el nodo y sus máquinas fuera de servicio.|Comprobar su estado y vigilar el espacio disponible. Un SSD podría mejorar el rendimiento, pero no evitaría por sí solo la pérdida de datos.|
|Copias de seguridad|El espacio reservado para copias es solo una estimación.|Guardar todas las copias en el mismo disco no protege frente a un fallo de esa unidad.|Guardar las copias importantes en otro dispositivo o ubicación.|
|RED|Tarjeta Realtek Gigabit Ethernet; eth0 aparecía como DOWN.|Sin una interfaz operativa, la gestión y la comunicación entre sistemas pueden fallar.|Comprobar cable, configuración y conectividad después de instalar.|
|Virtualización|El procesador admite VT-x, pero falta comprobar el firmware.|Si la virtualización está desactivada, las máquinas virtuales pueden no funcionar correctamente.|Activar y comprobar Intel VT-x en BIOS/UEFI antes de realizar las pruebas.|

## 3. Que componentes son mas criticos en mi servidor y por que?

Ordenar al menos tres componentes para este equipo y su servicio.
Distinguir cuello de botella, disponibilidad e integridad de los datos.

| Prioridad y componente | Funcion | Efecto si es insuficiente | Efecto si falla | Evidencia y justificacion |
|---|---|---|---|---|
| 1. RAM |Mantiene en memoria Proxmox y los sistemas virtualizados.|Puede causar lentitud y uso intensivo del disco como memoria de intercambio.|Un fallo físico puede provocar inestabilidad y apagar el nodo.|Solo se dispone de 8 GB según las notas. Es el principal recurso que habrá que vigilar al ejecutar ambas máquinas.|
| 2. Almacenamiento |Contiene Proxmox, las máquinas virtuales, sus datos y las copias locales.|Un disco lento puede alargar los arranques y las operaciones de lectura y escritura.|Si falla, se puede perder el acceso al nodo y a los datos que contiene.|El modelo exacto y el estado de la unidad están pendientes de confirmar. Las copias en otro dispositivo son importantes.|
| 3. CPU |Ejecuta Proxmox y las tareas de las máquinas virtuales.|Las tareas simultáneas pueden tardar más en completarse.|Un fallo del procesador impediría utilizar el servidor.|El Pentium G4560 dispone de 2 núcleos físicos y 4 hilos, suficientes como punto de partida para un laboratorio sencillo, pero limitados para cargas elevadas.|

Componente que mejoraria primero y motivo para priorizarlo frente a otro:

Mejoraría primero la RAM, siempre que las pruebas confirmen que es el principal cuello de botella. Pasar a una capacidad superior, si la placa base lo permite, facilitaría ejecutar Proxmox y las dos máquinas con más margen.

## Fuentes tecnicas

Consultar al menos tres fuentes primarias, incluyendo Proxmox y
fabricante o plataforma virtual. Relacionarlas con las tres respuestas.

| Fuente y URL | Version/modelo y fecha de consulta | Afirmacion respaldada | Aplicacion al nodo |
|---|---|---|---|
|Proxmox VE: requisitos oficiales https://www.proxmox.com/en/products/proxmox-virtual-environment/requirements|Requisitos oficiales consultados el 13/10/2026; confirmar los de la versión exacta que se instale.|Arquitectura compatible, virtualización y necesidades de memoria y almacenamiento.|Permite contrastar los recursos del equipo con los requisitos de Proxmox.|
|Intel: Pentium G4560 https://www.intel.com/content/www/us/en/products/sku/97143/intel-pentium-processor-g4560-3m-cache-3-50-ghz/specifications.html|Intel Pentium G4560; consultado el 13/10/2026.|2 núcleos, 4 hilos, 3,50 GHz, arquitectura Intel 64 y compatibilidad con VT-x.|Justifica la evaluación de la CPU y la virtualización por hardware.|
|Toshiba: documentación de la serie DT01ACA https://toshiba-semicon-storage.com/content/dam/toshiba-ss-v3/master/en/storage/product/internal-specialty/cHDD-DT01ACAxxx-Product-Overview.pdf|Serie DT01ACA; consultado el 13/10/2026.|Características de las unidades de la serie, incluida la variante de 500 GB.|Sirve para contrastar el modelo si se confirma que la unidad instalada es una DT01ACA050.|

## Dictamen de viabilidad

Apto, apto con condiciones o no apto para la propuesta actual: PENDIENTE.

El equipo dispone de un procesador de 64 bits compatible con Intel VT-x, 8 GB de RAM según las anotaciones y una unidad de almacenamiento con aproximadamente 465,8 GB visibles. En principio, estos recursos pueden servir para instalar Proxmox directamente en el equipo físico y ejecutar un servidor ASO y un cliente Linux ligeros.


## Evidencias y revision docente

Enlazar salidas revisadas desde ../evidencias/. Un listado automatico no
sustituye la investigacion. Registrar la pregunta de defensa y respuesta.

[Volver al indice](../README.md)
