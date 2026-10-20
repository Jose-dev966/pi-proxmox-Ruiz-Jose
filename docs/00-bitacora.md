# Bitacora de sesiones

La bitacora es el registro cronologico del trabajo. Anade una entrada al final
de cada sesion y conserva las anteriores. Escribe datos comprobables y enlaza
las evidencias utiles; evita frases generales como "he trabajado en Proxmox".

## Sesion 01 - 29/09/26

- Objetivo: iniciar GitHub y la documentacion Markdown.
- Acciones realizadas: PENDIENTE: configuraciones, cambios o investigacion.
- Decisiones y motivos: PENDIENTE: eleccion realizada y alternativas valoradas.
- Pruebas y resultados: PENDIENTE: resultado esperado, comando o metodo y resultado obtenido.
- Documentos o evidencias: [Ficha inicial](00-ficha-inicial.md).
- Incidencias y solucion o estado pendiente: PENDIENTE.
- Siguiente paso: PENDIENTE: accion concreta para la proxima sesion.

Anadir una entrada con esta estructura en cada sesion. El historial de
GitHub registra los commits; no hace falta incluir el hash del propio
commit dentro de su entrada de bitacora.

[Volver al indice](../README.md)


## Sesión 02 - 06/10/26

Objetivo:Crear el repositorio individual del proyecto y preparar la documentación inicial antes de comenzar el inventario de hardware y la instalación de Proxmox.


Acciones realizadas:
- Se ha creado el repositorio individual en GitHub.
- Se ha preparado la estructura inicial del proyecto.
- Se han creado los documentos iniciales en formato Markdown.
- Se ha preparado el README con la información básica del proyecto.
- Se ha iniciado la ficha inicial, la bitácora y la memoria técnica.
- Se ha preparado el archivo `.gitignore`.
- Se ha revisado la estructura de carpetas y documentos.

Pruebas y resultados:
Se ha comprobado que el repositorio local contiene los documentos iniciales y que Git reconoce los archivos preparados para el primer commit.

Queda pendiente comprobar la publicación del commit en GitHub y revisar que los enlaces del README funcionan correctamente.

Decisiones:
Se utilizará Git y GitHub para mantener el historial de cambios y publicar la documentación del proyecto.

La modalidad definitiva y los recursos concretos quedan pendientes de confirmar.

Incidencias:
Durante esta primera fase no se han producido incidencias importantes.

Siguiente paso:
Completar la información pendiente, publicar el primer commit en GitHub y comenzar el inventario del hardware disponible para el proyecto.

## Sesión 03 - 13/10/26

Objetivo:Hacer el inventario de hardware

Acciones realizadas:
- Se ha realizado el inventario inicial del ordenador como la CPU, la RAM, el Almacenamiento, la Red y la plataforma
- Se ha comprobado si es posible instalar proxmox en el equipo
- Se ha comrpobado que limitaciones tendría el equipo
- Se ha calculado el reparto de recursos de la Ram y el disco
- Se ha comprobado que componentes eran mas críticos para el servidor

Pruebas y resultados:
Se ha comprobado que en principio si se podría usar proxmox en ese dispositivo pero teniendo en cuenta tambien los limitantes del equipo

Decisiones:
No se utilizara proxmox en ese dispositivo debido a la falta de material por lo que se usara una maquina virtual

Incidencias:
No han habido incidencias importantes en esta fase.

## Sesión 04- 20/10/26

Objetivo:Diseñar la red antes de instalar los servicios identificando el nodo Proxmox, el Servidor ASO y el cliente Linux

Acciones realizadas:
- Se ha establecido los adaptadores
- La red se ha planteado antes de instalar los servicios para identificar las conexiones necesarias y reducir el acceso innecesario al laboratorio.

Incidencias:
Sin incidencias importantes
