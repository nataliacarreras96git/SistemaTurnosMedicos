# Encapsulamiento

El encapsulamiento es el principio de ocultar los detalles internos de una clase y exponer solo una interfaz controlada para interactuar con ella. En el diseño orientado a objetos, esto protege el estado del objeto, evita modificaciones directas indebidas y mantiene la invariancia de los datos.

En el proyecto del sistema de turnos médicos, el encapsulamiento ayuda a garantizar que las entidades manejen sus propios datos y reglas de negocio internamente. Por ejemplo, la clase `Secretaria` no modifica directamente los atributos de la clase `Turno`; en su lugar, utiliza la clase `LlegadaPaciente` como intermediaria para registrar la llegada y actualizar el estado del turno.

Relación con SOLID y patrones de diseño:
- SRP (Single Responsibility Principle): al contener los datos y el comportamiento relacionados en la misma clase, cada entidad asume una única responsabilidad.
- OCP (Open/Closed Principle): cuando los detalles de implementación están encapsulados, el comportamiento externo puede permanecer estable mientras la implementación interna cambia.
- DIP (Dependency Inversion Principle): los clientes interactúan con interfaces o métodos públicos, sin conocer los detalles concretos internos.
- Patrones como Facade, Adapter y Proxy emplean encapsulamiento para ocultar complejidad y proteger el acceso directo a componentes internos.

## Ejemplo en el proyecto

![Encapsulamiento en el proyecto](../../diagramas/01-diagrama-clases/capturas-pilares/poo-encapsulamiento-ejemplo-2.png)

El diagrama muestra la clase `Turno` con atributos internos como `horaRealLlegada`, `presente` y `diferenciaMinutos`. Estos atributos no deben ser modificados directamente por otras clases. En el caso de registrar una llegada, la `Secretaria` crea o utiliza un objeto `LlegadaPaciente` y llama a su método `registrar()`.

La clase `LlegadaPaciente` es la intermediaria que encapsula la lógica de registro de llegada y delega la actualización del estado al `Turno` a través de métodos controlados. De esta forma, `Secretaria` no accede ni modifica directamente los atributos privados de `Turno`; solo actúa a través de una interfaz pública y bien definida.

Otro ejemplo es la clase `UsuarioDelSistema`, donde el atributo `contrasena` es privado y solo se accede a través del método `autenticar(password)`. Esto protege el dato sensible y evita consultas directas a la contraseña.

Justificación técnica:
- `Turno` encapsula su lógica de cálculo de llegada y estado, garantizando consistencia en sus datos internos.
- `LlegadaPaciente` actúa como un mediador que permite a `Secretaria` modificar el estado del turno sin acceder directamente a sus atributos.
- El diseño reduce el acoplamiento entre clases y evita efectos secundarios no controlados al modificar atributos directamente.

## Ejemplo de Código

```java
public class LlegadaPaciente {
    private LocalDateTime horaLlegada;
    private Turno turno;

    public LlegadaPaciente(Turno turno, LocalDateTime horaLlegada) {
        this.turno = turno;
        this.horaLlegada = horaLlegada;
    }

    public void registrar() {
        turno.registrarLlegada(horaLlegada);
    }
}

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
- La clase `LlegadaPaciente` encapsula el nexo entre `Secretaria` y `Turno`, evitando que la secretaria modifique directamente los atributos de la clase `Turno`.
- La interfaz pública `registrar()` de `LlegadaPaciente` y `estaPresente()` de `Turno` expone solo lo necesario, protegiendo el estado interno del objeto.