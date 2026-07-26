# Abstracción

La abstracción en el diseño orientado a objetos consiste en separar lo esencial de lo incidental: definir qué hace una entidad sin exponer cómo lo hace. Esta técnica permite modelar el dominio en términos de comportamientos y responsabilidades relevantes, mientras que los detalles de implementación quedan ocultos detrás de clases abstractas, interfaces o métodos bien definidos.

En el proyecto del sistema de turnos médicos, la abstracción es clave para mantener el modelo flexible y comprensible. Ayuda a que el sistema dependa de conceptos generales (como un `UsuarioDelSistema` o una operación de cambio de estado de turno) en lugar de depender de clases concretas específicas. Esto reduce el acoplamiento y facilita la extensión del sistema sin modificar las partes existentes.

Relación con SOLID y patrones de diseño:
- OCP (Open/Closed Principle): la abstracción permite que nuevas subclases se agreguen sin alterar el código que trabaja sobre la superclase abstracta.
- LSP (Liskov Substitution Principle): los clientes consumen el contrato abstracto, de modo que cualquier implementación concreta puede sustituir a la abstracción sin cambiar el comportamiento esperado.
- DIP (Dependency Inversion Principle): los módulos de alto nivel dependen de abstracciones en lugar de detalles concretos.
- Patrones como Strategy, Template Method o Facade suelen apoyarse en abstracciones para definir comportamientos intercambiables y ocultar complejidad.

## Ejemplo en el proyecto

![Abstracción en el proyecto](../../diagramas/01-diagrama-clases/capturas-pilares/poo-abstraccion-ejemplo-1.png)

En este diagrama se observa la clase abstracta `UsuarioDelSistema` que agrupa atributos y métodos comunes a `Paciente`, `Medico` y `Secretaria`. Estas subclases concretas extienden la abstracción básica con comportamientos específicos del rol, mientras que el resto del sistema puede trabajar con el tipo general `UsuarioDelSistema`.

Justificación técnica:
- `UsuarioDelSistema` actúa como una abstracción de nivel superior que define la interfaz común de usuarios y oculta detalles específicos de cada tipo de usuario.
- Las subclases `Paciente`, `Medico` y `Secretaria` implementan esta abstracción con sus propias propiedades y responsabilidades, cumpliendo LSP y facilitando nuevas extensiones.

## Ejemplo de código

```
java
public abstract class UsuarioDelSistema {
    protected int id;
    protected String nombre;
    protected String email;
    protected String telefono;
    private String contrasena;

    public UsuarioDelSistema(int id, String nombre, String email, String telefono, String contrasena) {
        this.id = id;
        this.nombre = nombre;
        this.email = email;
        this.telefono = telefono;
        this.contrasena = contrasena;
    }

    public boolean autenticar(String password) {
        return this.contrasena.equals(password);
    }

    public abstract void actualizarDatos();
}

public class Paciente extends UsuarioDelSistema {
    private String obraSocial;

    public Paciente(int id, String nombre, String email, String telefono, String contrasena, String obraSocial) {
        super(id, nombre, email, telefono, contrasena);
        this.obraSocial = obraSocial;
    }

    @Override
    public void actualizarDatos() {
        // Implementación específica del paciente
    }
}

```

Justificación técnica:
- El ejemplo de `UsuarioDelSistema` muestra una abstracción explícita: define la estructura y el comportamiento común a todos los usuarios sin proporcionar una implementación completa para `actualizarDatos()`.
- `Paciente` hereda esa abstracción y ofrece una implementación concreta, lo que permite que el sistema manipule distintos tipos de usuario mediante el mismo tipo base.
- El método `cambiarEstado` de `Turno` abstrae la operación de cambio de estado y encapsula las reglas de negocio de validación dentro de la propia clase.