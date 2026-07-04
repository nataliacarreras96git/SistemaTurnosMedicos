# Uso de IA - documentador-coordinador de repositorio

## Herramienta utilizada

Se utilizó GitHub Copilot (Agent Mode) integrado en VS Code.


## Contexto proporcionado

-Utilizado para la realización de correcciones de pull requests y  su aprobación.

## Prompt Utilizado

```
Actúa como un Senior Software Engineer realizando code review profesional.

Estás analizando los cambios de una Pull Request activa.

INSTRUCCIONES IMPORTANTES:

- Identifica problemas reales del código
- Enumera los hallazgos (1, 2, 3…)
- Cada hallazgo debe ser independiente
- Sé claro, técnico y concreto
- No inventes problemas hipotéticos sin evidencia en el código
- No incluyas sugerencias de tests

Para cada hallazgo usa EXACTAMENTE esta estructura:

==================================================
HALLAZGO #<número>

Archivo:
Línea:

Tipo de problema:
(bug | performance | seguridad | legibilidad | diseño | otro)

Severidad:
(baja | media | alta | crítica)

Explicación técnica:
Por qué esto es un problema real.

Sugerencia de mejora:
Cambio concreto recomendado.

Ejemplo de código corregido (si aplica):
```codigo
ejemplo
DECISIÓN DEL REVISOR HUMANO:

[ ] Aceptar sugerencia
[ ] Rechazar sugerencia

Justificación del revisor humano:
(Completar manualmente si se rechaza)
Al final agrega:

RESUMEN GENERAL DE LA PR
Evaluación global de calidad y riesgos técnicos.

DECISIÓN FINAL SUGERIDA POR IA:

APPROVE / REQUEST CHANGES / COMMENT ONLY
No completes la sección "DECISIÓN DEL REVISOR HUMANO".
Debe quedar vacía para edición manual.
Publica comentarios directamente en la Pull Request en las líneas correspondientes.
No respondas en el chat salvo para el resumen final.

```

## Resultados obtenidos

### Revision 1 - Especialista en Diagramas de Actividades- Casos de Uso 1 y 2 
```
HALLAZGO #1
Archivo: 04-actividad-cancelar-turno-01.puml
Línea: 44
Tipo de problema: bug
Severidad: alta
Explicación técnica: El archivo termina con @endum en lugar de @enduml...
Sugerencia de mejora: Reemplazar @endum por @enduml.

==================================================
HALLAZGO #2
Archivo: 04-actividad-agendar-turno-02.puml
Línea: 45
Tipo de problema: bug
Severidad: media
Explicación técnica: En la rama else del chequeo de disponibilidad, el diagrama aún procede a guardar el turno...
Sugerencia de mejora: Ajustar el flujo para que, si no hay horario disponible, se notifique...

==================================================
HALLAZGO #3
Archivo: esp-actividades-1-2.md
Línea: 58
Tipo de problema: legibilidad
Severidad: baja
Explicación técnica: La documentación afirma que el diagrama de caso 2 tenía errores de sintaxis y fue corregido, pero el PR actual aún contiene una inconsistencia...

RESUMEN GENERAL DE LA PR
La PR cumple con el propósito de añadir diagramas y documentación, pero incluye un error crítico de sintaxis en 04-actividad-cancelar-turno-01.puml...

DECISIÓN FINAL SUGERIDA POR IA:
REQUEST CHANGES
```

### Revision 2 - Especialista en Diagramas de Actividades- Casos de Uso 3,4 y 5
```
pero por ejemplo como adapto este texto de el output de la ia:
HALLAZGO #1

Archivo:
04-actividad-gestionar-disponibilidad-05.puml

Línea:
45

Tipo de problema:
diseño

Severidad:
media

Explicación técnica:
La partición |Agenda| se utiliza como si fuera un actor responsable de actualizar disponibilidad, pero en un diagrama de actividades esta entidad parece ser un almacenamiento o componente interno del sistema. Esto diluye la claridad de responsabilidades y hace que el diagrama sea menos preciso sobre quién ejecuta realmente la acción.

Sugerencia de mejora:
Mover las acciones de Agenda bajo la partición |Sistema| o renombrar claramente la partición a algo que represente un componente interno, no un actor externo.

Ejemplo de código corregido (si aplica):

DECISIÓN DEL REVISOR HUMANO:

[ ] Aceptar sugerencia
[ ] Rechazar sugerencia

Justificación del revisor humano:


==================================================
HALLAZGO #2

Archivo:
04-actividad-autorizar-sobreturno-04.puml

Línea:
13-18

Tipo de problema:
legibilidad

Severidad:
media

Explicación técnica:
La condición if (Paciente está registrado?) está ubicada en la partición |Paciente|, pero el chequeo de existencia del paciente normalmente corresponde a una validación del sistema. En un diagrama de actividades, esto malinterpreta la responsabilidad de la decisión y puede inducir a errores en la lectura del flujo.

Sugerencia de mejora:
Reubicar la decisión y la acción de selección/registro de paciente en la partición |Sistema|, dejando al paciente sólo en acciones de ingreso de datos o confirmación.

Ejemplo de código corregido (si aplica):

DECISIÓN DEL REVISOR HUMANO:

[ ] Aceptar sugerencia
[ ] Rechazar sugerencia


Justificación del revisor humano:


==================================================
HALLAZGO #3


Archivo:
diagramas-de-actividades.md


Línea:
7-11


Tipo de problema:
legibilidad


Severidad:
baja


Explicación técnica:
El índice sólo referencia los archivos PNG generados y omite los archivos fuente .puml recién añadidos. Esto dificulta el mantenimiento y hace que el documento no refleje completamente los artefactos de la PR.


Sugerencia de mejora:
Agregar referencias explícitas a los archivos .puml en el índice o mantener ambos tipos de artefactos documentados.


Ejemplo de código corregido (si aplica):


DECISIÓN DEL REVISOR HUMANO:


[ ] Aceptar sugerencia
[ ] Rechazar sugerencia


Justificación del revisor humano:


==================================================
HALLAZGO #4


Archivo:
esp-actividades-3-4-5.md


Línea:
10-12


Tipo de problema:
otro


Severidad:
baja


Explicación técnica:
El informe de IA dice “No agregue ni cambie ningún archivo”, pero la PR añade múltiples archivos .puml, .png y .md. Esa inconsistencia hace que la documentación del proceso sea poco confiable y puede confundir a revisores sobre qué parte fue generada y qué parte se aprobó intencionalmente.


Sugerencia de mejora:
Ajustar el texto del informe para reflejar con precisión las acciones realizadas en la PR, o mover esta documentación a una carpeta de trabajo temporal si no se pretende entregarla como artefacto final.


Ejemplo de código corregido (si aplica):


DECISIÓN DEL REVISOR HUMANO:


[ ] Aceptar sugerencia
[ ] Rechazar sugerencia


Justificación del revisor humano:


RESUMEN GENERAL DE LA PR
La PR agrega diagramas de actividad valiosos para los casos de uso 3, 4 y 5, pero presenta problemas de claridad en la asignación de responsabilidades dentro de los diagramas y en la documentación de artefactos. También sería útil alinear el informe de IA con el contenido real de la PR y asegurar que el índice de diagramas refiera los archivos fuente.


DECISIÓN FINAL SUGERIDA POR IA:


REQUEST CHANGES
```
### Revisión 3 - Especialista en Diagramas de Secuencia
```
Estado: Request Changes enviado.
Output generado por la IA
HALLAZGO #1
Archivo: 05-secuencia-agendar-turno-02.puml
Línea: 17, 32
Tipo de problema: legibilidad | diseño
Explicación técnica: En el diagrama AgendarTurno la interacción inicial... no incluye el identificador paciente, pero más abajo el servicio invoca crearTurno(paciente...)...
Sugerencia de mejora: Pasar explícitamente el identificador paciente desde la pantalla al servicio...

==================================================
HALLAZGO #2
Archivo: 05-secuencia-autorizar-sobreturno-03.puml
Línea: 39
Tipo de problema: diseño | legibilidad
Explicación técnica: En AutorizarSobreturno el mensaje servicio -> notificacion : enviarAvisoMedico(medico, paciente) usa el identificador medico que no aparece en pasos previos...
Sugerencia de mejora: Incluir el paso donde se determina o se recupera el medico...

==================================================
HALLAZGO #3
Archivo: changelog.md
Línea: 39, 43
Tipo de problema: legibilidad | otro
Explicación técnica: En changelog.md la entrada para PR #77 aparece duplicada...
Sugerencia de mejora: Unificar las dos entradas de PR #77 en una sola línea...

DECISIÓN FINAL SUGERIDA POR IA:
REQUEST CHANGES
``` 

-A partir del prompt definido, se realizaron varias correcciones de hallazgos para cada PR. Ninguna superaba los 4 hallazgos encontrados por la IA, y se enviaron comentarios de “Request Changes” para corregir esos errores antes de aprobar la PR.

### Revisión N° 4: Re-revisión del Especialista en Actividades (Casos 3, 4 y 5)

``` 
- Estado: APPROVED (Aprobación final tras correcciones).
Output generado por la IA
## ==================================================
## RESUMEN FINAL DE CODE REVIEW - PR #90
## ==================================================

Estado de la Revisión: - SIN HALLAZGOS

Evaluación General:
Tras análisis exhaustivo de los cambios en esta Pull Request, confirmo que los diagramas de actividades presentados cumplen con los estándares de calidad requeridos:

 Diagramas de Actividades - Caso de Uso 3 (Autorizar Sobreturno)
- Estructura correcta de swimlanes con actores apropiados
- Flujos condicionales bien definidos
- Lógica de proceso clara y coherente

 Diagramas de Actividades - Caso de Uso 4 (Gestionar Disponibilidad)
- Swimlanes semánticamente correctos
- Cobertura completa de rutas de ejecución
- Decisiones lógicas adecuadamente ubicadas

 Diagramas de Actividades - Caso de Uso 5 (Reprogramar Turno)
- Particiones correctamente asignadas
- Flujos lógicos coherentes
- Integración apropiada de actores y sistema

 Documentación Acompañante
- Archivo esp-actividades-3-4-5.md documenta correctamente el proceso
- Iteraciones y ajustes debidamente registrados

DECISIÓN FINAL: APPROVE 

``` 



## Ajustes Realizados
### Revisión N°1: Especialista en Patrón de Diseño de Comportamiento
```
- Sugerencia Aceptada (Hallazgo #1): Se aceptó y se envió el comentario de corrección para cambiar link faliido  por link bien direcciónado. Este era un error crítico de sintaxis que impedía que se  renderizara el diagrama correctamente, rompiendo el formato de entrega.
- Sugerencias Rechazadas (Hallazgos #2 y #3):
Decidí rechazar el Hallazgo #2; consideré que el flujo actual del diagrama representa correctamente el escenario base acordado por el equipo y que la sugerencia de la IA añadía una complejidad innecesaria para esta entrega
.
Se rechazó el Hallazgo #3 por ser una observación menor de forma en el archivo .md.
```
### Revisión N° 2: Especialista en Patrón de Diseño Creacional
```
- Hallazgo #1 (Diseño): Se solicitó al compañero agregar su archivo ia/segundo-parcial/especialista-patron-creacional.md, faltante para completar nuestro trabajo de manera correcta.
- Hallazgo #2 y #3: Se decidio ignorar esatas 2 al ser cambios en redacciónes de texto minimas.

```

### Revisión 3 - Especialista en Patrón de Diseño Estructural
```
- Sugerencias Aceptadas (Hallazgos #1 y #2): Se enviaron como "Request Changes".
En el Hallazgo #1, la IA detectó correctamente una falta de coherencia en el flujo de archivos ubicados  con nombres relativamente parecidos.Esto genera duplicación de documentación, confusión sobre la fuente canónica y dificultad para mantener la documentación. No es lo que se solicita.
En el Hallazgo #2, Se solicita la eliminación de un diagrama ya creado 2 veces y ubicados en diferentes lugares.Este diagrama hay que borrarlo, ya se encuentraba en diagramas/01-diagrama-clases.
Asi nuestro trabajo queda bien organizado.
- Sugerencia Rechazada (Hallazgo #3): Decidí ignorar este hallazgo al ser cambios de redacciónes de texto minimas.


### Revisión N° 4: Re-revisión - release/segundo-parcial

Decisión: Se acepta la sugerencia de aprobación (APPROVE) de la IA.
Justificación: Se le solicito a Copilot una corrección general en la release/segundo-parcial para minimizar errorers a futuro. La IA confirma que ahora las particiones son semánticamente correctas y el flujo es coherente, por lo que procedo al cierre técnico de esta tarea


## Conclusión

El uso del prompt estructurado y la integración de IA facilitaron una revisión exhaustiva y objetiva de los artefactos clave del sistema. Las correcciones realizadas mejoraron la calidad de la documentación y la alineación entre los distintos modelos.