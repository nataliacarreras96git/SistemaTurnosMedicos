# Polimorfismo

El polimorfismo es la capacidad de tratar objetos de diferentes clases derivadas como si fueran instancias de una misma superclase. En el diseño orientado a objetos, esto permite escribir código genérico y reusable, donde el comportamiento concreto se determina en tiempo de ejecución según la clase real del objeto.

En el proyecto del sistema de turnos médicos, el polimorfismo se aplica cuando el sistema maneja usuarios mediante la clase base `UsuarioDelSistema` y delega la ejecución de métodos como `actualizarDatos()` a cada tipo concreto de usuario (`Paciente`, `Medico`, `Secretaria`). Esto permite que el código de negocio trabaje con una interfaz común, sin conocer las diferencias de implementación de cada rol.

Relación con SOLID y patrones de diseño:
- LSP (Liskov Substitution Principle): el polimorfismo es la base para sustituir una subclase por su superclase sin alterar el comportamiento del sistema.
- DIP (Dependency Inversion Principle): los módulos dependen de abstracciones generales en lugar de clases concretas, lo que facilita el reemplazo de implementaciones.
- OCP (Open/Closed Principle): el código puede extenderse con nuevas subclases sin cambiar las partes que consumen la abstracción.
- Patrones como Strategy, Command y Observer utilizan polimorfismo para invocar comportamientos distintos desde una interfaz común.

## Ejemplo en el proyecto

![Polimorfismo en el proyecto](../../diagramas/01-diagrama-clases/capturas-pilares/poo-polimorfismo-ejemplo-1.png)

El diagrama muestra la clase base `UsuarioDelSistema` y sus derivadas `Paciente`, `Medico` y `Secretaria`. El sistema puede mantener una lista de UsuarioDelSistema y ejecutar métodos como `actualizarDatos()` en cada objeto, dejando que la implementación específica se resuelva según el tipo real del usuario.

Esta estructura refleja el polimorfismo porque permite que el mismo mensaje (`actualizarDatos()`) se comporte de forma diferente según la subclase que lo reciba. Así, el código que recorre la colección de usuarios no necesita conocer si está trabajando con un paciente, un médico o una secretaria.

Justificación técnica:
- La clase `UsuarioDelSistema` define la operación polimórfica `actualizarDatos()`.
- Las subclases concretas implementan esa operación según su lógica propia.
- El sistema puede manejar diferentes tipos de usuarios con el mismo código, favoreciendo la extensibilidad y la mantenibilidad.

## Ejemplo de Código

```
java
public void procesarActualizacion(List<UsuarioDelSistema> usuarios) {
    for (UsuarioDelSistema usuario : usuarios) {
        usuario.actualizarDatos();
    }
}

public class Secretaria extends UsuarioDelSistema {
    @Override
    public void actualizarDatos() {
        // Actualización específica para secretaria
    }
}

public class Paciente extends UsuarioDelSistema {
    @Override
    public void actualizarDatos() {
        // Actualización específica para paciente
    }
}
```

Justificación técnica:
- El método `procesarActualizacion` acepta una lista de la superclase `UsuarioDelSistema`, demostrando cómo el código trabaja con la abstracción en lugar de con tipos concretos.
- Cada subclase (`Secretaria`, `Paciente`, etc.) implementa su propia versión de `actualizarDatos()`, lo que permite comportamientos específicos sin condicionales adicionales.
- Este uso de polimorfismo reduce el acoplamiento y facilita la incorporación de nuevos tipos de usuarios en el futuro.