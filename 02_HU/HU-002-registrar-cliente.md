# HU-002 --- Registrar cliente

## Identificación

  Campo             Valor
  ----------------- ---------------------------
  ID                HU-002
  Título            Registrar cliente
  Módulo            Gestión de clientes
  Actor principal   Administrador
  Prioridad         CRÍTICA
  Estimación        Pendiente de refinamiento
  Dependencias      Pendiente de definición.
  Estado            Pendiente

## Historia de usuario

> Como Administrador, quiero registrar clientes asociados a documentos,
> para disponer de su información durante la gestión y seguimiento
> documental.

## Dependencias

Pendiente de definición.

## Precondiciones

-   El Administrador debe tener acceso al módulo de registro.
-   Los datos requeridos del cliente deben estar disponibles; los campos
    específicos están Pendientes de definición.

## Reglas de negocio

### RN-01 --- Cliente sin acceso directo

El cliente no utiliza el sistema directamente.

### RN-02 --- Gestión autorizada

Los datos y documentos del cliente son gestionados por personal
autorizado.

## Descripción funcional

El Administrador registra la información del cliente para que quede
disponible en búsquedas, reportes y asociación con documentos. Los
campos específicos del cliente están **Pendientes de definición**. Un
error no debe producir un cliente parcialmente registrado.

## Criterios de aceptación

### CA-01 --- Registro exitoso

**Dado que** el Administrador accede al módulo de registro.

**Cuando** ingresa los datos requeridos y guarda.

**Entonces** el cliente queda registrado y disponible para búsquedas y
reportes.

### CA-02 --- Sin acceso directo

**Dado que** el cliente ha sido registrado.

**Cuando** se gestiona su información.

**Entonces** el sistema no le concede acceso directo.

## Caso exitoso

Entrada: datos requeridos del cliente → Validación: campos obligatorios
→ Procesamiento: registro → Resultado: cliente disponible para
asociación, búsquedas y reportes.

## Casos de error

### Error 1

-   **Condición:** Datos obligatorios incompletos
-   **Acción:** Intentar guardar el cliente
-   **Resultado:** No completar el registro
-   **Datos que NO deben modificarse:** No almacenar un cliente parcial.

## Integridad / no modificación

Si el registro falla, no debe almacenarse parcialmente el cliente ni
alterarse información de otros registros.

## Gherkin / BDD

``` gherkin
Feature: Registro de clientes

  Scenario: Registrar cliente
    Given el Administrador accede al registro de clientes
    When ingresa los datos requeridos y guarda
    Then el cliente queda disponible para búsquedas y reportes
    And no obtiene acceso directo al sistema
```
