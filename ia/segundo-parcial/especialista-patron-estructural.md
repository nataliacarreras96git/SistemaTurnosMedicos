# Documentación del proceso de generación con IA - Patrón Estructural Facade

## 1. Prompt utilizado

El siguiente prompt fue utilizado con Copilot Agent Mode para analizar el sistema y proponer la aplicación de un patrón de diseño estructural:

```text
Analizar el sistema de gestión de turnos médicos utilizando como contexto los siguientes archivos:

diagramas/01-diagrama-clases/01-diagrama-clases-final.puml

diagramas/01-diagrama-clases/01-solid-01-srp.puml

diagramas/01-diagrama-clases/01-solid-02-ocp.puml

diagramas/01-diagrama-clases/01-solid-03-lsp.puml

diagramas/01-diagrama-clases/01-solid-04-isp.puml

diagramas/01-diagrama-clases/01-solid-05-dip.puml

Identificar un problema específico del sistema que pueda resolverse mediante un patrón de diseño estructural.

Seleccionar el patrón más adecuado entre Adapter, Bridge, Composite, Decorator, Facade o Proxy.

Generar un diagrama de clases UML utilizando PlantUML que represente la solución propuesta.

Justificar la elección del patrón considerando los principios SOLID.
```

---

# 2. Archivos utilizados como contexto

Para la generación del diagrama y análisis del patrón se utilizaron como referencia los siguientes archivos:

- `diagramas/01-diagrama-clases/01-diagrama-clases-final.puml`
- `diagramas/01-diagrama-clases/01-solid-01-srp.puml`
- `diagramas/01-diagrama-clases/01-solid-02-ocp.puml`
- `diagramas/01-diagrama-clases/01-solid-03-lsp.puml`
- `diagramas/01-diagrama-clases/01-solid-04-isp.puml`
- `diagramas/01-diagrama-clases/01-solid-05-dip.puml`

Estos archivos permitieron analizar la estructura actual del sistema, sus responsabilidades y las relaciones existentes entre las clases.

---

# 3. Resultado inicial generado por la IA

La IA identificó que el sistema posee diferentes componentes que participan en las operaciones relacionadas con los turnos médicos.

Se detectó que acciones como crear, modificar o cancelar un turno requieren coordinar múltiples clases:

- Agenda.
- Turno.
- Paciente.
- Médico.
- Notificación.

Debido a esta complejidad, se recomendó utilizar el patrón estructural **Facade**.

---

# 4. Ajustes realizados al resultado generado

Luego de analizar la propuesta inicial, se realizaron los siguientes ajustes:

- Se adaptaron los nombres de las clases al dominio del sistema de turnos médicos.
- Se creó la clase `GestionTurnosFacade` como punto único de acceso.
- Se ajustaron las responsabilidades de cada clase siguiendo principios SOLID.
- Se simplificó el diagrama UML para representar únicamente los componentes necesarios del patrón.
- Se agregó documentación explicando la motivación y justificación técnica.

---

# 5. Iteraciones realizadas

## Primera iteración

La IA analizó la arquitectura existente del sistema.

Resultado:

- Identificación del problema relacionado con el acoplamiento entre componentes.
- Selección del patrón Facade como posible solución.

---

## Segunda iteración

Se solicitó adaptar la solución al contexto del sistema de turnos médicos.

Resultado:

- Creación de la clase `GestionTurnosFacade`.
- Definición de relaciones con Agenda, Turno y Notificación.
- Simplificación de la interacción para los usuarios del sistema.

---

## Tercera iteración

Se revisó la propuesta considerando los principios SOLID.

Resultado:

- Mejora en la distribución de responsabilidades.
- Mayor claridad del diagrama UML.
- Reducción de dependencias directas entre componentes.

---

# 6. Conclusión

La utilización de IA permitió facilitar el análisis de la arquitectura existente y la selección de un patrón estructural adecuado.

El patrón **Facade** fue seleccionado porque permite simplificar la comunicación con múltiples componentes internos del sistema, reduciendo el acoplamiento y mejorando la mantenibilidad.

La solución propuesta permite que futuras modificaciones sean más sencillas y mantiene una estructura alineada con buenas prácticas de diseño de software.