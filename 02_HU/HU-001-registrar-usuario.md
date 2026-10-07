# HU-001 --- Registrar usuario

## Identificación

  Campo             Valor
  ----------------- ---------------------------
  ID                HU-001
  Título            Registrar usuario
  Módulo            Gestión de usuarios
  Actor principal   Administrador
  Prioridad         CRÍTICA
  Estimación        Pendiente de refinamiento
  Dependencias      Pendiente de definición.
  Estado            Pendiente

## Historia de usuario

> Como Administrador, quiero registrar usuarios con un rol definido,
> para gestionar el acceso del personal autorizado al sistema.

## Dependencias

Pendiente de definición.

## Precondiciones

-   El Administrador debe tener acceso al sistema.
-   El usuario debe registrarse con un rol definido.

## Reglas de negocio

### RN-01 --- Rol definido

Todo usuario registrado debe contar con un rol definido.

### RN-02 --- Acceso autorizado

El sistema está destinado a personal autorizado con roles ADM, SEG o
SUPER.

### RN-03 --- Cliente sin acceso

El cliente no utiliza el sistema directamente.

## Descripción funcional

El Administrador registra un usuario y le asigna un rol. Los datos
específicos del usuario no están definidos en el PRD, por lo que quedan
como **Pendiente de definición**. Si el registro es válido, el usuario
queda almacenado con su rol; si falla, no debe generarse un registro
parcial.

## Criterios de aceptación

### CA-01 --- Registro exitoso

**Dado que** el Administrador accede al registro de usuarios.

**Cuando** registra un usuario con un rol definido.

**Entonces** el sistema almacena el usuario con el rol correspondiente.

### CA-02 --- Rol obligatorio

**Dado que** se está registrando un usuario.

**Cuando** se intenta guardar sin un rol definido.

**Entonces** el sistema no completa el registro.

## Caso exitoso

Entrada: datos del usuario y rol definido → Validación: información
requerida → Procesamiento: registro → Resultado: usuario registrado con
su rol.

## Casos de error

### Error 1

-   **Condición:** Usuario sin rol
-   **Acción:** Intentar guardar el registro
-   **Resultado:** El registro es rechazado
-   **Datos que NO deben modificarse:** No se registra parcialmente el
    usuario.

## Integridad / no modificación

Si la operación falla, no debe almacenarse parcialmente el usuario ni
modificarse información de otros usuarios.

## Gherkin / BDD

``` gherkin
Feature: Registro de usuarios

  Scenario: Registrar usuario con rol definido
    Given el Administrador accede al registro de usuarios
    When registra un usuario con un rol definido
    Then el sistema almacena el usuario con el rol correspondiente

  Scenario: Intentar registrar usuario sin rol
    Given el Administrador está registrando un usuario
    When intenta guardar sin un rol definido
    Then el sistema no completa el registro
```
