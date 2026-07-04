# Patrón de Diseño Creacional: Builder aplicado a Turno

Este documento presenta el patrón Builder como solución de diseño para la clase Turno dentro del proyecto SistemaTurnosMedicos. La propuesta busca mostrar cómo un patrón creacional puede mejorar la claridad del código, reducir la complejidad de la construcción de objetos y mantener coherencia con los principios SOLID, con especial atención a la legibilidad y a la organización de las reglas de negocio.

## 1. Introducción al Patrón

### 1.1 Definición

El patrón Builder pertenece a la familia de patrones creacionales descrita por Gamma et al. en Design Patterns y su propósito es separar la construcción de un objeto complejo de su representación final. En lugar de exigir un constructor con numerosos parámetros o múltiples sobrecargas, Builder permite construir el producto paso a paso mediante una interfaz fluida y legible.

Este enfoque resulta especialmente útil cuando la creación de un objeto exige combinar datos obligatorios con atributos opcionales, validaciones de negocio o configuraciones que dependen del contexto. En la práctica, el patrón mejora la claridad del código cliente y facilita el mantenimiento del sistema a medida que crecen las reglas de construcción.

### 1.2 Problema que resuelve

El problema central del patrón Builder es el llamado constructor telescópico, que aparece cuando una clase requiere muchos atributos y varios de ellos son opcionales. En esos casos, los constructores tradicionales se vuelven difíciles de leer, propensos a errores de orden y poco expresivos para el desarrollador que consume la API.

En el dominio de SistemaTurnosMedicos, este problema se manifiesta con claridad en la clase Turno, porque su creación requiere combinar datos básicos del turno con información adicional que puede o no estar presente según el caso de uso. Builder evita este problema al exponer operaciones específicas y explícitas como conEstado, conSobreturno o conHistorialEvento.

### 1.3 Cuándo aplicar

El patrón Builder es una opción adecuada cuando:

- La clase tiene varios atributos y muchos de ellos son opcionales.
- La construcción del objeto requiere validaciones o reglas de negocio antes de crear la instancia.
- Se desea una API de creación más legible y expresiva que un constructor convencional.
- Se prevé que el proceso de construcción evolucionará con nuevas opciones sin modificar las llamadas existentes.

## 2. Aplicación en SistemaTurnosMedicos

### 2.1 Contexto del dominio

En el sistema, la clase Turno representa un objeto complejo del dominio. Su construcción no depende solo de los datos mínimos del turno, sino también de información secundaria que varía según el contexto: estado inicial, autorización de sobreturno, llegada del paciente, presencia del mismo o historial de eventos.

En el diseño propuesto, Turno concentra atributos relevantes de construcción en un único objeto. De ellos, tres son obligatorios para iniciar la creación del turno y los restantes se incorporan de forma incremental según la operación que se esté ejecutando. Esta combinación justifica el uso de Builder, ya que el proceso de creación se vuelve más claro y controlado que un constructor tradicional.

Los atributos relevantes del dominio pueden agruparse de la siguiente manera:

- Atributos obligatorios: fechaHoraProgramada, paciente y medico.
- Atributos opcionales: estado, sobreturno, horaRealLlegada, presente, diferenciaMinutos e historial.
- Atributos derivados o de estado: algunos valores no se completan al momento de creación, sino en fases posteriores del ciclo de vida del turno.

Esta distribución refuerza la idea de que la construcción debe ser flexible y expresiva, en lugar de depender de un único constructor sobrecargado.

### 2.2 Clases involucradas

| Clase | Rol en el patrón | Responsabilidad |
|-------|------------------|-----------------|
| Turno | Product | Objeto complejo a construir y encapsular en el dominio |
| Turno.Builder | Builder | Construye Turno paso a paso mediante métodos fluentes |
| Agenda | Director (opcional) | Coordina la creación del turno a partir del builder |
| Secretaria | Client | Solicita la creación del turno y aporta los datos iniciales |

### 2.3 Diagrama UML

![Diagrama de Clases - Patrón Builder](../../diagramas/01-diagrama-clases/01-patron-creacional-builder.png)

**Explicación del diagrama:**
- La clase Turno representa el producto final del patrón y contiene la lógica de negocio asociada al ciclo de vida del turno.
- Su constructor es privado, lo que impide que otras clases creen instancias directamente sin pasar por la validación del builder.
- La clase interna Turno.Builder expone un conjunto de métodos fluentes que permiten configurar los atributos opcionales antes de construir el objeto.
- Agenda utiliza el builder como punto de entrada para crear turnos de manera controlada y coherente con el dominio.
- La relación entre Agenda y Builder permite separar la coordinación del proceso de construcción del objeto mismo, lo que mejora la cohesión del diseño.

### 2.4 Justificación del diseño

La elección de Builder se sustenta en la necesidad de mantener un equilibrio entre expresividad y control. Mientras que un constructor tradicional obliga a pasar todos los datos en un orden fijo y poco claro, el builder permite leer el proceso de construcción en términos del dominio. En este sentido, la solución no solo mejora la sintaxis del código, sino que también comunica mejor la intención del negocio al lector.

## 3. Implementación

### 3.1 Estructura del código

```pseudocode
CLASE Turno
  ATRIBUTOS PRIVADOS:
    - fechaHoraProgramada: DateTime
    - paciente: Paciente
    - medico: Medico
    - estado: TurnoEstado
    - sobreturno: Boolean
    - horaRealLlegada: DateTime
    - presente: Boolean
    - diferenciaMinutos: Integer
    - historial: List<String>

  CONSTRUCTOR PRIVADO(builder: Builder)
    // Asigna atributos desde builder

  CLASE INTERNA Builder
    ATRIBUTOS PRIVADOS:
      - fechaHoraProgramada: DateTime
      - paciente: Paciente
      - medico: Medico
      - estado: TurnoEstado = PENDIENTE
      - sobreturno: Boolean = false
      - horaRealLlegada: DateTime = null
      - presente: Boolean = false
      - diferenciaMinutos: Integer = 0
      - historial: List<String> = []

    MÉTODOS FLUENTES:
      + conEstado(estado): Builder
      + conSobreturno(sobreturno): Builder
      + conHoraLlegada(horaReal): Builder
      + conPresente(presente): Builder
      + conHistorialEvento(evento): Builder
      + build(): Turno
```

El flujo de construcción sigue un orden deliberado: primero se definen los datos obligatorios, luego se incorporan las configuraciones opcionales y, por último, se invoca build(). Este diseño preserva la claridad semántica del código sin exponer al cliente los detalles internos del objeto resultante.

### 3.2 Validaciones en build()

Las validaciones se concentran en el método build() para garantizar que el objeto solo se cree si cumple con las reglas del dominio. Entre las principales validaciones se encuentran:

- La fecha y la hora programada deben estar presentes.
- Paciente y médico deben ser referencias válidas y obligatorias.
- El estado inicial debe ser consistente con la operación de creación.
- Si se marca el turno como sobreturno, debe existir un contexto válido para esa autorización.
- El historial puede inicializarse de forma vacía o completarse según la operación concreta.

Este enfoque evita que el objeto quede en un estado parcial o inconsistente. Además, centraliza en un solo punto las reglas que, de otro modo, se dispersarían entre varios constructores o llamadas directas al operador new.

### 3.3 Flujo de construcción

El flujo típico de construcción puede describirse en tres etapas. Primero, el cliente define los datos obligatorios del turno. Luego, agrega las configuraciones opcionales que corresponden al caso concreto. Finalmente, invoca build(), proceso que valida el estado del objeto y lo retorna listo para su uso.

Este orden facilita la trazabilidad del diseño y permite que el código cliente se mantenga comprensible incluso cuando el número de atributos crece.

## 4. Ejemplos de uso en Casos de Uso

### 4.1 CU01 - Crear Turno

```pseudocode
turno = new Turno.Builder(fechaHora, paciente, medico)
  .conEstado(TurnoEstado.PENDIENTE)
  .conHistorialEvento("Turno creado por Secretaria")
  .build()
```

### 4.2 CU02 - Reprogramar Turno

```pseudocode
turnoReprogramado = new Turno.Builder(nuevaFechaHora, paciente, medico)
  .conEstado(TurnoEstado.REPROGRAMADO)
  .conHistorialEvento("Turno original reprogramado")
  .conHistorialEvento("Cambio solicitado por paciente")
  .build()
```

### 4.3 CU04 - Autorizar Sobreturno

```pseudocode
sobreturno = new Turno.Builder(fechaHora, pacienteUrgente, medico)
  .conEstado(TurnoEstado.CONFIRMADO)
  .conSobreturno(true)
  .conHistorialEvento("Sobreturno autorizado")
  .build()
```

### 4.4 CU05 - Registrar Llegada

```pseudocode
turno = new Turno.Builder(fechaHora, paciente, medico)
  .build()

turno.registrarLlegada(horaRealLlegada)
```

En este caso, el builder se utiliza para crear una instancia inicial del turno, mientras que la operación de registrar llegada se encarga de completar los atributos de seguimiento que corresponden al estado posterior del turno.

## 5. Ventajas y desventajas

### 5.1 Ventajas

- El código cliente es más legible y expresivo.
- Las validaciones de negocio quedan centralizadas en build().
- Se facilita la incorporación de atributos opcionales sin multiplicar constructores.
- El diseño mejora la mantenibilidad del sistema en futuras modificaciones.

### 5.2 Desventajas

- Requiere una estructura adicional, como una clase interna o un builder separado.
- Puede resultar excesivo si la clase tiene pocos atributos y la construcción es trivial.
- Implica un pequeño costo de implementación inicial en comparación con un constructor simple.

## 6. Relación con principios SOLID

Desde una perspectiva académica, Builder no solo resuelve un problema de creación de objetos, sino que también refuerza la arquitectura del sistema al preservar el encapsulamiento y reducir el acoplamiento entre el cliente y la clase compleja. Esta separación entre construcción y uso favorece la evolución del diseño sin afectar de forma inmediata a las partes que ya dependen del objeto Turno.

| Principio | Cómo lo cumple Builder |
|-----------|------------------------|
| SRP | Builder separa la construcción del objeto de la lógica de negocio del turno |
| OCP | Se pueden agregar nuevos atributos opcionales sin modificar constructores ya existentes |
| DIP | Agenda depende de la abstracción del builder para crear turnos, no de un constructor concreto |

## 7. Alternativas evaluadas y descartadas

| Patrón | Razón de descarte |
|--------|-------------------|
| Factory Method | No hay familias de objetos relacionadas que justifiquen una jerarquía de creación |
| Singleton | Agenda ya es una entidad única por contexto, por lo que no requiere este patrón |
| Prototype | No es un requisito del dominio clonar turnos existentes |

## 8. Referencias

- Gamma, E. et al. (1994). Design Patterns. Addison-Wesley.
- Bloch, J. (2018). Effective Java (3ra ed.). Item 2.
- Refactoring.Guru - Builder Pattern.

<!-- RCs resueltos: RC28 (eliminar identificadores innecesarios), RC29 (indicar cardinalidad en el diagrama), RC32 (explicar cómo se utilizan las clases del diagrama en la justificación técnica), y ajuste de historial solicitado en RC3/RC4 de A4. -->

---


