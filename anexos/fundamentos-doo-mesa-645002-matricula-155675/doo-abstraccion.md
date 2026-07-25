# Abstracción

[Volver al índice de fundamentos](./fundamentos-doo.md)

## Explicación teórica

La abstracción consiste en representar un concepto mediante sus características y comportamientos esenciales, dejando fuera los detalles que no son necesarios para utilizarlo. Permite trabajar con una interfaz clara —qué hace un objeto— sin depender de todos los pasos internos —cómo lo hace—.

## Ejemplo 1: `UsuarioDelSistema`

`UsuarioDelSistema` es una clase abstracta que concentra los datos y operaciones comunes de los usuarios. No representa un actor concreto que deba instanciarse; sirve como modelo general para `Paciente`, `Medico` y `Secretaria`.

![Clase abstracta UsuarioDelSistema](./images/abstraccion-usuario-del-sistema.png)

```text
abstract class UsuarioDelSistema
    private nombre
    private email
    private contrasena

    public autenticar(password): boolean
    public actualizarDatos(): void
end
```

El fragmento expone únicamente las operaciones necesarias para autenticar y actualizar a cualquier usuario. La validación de la contraseña y la forma concreta de actualización quedan ocultas. Es abstracción porque el sistema puede trabajar con el concepto general sin conocer los detalles de cada subtipo.

## Ejemplo 2: `cambiarEstado()` de `Turno`

La clase `Turno` ofrece una operación simple para solicitar un cambio de estado. Quien la invoca no necesita conocer las reglas que validan una transición.

![Método cambiarEstado de Turno](./images/abstraccion-cambiar-estado.png)

```text
method Turno.cambiarEstado(nuevoEstado)
    if transicionValida(estado, nuevoEstado) then
        estado = nuevoEstado
        agregarAlHistorial("Estado actualizado")
    else
        error "Transición de estado inválida"
    end if
end
```

La operación representa una intención del dominio y oculta sus verificaciones. Por eso abstrae una regla de negocio detrás de una acción comprensible.

## Relación con SOLID

- **SRP:** `UsuarioDelSistema` se ocupa del comportamiento común; cada subclase conserva sus responsabilidades específicas.
- **OCP:** puede agregarse otro tipo de usuario extendiendo la abstracción.
- **LSP:** las subclases deben poder utilizarse donde se espera un `UsuarioDelSistema`.
- **DIP:** los componentes pueden depender de abstracciones como `iNotificacion`, no de medios concretos.

## Relación con los patrones

- **Builder:** abstrae la construcción de `Turno`; el cliente usa `build()` sin manipular el constructor privado.
- **Facade:** `GestionTurnosFacade` oculta la coordinación entre `Agenda`, `Turno` y `Notificacion`.
- **Observer:** `iNotificacion` y `Sujeto` abstraen los contratos de observación.

## Síntesis

`UsuarioDelSistema`, `cambiarEstado()`, `GestionTurnosFacade` e `iNotificacion` permiten utilizar el sistema desde contratos simples y estables.
