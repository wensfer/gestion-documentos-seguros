# HU-012 --- Controlar acceso por tipo de usuario

## Identificación

  -----------------------------------------------------------------------
  Campo                               Valor
  ----------------------------------- -----------------------------------
  ID                                  HU-012

  Título                              Controlar acceso por tipo de
                                      usuario

  Módulo                              Control de acceso

  Actor principal                     Sistema

  Prioridad                           CRÍTICA

  Estimación                          Pendiente de refinamiento

  Dependencias                        HU-001 Registrar usuario --- el
                                      usuario debe contar con un rol
                                      definido para aplicar el control de
                                      acceso.

  Estado                              Pendiente
  -----------------------------------------------------------------------

## Historia de usuario

> Como usuario autorizado, quiero acceder únicamente a las
> funcionalidades correspondientes a mi rol, para proteger la
> información y mantener el acceso restringido según el tipo de usuario.

## Dependencias

HU-001 Registrar usuario --- el usuario debe contar con un rol definido
para aplicar el control de acceso.

## Precondiciones

-   El usuario debe estar registrado.
-   El usuario debe tener un rol definido.

## Reglas de negocio

### RN-01 --- Roles autorizados

Los roles con acceso son ADM, SEG y SUPER.

### RN-02 --- Cliente bloqueado

El cliente no utiliza el sistema directamente.

### RN-03 --- Acceso por rol

El acceso a las funcionalidades debe restringirse según el tipo de
usuario.

### RN-04 --- Privacidad

La información de clientes debe ser gestionada por personal autorizado.

## Descripción funcional

El sistema identifica el rol del usuario y controla el acceso a las
funcionalidades. El Administrador gestiona información general y
usuarios; el Personal de seguros registra, consulta y realiza
seguimiento; el Responsable/Supervisor consulta, genera reportes y
supervisa. El cliente no accede directamente. Los permisos granulares no
especificados quedan como **Pendiente de definición**.

## Criterios de aceptación

### CA-01 --- Acceso autorizado

**Dado que** existe un usuario con rol autorizado.

**Cuando** solicita una funcionalidad correspondiente a su rol.

**Entonces** el sistema permite el acceso.

### CA-02 --- Acceso no autorizado

**Dado que** un usuario solicita una funcionalidad no permitida para su
rol.

**Cuando** intenta ejecutar la operación.

**Entonces** el sistema impide la operación.

### CA-03 --- Cliente

**Dado que** el cliente no utiliza directamente el sistema.

**Cuando** se intenta acceder como cliente.

**Entonces** el sistema bloquea el acceso.

## Caso exitoso

Entrada: usuario y rol → Validación: autorización → Procesamiento:
comprobación de permisos → Resultado: acceso a funcionalidades
correspondientes.

## Casos de error

### Error 1

-   **Condición:** Funcionalidad no autorizada
-   **Acción:** Intentar ejecutarla
-   **Resultado:** Bloquear la operación
-   **Datos que NO deben modificarse:** No modificar la información
    asociada.

### Error 2

-   **Condición:** Acceso de cliente
-   **Acción:** Intentar acceder
-   **Resultado:** Bloquear el acceso
-   **Datos que NO deben modificarse:** No modificar información.

## Integridad / no modificación

Una operación rechazada por autorización no debe producir modificaciones
en documentos, clientes, fechas, estados, renovaciones ni historial.

## Gherkin / BDD

``` gherkin
Feature: Control de acceso por tipo de usuario

  Scenario: Acceso autorizado
    Given existe un usuario con un rol autorizado
    When solicita una funcionalidad correspondiente a su rol
    Then el sistema permite el acceso

  Scenario: Acceso no autorizado
    Given existe un usuario con un rol definido
    When solicita una funcionalidad no autorizada
    Then el sistema impide la operación
    And no modifica información

  Scenario: Acceso de cliente
    Given el cliente no utiliza directamente el sistema
    When intenta acceder al sistema
    Then el sistema bloquea el acceso
```
