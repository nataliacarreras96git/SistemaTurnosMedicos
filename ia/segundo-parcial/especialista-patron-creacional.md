# Documentación del Proceso IA - Especialista en Patrones Creacionales

## 1. Contexto

**Rol asignado:** Especialista en Patrones Creacionales  
**Integrante:** @nachonervi-design (Ignacio Nervi)  
**Materia:** Diseño Orientado a Objetos (DOO) - TUPS  
**Proyecto:** Sistema de Turnos Médicos - Grupo N°4  
**Profesor:** Lic. Matías Velásquez  
**Cuatrimestre:** 1er Cuatrimestre 2026

### Objetivo de la entrega

Como especialista creacional, mi tarea fue aplicar **un patrón de diseño de tipo creacional** al sistema, enfocándome en la creación de objetos y en la claridad de la API de creación. Además, documenté los **5 principios SOLID** aplicados al diseño existente del sistema y generé material auxiliar (diagramas y ejemplos) para facilitar la revisión.

### Entregables generados

1. **Patrón Builder** aplicado a la clase `Turno`
2. **5 Principios SOLID** (SRP, OCP, LSP, ISP, DIP) documentados con ejemplos del dominio

---

## 2. Herramientas de IA utilizadas

| Herramienta | Uso específico |
|-------------|----------------|
| **Qwen (Asistente IA)** | Análisis del problema, generación de documentación y prompts iterativos |
| **GitHub Copilot** | Sugerencias de código y validación de sintaxis PlantUML |
| **ChatGPT (GPT-4)** | Revisión cruzada de decisiones de diseño |
| **PlantUML Online** | Generación de diagramas UML a partir de código |

---

## 3. Prompts utilizados

A continuación se muestran los prompts reales que utilicé para guiar a las IA en cada una de las fases importantes. Los prompts se presentan tal como fueron formulados (texto literal), y cada uno incluye el resumen del resultado obtenido.

### Prompt 1: Selección del patrón creacional

```text
Soy Especialista en Patrones Creacionales en un proyecto de Sistema de Turnos Médicos.
Tengo estas clases con sus atributos:

- Turno: id, fechaHoraProgramada, paciente, medico, estado, esSobreturno, 
  observaciones, horaRealLlegada, diferenciaMinutos, presente, motivoCancelacion
- UsuarioDelSistema (abstracta) con subclases: Paciente, Medico, Secretaria
- Agenda: gestiona turnos de un médico
- Notificacion: envía mensajes a pacientes

¿Qué patrón creacional me recomendás aplicar y por qué? 
Considerá: Builder, Factory Method, Singleton, Abstract Factory, Prototype.
```

**Resultado obtenido:**
- **Recomendación:** Patrón Builder para la clase `Turno`
- **Justificación:** Resuelve el problema del "constructor telescópico" (10+ atributos, muchos opcionales)
- **Alternativas descartadas:** Factory Method (no aplica porque no hay familias de objetos), Singleton (Agenda ya es única por médico)

### Prompt 2: Generación del código del Builder

```text
Generá el código del patrón Builder para la clase Turno. Incluí:
1. Clase Turno con constructor privado que recibe un Builder
2. Clase interna estática Turno.Builder con métodos fluentes
3. Método build() con validaciones de negocio
4. Ejemplos de uso para los casos de uso CU01, CU02, CU04 y CU05

Usá pseudocódigo legible, no sintaxis específica de un lenguaje.
```

**Resultado obtenido:**
- Código de `Turno` con constructor privado
- `Turno.Builder` con métodos `conEstado()`, `conSobreturno()`, `conObservaciones()`, etc.
- Validaciones centralizadas en `build()`: paciente no nulo, médico no nulo, fecha futura

### Prompt 3: Diagrama UML del patrón

```text
Generá el código PlantUML del diagrama de clases del patrón Builder 
aplicado a Turno en el Sistema de Turnos Médicos.

Mostrá:
- Clase Turno (Product) con constructor privado
- Clase interna Turno.Builder con métodos fluentes
- Relaciones con Paciente, Medico y Agenda
- Notas explicativas del flujo de construcción
```

**Resultado obtenido:**
- Archivo `01-patron-creacional-builder.puml` generado correctamente
- Diagrama exportado a PNG usando PlantUML Online

### Prompt 4: Documentación de principios SOLID

```text
Para el Sistema de Turnos Médicos, dame ejemplos concretos de cada 
principio SOLID usando las clases existentes del diagrama final:

- SRP: Single Responsibility Principle
- OCP: Open/Closed Principle  
- LSP: Liskov Substitution Principle
- ISP: Interface Segregation Principle
- DIP: Dependency Inversion Principle

Clases disponibles: Turno, Agenda, UsuarioDelSistema, Paciente, Medico, 
Secretaria, TurnoEstado (enum)
```

**Resultado obtenido:**
- 5 ejemplos específicos del dominio con diagramas PlantUML para cada uno
- SRP: Turno gestiona su ciclo de vida, Agenda coordina turnos
- OCP: Enum `TurnoEstado` extensible sin modificar `Turno`
- LSP: Subclases de `UsuarioDelSistema` sustituibles
- ISP: Interfaces segregadas por capacidad
- DIP: `Agenda` depende de abstracciones, no de implementaciones

### Prompt 5: Validación de coherencia

```text
Revisá si el patrón Builder aplicado a Turno y los principios SOLID 
documentados son coherentes con:

1. El diagrama final de clases (06-clases-diagrama-final.puml)
2. Las tarjetas CRC existentes (Turno, Agenda, Secretaria, Paciente, Medico)
3. Los casos de uso CU01, CU02, CU04, CU05

Identificá inconsistencias o conflictos.
```

**Resultado obtenido:**
- ✅ Coherencia confirmada con el diagrama final
- ✅ Alineación con tarjetas CRC (responsabilidades preservadas)
- ✅ Beneficio claro para los 4 casos de uso principales
- ⚠️ Ajuste: agregar atributo `historial: List<String>` solicitado por docente en RC3/RC4 de A4

---

## 4. Decisiones de diseño tomadas

### Decisión 1: Elegir Builder sobre otros patrones creacionales

**Alternativas evaluadas:**

| Patrón | Aplicabilidad | Razón de descarte |
|--------|---------------|-------------------|
| Factory Method | Crear diferentes tipos de `UsuarioDelSistema` | Ya resuelto con herencia |
| Singleton | `Agenda` única por médico | Cardinalidad ya lo garantiza |
| Abstract Factory | Familias de objetos | No aplica al dominio |
| Prototype | Clonar turnos | No es un requisito |
| **Builder** | **Turno con atributos opcionales** | **✅ Resuelve problema real** |

**Decisión final:** Builder aplicado a `Turno`  
**Justificación:** La clase tiene 10 atributos (3 obligatorios + 7 opcionales). Sin Builder habría constructor telescópico, código ilegible y validaciones dispersas.

### Decisión 2: Clase interna estática vs clase separada

**Alternativas:**
- `TurnoBuilder` como clase separada
- `Turno.Builder` como clase interna estática

**Decisión:** Clase interna estática  
**Justificación:** Builder es específico de `Turno`, acceso a miembros privados, encapsulamiento fuerte, convención estándar.

### Decisión 3: Validaciones centralizadas en `build()`

**Decisión:** Validar en `build()` en vez de en cada setter  
**Justificación:** DRY, construcción parcial sin errores, más fácil de testear.

### Decisión 4: Documentar SOLID con clases existentes

**Decisión:** Usar clases existentes en vez de crear nuevas  
**Justificación:** Coherencia con A4, no introduce complejidad, demuestra que SOLID ya estaba aplicado.

### Decisión 5: Incluir atributo `historial` en Builder

**Contexto:** Docente marcó en RC3/RC4 de A4 que `Turno` debe tener `historial`  
**Decisión:** Agregar `conHistorial(List<String>)` al Builder  
**Justificación:** Coherencia con correcciones del docente.

---

## 5. Verificación y validación

### Checklist de calidad del patrón Builder

- ✅ Constructor de `Turno` es privado
- ✅ `Turno.Builder` tiene métodos fluentes (retornan `this`)
- ✅ `build()` valida todos los atributos obligatorios
- ✅ Los atributos de `Turno` son privados (encapsulamiento)
- ✅ Ejemplos de uso funcionan para CU01, CU02, CU04, CU05

### Checklist de coherencia con el diseño

- ✅ Respeta `06-clases-diagrama-final.puml`
- ✅ Alineado con tarjetas CRC
- ✅ Beneficia casos de uso principales
- ✅ Mantiene encapsulamiento
- ✅ Incluye `historial` solicitado por docente

### Checklist de principios SOLID

- ✅ SRP: Responsabilidad única
- ✅ OCP: Jerarquía extensible
- ✅ LSP: Sustitución segura
- ✅ ISP: Interfaces segregadas
- ✅ DIP: Dependencias de abstracciones

---

## 6. Aprendizajes

### Lo que aprendí

1. **Los patrones resuelven problemas reales:** Builder resuelve el constructor telescópico de `Turno`.
2. **SOLID ya estaba aplicado:** Solo tuve que documentarlo con ejemplos concretos.
3. **La IA acelera pero no reemplaza:** Generó código rápido, pero yo validé coherencia.
4. **La documentación es clave:** Sin documentación clara, el patrón no tiene valor.
5. **Las correcciones del docente mejoran el diseño:** El atributo `historial` enriqueció el Builder.

### Lo que haría diferente

1. Empezar con análisis manual antes de preguntar a la IA
2. Validar con otros especialistas antes de decidir
3. Crear tests conceptuales
4. Documentar decisiones negativas con más detalle

### Uso responsable de IA

- ✅ Usé IA para generar código base
- ✅ Validé cada decisión manualmente
- ✅ Ajusté a necesidades específicas
- ✅ Documenté proceso transparente
- ✅ Incluí prompts reales
- ❌ NO copié sin entender
- ❌ NO dejé que IA decidiera por mí
- ❌ NO omití alternativas descartadas

---

## 7. Referencias bibliográficas

- **Gamma, E., Helm, R., Johnson, R., Vlissides, J.** (1994). *Design Patterns: Elements of Reusable Object-Oriented Software*. Addison-Wesley.
- **Bloch, J.** (2018). *Effective Java* (3ra ed.). Item 2: Builder Pattern.
- **Martin, R. C.** (2002). *Agile Software Development, Principles, Patterns, and Practices*.
- **Refactoring.Guru** - [Builder Pattern](https://refactoring.guru/design-patterns/builder)
- **Refactoring.Guru** - [SOLID Principles](https://refactoring.guru/design-principles/solid)

---

## 8. Archivos generados en esta entrega

### Patrón Builder
- `anexos/patrones-diseno/patron-de-diseno-creacional.md`
- `anexos/patrones-diseno/patrones_diseno.md` (índice)
- `diagramas/01-diagrama-clases/01-patron-creacional-builder.puml`
- `diagramas/01-diagrama-clases/01-patron-creacional-builder.png`

### Principios SOLID
- `anexos/principios-solid/principios_solid.md` (índice)
- `anexos/principios-solid/01-srp.md` a `05-dip.md`
- `diagramas/01-diagrama-clases/01-solid-srp.puml` a `05-solid-dip.puml`

---

**Autor:** @nachonervi-design (Especialista en Patrones Creacionales)  
**Fecha:** Julio 2026  
**PR asociada:** [#148 - Release/segundo parcial](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/148)
