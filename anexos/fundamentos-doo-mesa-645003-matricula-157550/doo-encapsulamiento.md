# Encapsulamiento

El encapsulamiento es el principio de ocultar los detalles internos de una clase y exponer solo una interfaz controlada para interactuar con ella. En el diseño orientado a objetos, esto protege el estado del objeto, evita modificaciones directas indebidas y mantiene la invariancia de los datos.

En el proyecto del sistema de turnos médicos, el encapsulamiento ayuda a garantizar que las entidades manejen sus propios datos y reglas de negocio internamente. Por ejemplo, un turno no permite cambiar su estado o sus tiempos de llegada directamente desde afuera; en su lugar, ofrece métodos para realizar esas operaciones de forma segura.

Relación con SOLID y patrones de diseño:
- SRP (Single Responsibility Principle): al contener los datos y el comportamiento relacionados en la misma clase, cada entidad asume una única responsabilidad.
- OCP (Open/Closed Principle): cuando los detalles de implementación están encapsulados, el comportamiento externo puede permanecer estable mientras la implementación interna cambia.
- DIP (Dependency Inversion Principle): los clientes interactúan con interfaces o métodos públicos, sin conocer los detalles concretos internos.
- Patrones como Facade, Adapter y Proxy emplean encapsulamiento para ocultar complejidad y proteger el acceso directo a componentes internos.

## Ejemplo en el proyecto

![Encapsulamiento en el proyecto](../../diagramas/01-diagrama-clases/capturas-pilares/poo-encapsulamiento-ejemplo-2.png)

El diagrama muestra la clase `Turno` con atributos internos como `horaRealLlegada`, `presente` y `diferenciaMinutos`. Estos atributos no deben ser modificados directamente por otros objetos; en cambio, `Turno` expone el método `registrarLlegada(horaReal)` para calcular y actualizar su propio estado.

Otro ejemplo es la clase `UsuarioDelSistema`, donde el atributo `contrasena` es privado y solo se accede a través del método `autenticar(password)`. Esto protege el dato sensible y evita consultas directas a la contraseña.

Justificación técnica:
- `Turno` encapsula su lógica de cálculo de llegada y estado, garantizando consistencia en sus datos internos.
- `UsuarioDelSistema` protege la contraseña y proporciona una única interfaz de validación.
- El diseño reduce el acoplamiento entre clases y evita efectos secundarios no controlados al modificar atributos directamente.

## Ejemplo de Código

```
java
public class Turno {
    private LocalDateTime horaRealLlegada;
    private boolean presente;
    private int diferenciaMinutos;

    public void registrarLlegada(LocalDateTime horaReal) {
        this.horaRealLlegada = horaReal;
        this.diferenciaMinutos = calcularDiferencia(horaReal);
        this.presente = true;
    }

    private int calcularDiferencia(LocalDateTime horaReal) {
        // Lógica interna para calcular la diferencia entre hora programada y hora real
        return 0;
    }

    public boolean estaPresente() {
        return presente;
    }
}
```

Justificación técnica:
- El ejemplo muestra cómo `Turno` mantiene sus atributos internos privados y los gestiona desde métodos controlados.
- El método `calcularDiferencia()` es privado, lo que significa que la lógica de cálculo permanece dentro de la clase y no se puede alterar directamente desde fuera.
- La interfaz pública `registrarLlegada()` y `estaPresente()` expone solo lo necesario, protegiendo el estado interno del objeto.
