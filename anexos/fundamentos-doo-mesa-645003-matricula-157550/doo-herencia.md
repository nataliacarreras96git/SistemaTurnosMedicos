# Herencia

La herencia en el diseño orientado a objetos permite que una clase (subclase) reutilice atributos y comportamientos definidos en otra clase (superclase). Este principio facilita la creación de jerarquías de clases donde las características comunes se centralizan en una clase base, mientras que las especializaciones se implementan en clases derivadas.

En el proyecto del sistema de turnos médicos, la herencia se usa para compartir funcionalidades de los usuarios del sistema y reducir la duplicación de código. Esto aporta claridad al diseño, permite extender el sistema con nuevos tipos de usuarios y respeta la idea de que las clases especializadas deben construir sobre una definición general ya existente.

Relación con SOLID y patrones de diseño:
- OCP (Open/Closed Principle): la herencia permite añadir nuevas subclases sin modificar la superclase; el comportamiento común permanece cerrado al cambio y abierto a la extensión.
- LSP (Liskov Substitution Principle): cualquier objeto de una subclase debe poder sustituir a la superclase sin alterar el comportamiento del sistema.
- DIP (Dependency Inversion Principle): los componentes pueden depender de una clase base o interfaz general en vez de depender de implementaciones concretas.
- Patrones como Factory Method, Template Method y Strategy suelen apoyarse en jerarquías de clases para organizar la variación de comportamiento.

## Ejemplo en el proyecto

![Herencia en el proyecto](../../diagramas/01-diagrama-clases/capturas-pilares/poo-herencia-ejemplo-1.png)

El diagrama muestra la clase abstracta `UsuarioDelSistema` como superclase de `Paciente`, `Medico` y `Secretaria`. La superclase define los atributos comunes (id, nombre, email, telefono) y métodos compartidos (`autenticar()`, `actualizarDatos()`), mientras que cada subclase concreta incorpora comportamiento y atributos específicos de su rol.

Esta estructura refleja la herencia porque las clases especializadas extienden la definición general del usuario y reutilizan el código común sin repetirlo. Además, el diseño permite introducir nuevos tipos de usuario sin cambiar las clases existentes, lo que mejora la escalabilidad y mantiene el sistema más mantenible.

Justificación técnica:
- `UsuarioDelSistema` establece un contrato base para todos los usuarios, centralizando la lógica de autenticación y gestión de datos.
- `Paciente`, `Medico` y `Secretaria` heredan ese contrato, lo que garantiza consistencia en el comportamiento y facilita el reemplazo de una subclase por otra donde se use la superclase.
- El uso de herencia reduce la duplicación de atributos y métodos, alineándose con el principio DRY (Don’t Repeat Yourself) y con la lógica de diseño de POO.

## Ejemplo de Código

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

public class Medico extends UsuarioDelSistema {
    private String especialidad;

    public Medico(int id, String nombre, String email, String telefono, String contrasena, String especialidad) {
        super(id, nombre, email, telefono, contrasena);
        this.especialidad = especialidad;
    }

    @Override
    public void actualizarDatos() {
        // Implementación específica del médico
    }
}
```

Justificación técnica:
- El fragmento muestra a Medico heredando de `UsuarioDelSistema`, reutilizando los atributos y el comportamiento de la superclase.
- El constructor de `Medico` invoca super(...) para inicializar la parte común de la clase base y añade atributos propios como especialidad.
- La implementación de `actualizarDatos()` en la subclase prueba que la herencia permite definir comportamiento específico sin duplicar la lógica común.
