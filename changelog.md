# Changelog

## [Unreleased]

## [Released - Segundo Parcial] - 2026-06-27

### Added

- [feature/coord-devops-update-docs] Se aplicaron correcciónes y actuaizaciones para que  Sistema de Turnos Médicos pueda mejorar el rendimiento. PR: [#147](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/147) -@britezacostaalexis-pixel(Coordinador y Devops)


- [feature/esp-patron-estructural-facade] Se aplicó el patrón facade al Sistema de Turnos Médicos para mejorar el rendimiento. PR: [#145](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/145) - @lautarochavez14 (Especialista en Patrón de diseño Estructural)


- [feature/esp-creacional-add-patron-builder] Patrón Builder aplicado a la clase Turno para resolver el constructor telescópico. Incluye diagrama UML, documentación completa con ejemplos para CU01/CU02/CU04/CU05, integración con Agenda, y documentación del proceso de IA. Principios SOLID (SRP, OCP, LSP, ISP, DIP) documentados con diagramas PlantUML específicos y ejemplos aplicados al Sistema de Turnos Médicos. PR: pendiente - @nachonervi-design (Especialista en Patrones Creacionales) PR: [#133](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/133)

- [feature/esp-patron-comportamiento-add-observer] Se aplicó el patrón Observer al Sistema de Turnos Médicos para mejorar el rendimiento. PR: [#142](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/142) - @eternalnight04 (Especialista en Patrón de Diseño de Comportamiento)

### Fixed

- [fix/coordinador-devops.md] Implementación de ia/segundo-parcial/coordinador-devops.md, pasada por alto. PR: [#149](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/149) - @britezacostaalexis-pixel(Coordinador y Devops)

- [fix/add-docs-ia-patron-builder] Agregada documentación del proceso IA para patrón Builder y principios SOLID (`ia/segundo-parcial/especialista-patron-creacional.md`). PR: [#150](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/150) - @nachonervi-design (Especialista en Patrones Creacionales)

- [fix/comportamiento-observer-1] Eliminados IDs de patron de comportamiento, se agregaron atributos para NotificacionMedio y se corrigió un archivo md de comportamiento para ser fiel al formato de entrega. PR: [#151](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/151) - @eternalnight04 (Especialista en Patrón de Diseño de Comportamiento)

- [fix/patrones-correcciones-1] Se eliminaron IDs, secciones del archivo de patrón creacional, se corrigieron índices y se aplicaron otras correcciones mínimas a los archivos md de patrón de diseño estructural y creacional. PR: [#152](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/152) - @eternalnight04 (Especialista en Patrón de Diseño de Comportamiento)

- [fix/nachonervi-reescribir-docs-creacional] Se reescribió el anexo del patrón Builder con formato académico y estructura del parcial. PR: [#153](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/153) - @nachonervi-design (Especialista en Patrones Creacionales)

- [fix/esp-patron-estructural-facade-2] Correcciones en diagrama estructural. PR: [#158](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/158) - @eternalnight04 (Especialista en Patrón de Diseño de Comportamiento)

**Nota con respecto a la PR #158:** Es una rama realizada copiando y pegando los cambios que hizo @lautarochavez14 en su PR: [#156](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/156) y en PR: [#157](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/157). Estas PRs no pudieron mergearse debido a conflictos en sus ramas, por lo tanto, para ahorrar tiempo, se decidió hacer una nueva PR que contenga estos cambios.



## [Released - Actividad Obligatoria N°4] - 2026-06-18

### Added

- [feature/analista-cu-2-3-add-anexo-cu2-cu3] Se agrega archivo analista-cu-2-3. PR: [#113](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/113) - @britezacostaalexis-pixel (Analista Funcional de Casos de Uso 2 y 3)

- [feature/analista-cu-4-5-add-anexo-cu4-cu5] Se agrega el archivo analista-cu-4-5 y el diagrama de registrar llegada. PR: [#114](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/114) - @lautarochavez14 (Analista Funcional de Casos de Uso 4 y 5)

- [feature/coordinador-devops-add-anexo-cu1] Se agrega el archivo analista-cu-1.md, un diagrama de crear turno y un analisis funcional del mismo. PR: [#116](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/116) - @eternalnight04 (Documentador y Coordinador)

- [feature/analista-cu-4-5-add-anexo-cu4-cu5] Agregados anexos de casos de uso CU04 (Autorizar Sobreturno) y CU05 (Registrar Llegada) con diagramas de secuencia completos. PR: [#129](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/129) - @lautarochavez14 (Analista Funcional de Casos de Uso 4 y 5)

- [fix/rc9-happy-path-pilares-poo] Correcciones completas de Request Changes del docente sobre Happy Path Global y Pilares POO. Se reescribió el pseudocódigo del Happy Path con tabla de trazabilidad obligatoria vinculando cada paso con las tarjetas CRC y Casos de Uso (RC9/RC21). Se regeneraron las 8 capturas de pilares POO (Encapsulamiento, Herencia, Abstracción, Polimorfismo) con contexto completo de las clases y coherencia con las descripciones del texto (RCN11/RCN12/RCN22/RCN23). Se restauró el encapsulamiento en el diagrama CU01 convirtiendo atributos públicos a privados en las clases Paciente, Secretaria, Medico, Turno y Notificacion (RCN1-RCN5). Se actualizaron las PRs #130 y #129 al changelog (RC23/RC24). PR: [#135](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/135) - @nachonervi-design (Arquitecto de Dominio)

- [fix/rcn1-rcn4-casos-uso-imagenes-duplicadas] Correcciones de Request Changes del docente sobre casos de uso CU02-CU05. En CU02 Reprogramar Turno y CU03 Cancelar Turno se agregaron los caracteres `!` faltantes en los links de diagramas para que las imágenes se visualicen incrustadas correctamente en GitHub (RCN1/RCN2). En CU04 Autorizar Sobreturno y CU05 Registrar Llegada se eliminaron las secciones duplicadas del contenido, manteniendo una única versión coherente con el diagrama final y las tarjetas CRC (RCN3/RCN4). PR: [#136](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/136) - @nachonervi-design (Arquitecto de Dominio)


- [fix/rc9-happy-path-trazabilidad] RC9: Happy Path Global reescrito con tabla de trazabilidad completa vinculando pseudocódigo con CRC y Casos de Uso. PR: [#130](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/130) - @nachonervi-design (Arquitecto de Dominio)

- [fix/correcciones-actividad-4] Se resuelven los Request Changes del docente para la reentrega de la Actividad Obligatoria N°4: Happy Path Global reescrito completamente con tabla de trazabilidad (RC9), formato markdown corregido en CU02 eliminando bloques ```md (RC5), IDs hardcodeados eliminados del diagrama final (RC10), cardinalidades y simbología UML corregidas en relaciones (RC11), índice de diagramas reestructurado según plantilla (RC13), y consistencia CRC restaurada eliminando tarjeta LlegadaPaciente e integrando sus atributos en Turno como List<String> (RC3/RC4). PR: [#122](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/122) - @nachonervi-design (Arquitecto de Dominio)

- [fix/analisis-correccion] Se corrige una linea de analisis_casos_uso.md. PR: [#117](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/117) - @eternalnight04 (Documentador y Coordinador)

- [fix/arquitecto-dominio-merge-conflicto] Se agrega el archivo arquitecto-dominio.md, happy-path-global.md, pilares-poo.md, el diagrama de clases final y capturas-pilares/. PR: [#118](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/118) - @eternalnight04 (Documentador y Coordinador)

**Notas con respecto a la PR 118**: Es una PR creada para que se pudiera mergear sin problemas con develop, ya que la [PR original #111](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/111) tuvo conflictos de merge. El autor original de dicha PR fue @nachonervi-design (Arquitecto de Dominio).

- [fix/develop-correcciones-1] Se aplican las últimas correcciones, se actualiza el README.md y el changelog. PR: [#119](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/119) - @eternalnight04 (Documentador y Coordinador)

### Fixed

- [fix/crear-turno-correcciones-1] Se corrigen 01-caso-de-uso-crear-turno.md, 01-clases-crear-turno-01.puml, analisis_casos_uso.md y 06-clases-diagrama-final.puml. PR: [#121](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/121) - @eternalnight04 (Documentador y Coordinador)

- [fix/correcciones-actividad-4] Se reescribieron archivos y request changes solicitados. PR: [#122](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/122) - @nachonervi-design (Arquitecto de Dominio)

-[fix/correcciones-diagramas.md] Corregido link del diagrama de clases. PR: [#123](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/123) - @nachonervi-design (Arquitecto de Dominio)

- [fix/crear-turno-correcciones-2] Se eliminan iDs de los diagramas y se agregaron tres nuevas tarjetas CRC: Auditoria, UsuarioDelSistema y Notificacion. PR: [#124](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/124) - @eternalnight04 (Documentador y Coordinador)

- [fix/reprogramar-turno-correcciones-1] Se renombraron clases y métodos del happy path global. PR: [#125](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/125) - @eternalnight04 (Documentador y Coordinador)

- [fix/reprogramar-turno-correcciones-2] Se renombraron clases y se agregaron links a las nuevas tarjetas crc. PR: [#126](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/126) - @eternalnight04 (Documentador y Coordinador)

- [feature/analista-cu-4-5-add-anexo-cu4-cu5] Agrega diagramas y archivos md de Registrar Llegada y Autorizar Sobreturno corregidos. PR: [#129](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/129) - @lautarochavez14 (Analista Funcional de Casos de Uso 4 y 5)

- [fix/rc9-happy-path-pilares-poo] Correcciones en Happy Path Global. PR: [#130](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/130) - @nachonervi-design (Arquitecto de Dominio)

- [fix/actualizar-archivos-1] Se agregaron los casos de uso 4 y 5 y se corrigieron archivos y diagramas. PR: [#132](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/132) - @eternalnight04 (Documentador y Coordinador)

- [fix/registrar-llegada-correcciones-1] Se volvió a agregar la tarjeta CRC llegada paciente, se corrigió el Happy Path Global y el archivo md de Registrar Llegada. PR: [#139](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/139) - @eternalnight04 (Documentador y Coordinador)

- [fix/atributos-correcciones-1] Se corrigieron las relaciones de cardinalidad, se privatizaron los atributos y se eliminaron las iDs de todas las clases de los diagramas de clases. PR: [#140](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/140) - @eternalnight04 (Documentador y Coordinador)

## [Released - Actividad Obligatoria N°3] - 2026-05-17

### Added

- [feature/esp-secuencia-add-diagrama-secuencia] Se crean diagramas de secuencia en PlantUML para los principales casos de uso. Se crea archivo `esp-secuencia.md` con documentación asociada. Cierra #88, #89, #90, #91, #92. PR: [#87](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/87) - @sofinestt (Especialista en Diagramas de Secuencia)
- [feature/doc-coord-repo-update-readme-md] Se actualiza el README y se agrega archivo de documentación de IA en ia/a3/documentador-coordinador.md. PR: [#96](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/96)
- [feature/esp-actividades-1-2-add-diagrama-actividad-1] Se agregan 2 diagramas de actividades para CU-01 Y CU-02
    PR: [#95](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/95) - @ANeicuan (Especialista en Diagrama de Actividades 1 y 2)
- [feature/esp-actividades-3-4-5-add-diagramas-actividad-3-4-5] Agrega 3 diagramas de actividades UML para casos de uso 3, 4, 5 (Cancelar Turno, Autorizar Sobreturno, Registrar Llegada) con documentación IA completa. Cierra #82, #83, #84. - @nataliacarreras96git (Especialista en Diagramas de Actividades)

### Fixed
- [fix/correcciones-rc-1-2] Correcciones en diagramas de actividades para los casos de uso "Registrar Turno Médico", "Reprogramar Turno Existente" y "Cancelar Turno". Se ajustaron diagramas, documentación y artefactos asociados para resolver observaciones académicas detectadas durante la revisión. Correcciones aplicadas sobre los RC #1, #2, #3, #4, #5, #6, #16 y #21. PR: [#100](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/100) — @britezacostaalexis-pixel
- [fix/correccion-readme] Simplificación y reorganización del README para cumplir las observaciones RC39. Se eliminó contenido no requerido para la entrega, manteniendo una estructura minimalista con integrantes actualizados, roles de la Actividad Obligatoria N°3 y navegación esencial del proyecto. PR: [#98](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/98) — @nachonervi-design
- [fix/correccion-changelog] Corrección y normalización de la estructura de changelog.md. Se unificaron secciones duplicadas de Unreleased, Release y Added, reubicando la información en las secciones correspondientes sin pérdida de trazabilidad histórica, para cumplir las observaciones RC7 y RC8. PR: [#99](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/99) — @nachonervi-design
- [fix/esp-secuencia-fix-diagramas-secuencias] Correcciones derivadas de las observaciones RC #24, #25, #26, #27, #28, #29, #30, #31, #32, #34, #35, #36, #37 y #38. Se actualizaron los diagramas de secuencia, sus archivos PlantUML, exportaciones gráficas e índice de navegación para asegurar consistencia, trazabilidad y cumplimiento de los requisitos de la Actividad Obligatoria N°3. PR: [#101](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/101) — @eternalnight04
- [fix/correciones-diagramasUML-formato] Mínima corrección de formato en el archivo diagramasUML.md. PR: [#102](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/102) - @eternalnight04
- [fix/correcciones-rc-4-5] Correcciones correspondientes a los RC 11, 20, 14, 15, 17, 18, 22 y 23. PR: [#103](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/103) - @britezacostaalexis-pixel
- [fix/secuencias-correcciones-1] Correcciones del índice de diagramas de actividades y en los diagramas de secuencia. PR: [#104](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/104) - @eternalnight04
- [fix/diagramas-secuencias-2] Correcciones en la numeración de los casos de uso, los mensajes de retorno de los diagramas de secuencias y se agregaron las últimas PR no registradas en el changelog. PR: [#105](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/105) - @eternalnight04
-[fix/diagramas-numeracion] Corrección en la numeración del índice de los diagramas de secuencias. PR: [#106](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/106) - @eternalnight04
-[fix/diagramas-correcciones-2] Correcciones en diagramas de secuencias, se hicieron retoques y corrigieron mensajes de metodos. PR: [#108](https://github.com/eternalnight04/SistemaTurnosMedicos/pull/108) - @eternalnight04


---

## [Released - Actividad Obligatoria N°2] - 2026-04-17

### Added

- [feature/especialista-escenarios-casos-uso] 5 escenarios de casos de uso completos con 16 campos cada uno. PR: [#48](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/48) - @nataliacarreras96git (Especialista en Escenarios)
- [feature/modelador-diagramas-casos-uso] 5 diagramas PlantUML de casos de uso. PR: [#51](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/51) - @TomasTorres27 (Modelador de Diagramas)
- [feature/disenador-tarjetas-crc-paciente] Tarjeta CRC: Paciente. PR: [#54](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/54) - @ferreyrasantiagojoaquin-lab (Diseñador CRC)
- [feature/disenador-tarjetas-crc-medico] Tarjeta CRC: Médico. PR: [#60](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/60) - @ferreyrasantiagojoaquin-lab (Diseñador CRC)
- [feature/disenador-tarjetas-crc-turno] Tarjeta CRC: Turno. PR: [#61](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/61) - @ferreyrasantiagojoaquin-lab (Diseñador CRC)
- [feature/disenador-tarjetas-crc-agenda] Tarjeta CRC: Agenda. PR: [#57](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/57) - @ferreyrasantiagojoaquin-lab (Diseñador CRC)
- [feature/disenador-tarjetas-crc-secretaria] Tarjeta CRC: Secretaria. PR: [#58](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/58) - @ferreyrasantiagojoaquin-lab (Diseñador CRC)
- [feature/disenador-tarjetas-crc-documentation] Documentación del proceso Copilot para Diseñador CRC. PR: [#63](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/63) - @ferreyrasantiagojoaquin-lab (Diseñador CRC)

### Changed

### Fixed

- [release/actividad-obligatoria-2] Correcciones RC1–RC11 solicitadas en review: tarjeta paciente en release, escenarios a 4 tablas, índices, cancelar-turno <<include>>, documentación IA con triple backtick. Commit: [bd75211](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/commit/bd75211) - @nataliacarreras96git (Documentadora y Coordinadora)
- [release/actividad-obligatoria-2] Correcciones de formato adicionales: herramientas_agile, diagramasUML. Commit: [227174e](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/commit/227174e) - @nataliacarreras96git (Documentadora y Coordinadora)
- [release/actividad-obligatoria-2] Entradas retroactivas en changelog para commits bd75211 y 227174e. Commit: [b5eae62](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/commit/b5eae62) — @nataliacarreras96git (Documentadora y Coordinadora)
- [release/actividad-obligatoria-2] Correcciones de índice tarjetas CRC, secciones de escenarios y formato changelog. Commit: [f335ed2](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/commit/f335ed2) — @nataliacarreras96git (Documentadora y Coordinadora)
- [release/actividad-obligatoria-2] Corrección de formato Keep Changelog A2: eliminación de párrafos narrativos. Commit: [71ccbe1](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/commit/71ccbe1) — @nataliacarreras96git (Documentadora y Coordinadora)
- [fix/correcciones-fix] Correcciones en changelog, escenarios_de_casos_de_uso.md y movimiento de tarjeta paciente a anexos/. PR: [#73](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/73) - @nataliacarreras96git (Documentadora y Coordinadora)
- [fix/resolver-rcs-a2-changelog]  Correccion de entradas en changelog con [#?] placeholder en ### Added y entrada en ### Changed sin PR link. Correccion de formato de PRs. PR [#78](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/78) - @nataliacarreras96git (Documentadora y Coordinadora)
- [fix/correcciones-changelog-fix] Se elimina entrada de changelog de la parte "Changed" al ser texto plano y no corresponder a ninguna PR, se eliminan entradas de PRs #75 y #76 del changelog ya que correspondían a correcciones del parcial, se agrega entrada de PR #78. PR [#79](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/79) - @sofinestt 
- [fix/correciones-diagramasUML-formato] Corrección del archivo `diagramasUML.md` para adecuarlo al formato de entrega requerido por la cátedra. Se reorganizó la estructura y presentación del índice de diagramas UML para mantener consistencia con los estándares de documentación del proyecto y resolver la observación RC #40. PR: [#102](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/102) — @eternalnight04
---

## [Release Actividad Obligatoria N°1] - 2026-03-26

Se consolidan todos los cambios realizados en la rama develop para la entrega final del trabajo práctico.

### Added

- [feature/modelador-casos-uso] Documentación de 5 casos de uso completos (UC-01 a UC-05) a partir de fuentes de dominio. PR: [#6](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/6) - @ademarco97 (Modelador)
- [feature/analista-requerimientos] Definición de requisitos funcionales y no funcionales del sistema. PR: [#8](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/8) - @nachonervi-design (Analista)
- [feature/diseniador-clases-add-boceto-inicial] Creación del diagrama de clases en formatos .excalidraw, .png y .puml. PR: [#9](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/9) - @LuchoBarrionuevo13 (Diseñador)
- [feature/doc-coord-repo-update-readme-md] Creación del README, introducción POO y anexos. PR: [#12](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/12) - @nataliacarreras96git (Documentadora)
- [feature/casos-uso-completos-g4] Completar 5 casos de uso (CU-01 a CU-05) con flujos principal y alternativo, actores y decisiones específicas del dominio. PR: [#34] (https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/34) - @TomasTorres27 (Diseñador de Clases Iniciales)
- [feature/casos-uso-g6-contenido-g4] Aporte de contenido de casos de uso del Grupo 6 adaptado al dominio de Sistema de Turnos Médicos (CU-01 a CU-05) con actores reales, flujos principal y alternativo. PR: [#36](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/36) - @ferreyrasantiagojoaquin-lab (Modelador)
- [feature/diagrama-mejorado-g4] Revisión y mejora del diagrama de clases en Excalidraw realizado por Natalia. Validación de entidades, relaciones y atributos según especificación del sistema de turnos médicos. PR: [#35](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/35) - @nataliacarreras96git (Coordinadora)

### Changed

- [feature/doc-coord-repo-update-readme-md] Actualización del README e introducción para mejorar claridad. PR: [#12](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/12) - @nataliacarreras96git (Documentadora)
- [feature/estructura-carpetas] Reorganización de carpetas (anexos/ y diagramas/). PR: [#10](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/10) - @nataliacarreras96git (Documentadora)
- [feature/normalizacion-nombres] Renombrado de carpetas a minúsculas (Diagramas → diagramas, 01-Diagrama-Clases → 01-diagrama-clases). PR: [#11](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/11) - @nataliacarreras96git (Documentadora)
- [feature/diagrama-mejorado-g4] Revisión y mejora del diagrama de clases en Excalidraw realizado por Natalia. Validación de entidades, relaciones y atributos según especificación del sistema de turnos médicos. PR: [#35](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/35) - @nataliacarreras96git (Coordinadora)

### Fixed

- [fix/revert-pr-14] Revert de PR #14 - Merge sin aprobación según corrección del profesor. Corrección de procedimiento GitFlow. - @nataliacarreras96git (Coordinadora)
- [fix/revert-pr-23] Revert de PR #23 - Merge sin aprobación según corrección del profesor. Corrección de procedimiento GitFlow. - @nataliacarreras96git (Coordinadora)
- [feature/doc-coord-correccion-changelog-a1] Corrección de changelog.md - formato exacto según especificación del profesor y agregación de entradas faltantes. PR: [#31](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/31) - @nataliacarreras96git (Documentadora y Coordinadora)
- [feature/doc-coord-correccion-readme-rnf] Corrección del README (tabla integrantes con Rol y matrículas actualizadas) e introduccion.md (Polimorfismo en lenguaje natural + 5 RNFs específicos). PR: [#32](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/32) - @nataliacarreras96git (Documentadora y Coordinadora)
- [fix/changelog-completo-todos-los-pr] Agregación de entradas faltantes en changelog: reverts de PR #14 y #23, y correcciones de PR #31 y #32. PR: [#33](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/33) - @nataliacarreras96git (Documentadora y Coordinadora)
- [fix/casos-uso-completos-g4] Corrección de 5 casos de uso completos (CU-01: Crear Turno, CU-02: Reprogramar, CU-03: Cancelar, CU-04: Autorizar Sobreturno, CU-05: Registrar Llegada) con actores, flujos principal y alternativo, precondiciones y postcondiciones. PR: [#34](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/34) - @TomasTorres27 (Diseñador)
- [fix/correccion-completa-actividad-1] Correcciones finales para la entrega: Agregar diagrama de clases (01-boceto-inicial.excalidraw y .png), enlace NotebookLM en anexos/introduccion.md, eliminar introduccion.md de raíz (versión correcta en anexos/), arreglar encoding UTF-8 en anexos/anexos.md. PR: [#42](https://github.com/nataliacarreras96git/SistemaTurnosMedicos/pull/42) - @nataliacarreras96git (Coordinadora)

