# Encapsulamiento

[Volver al índice de fundamentos](./fundamentos-doo.md)

## Explicación teórica

El encapsulamiento agrupa el estado y el comportamiento de un objeto y restringe el acceso directo a sus datos. Los atributos se mantienen privados y se modifican mediante operaciones controladas que preservan las reglas del dominio.

## Ejemplo 1: registro de llegada en `Turno`

`Turno` mantiene privados `horaRealLlegada`, `presente` y `diferenciaMinutos`. Estos valores están relacionados y deben actualizarse de manera consistente mediante `registrarLlegada()`.

![Atributos encapsulados de la llegada](../../diagramas/01-diagrama-clases/capturas-pilares/poo-encapsulamiento-ejemplo-1.png)

```text
class Turno
    private fechaHoraProgramada
    private horaRealLlegada
    private presente
    private diferenciaMinutos

    public method registrarLlegada(horaReal)
        horaRealLlegada = horaReal
        diferenciaMinutos = minutosEntre(fechaHoraProgramada, horaReal)
        presente = true
        cambiarEstado(PRESENTE)
    end
end
```

No se permite marcar `presente = true` sin registrar la hora ni calcular la diferencia. La operación mantiene los datos sincronizados y protege una invariante del turno.

## Ejemplo 2: contraseña de `UsuarioDelSistema`

![Contraseña privada de UsuarioDelSistema](../../diagramas/01-diagrama-clases/capturas-pilares/poo-encapsulamiento-ejemplo-2.png)

```text
class UsuarioDelSistema
    private contrasena

    public method autenticar(password): boolean
        return verificarCredencial(password, contrasena)
    end
end
```

El llamador obtiene un resultado booleano, pero no puede leer ni modificar directamente la credencial almacenada.

## Relación con SOLID

- **SRP:** `Turno` conserva las reglas propias de su estado.
- **OCP:** las operaciones públicas permiten cambiar la implementación interna sin afectar a sus clientes.
- **DIP:** otros componentes no dependen de la representación concreta de los atributos.

## Relación con los patrones

- **Builder:** el constructor privado y el `Builder` controlan la creación de `Turno`.
- **Facade:** encapsula la coordinación de varios subsistemas.
- **Observer:** `Sujeto` encapsula la colección de observadores y las operaciones de suscripción.

## Síntesis

La visibilidad privada y los métodos de negocio permiten que `Turno` y `UsuarioDelSistema` protejan su consistencia y expongan solo las operaciones necesarias.
