# HU-004 --- Registrar fechas de vigencia y vencimiento

## Identificación

  -----------------------------------------------------------------------
  Campo                               Valor
  ----------------------------------- -----------------------------------
  ID                                  HU-004

  Título                              Registrar fechas de vigencia y
                                      vencimiento

  Módulo                              Gestión documental

  Actor principal                     Personal de seguros

  Prioridad                           CRÍTICA

  Estimación                          Pendiente de refinamiento

  Dependencias                        HU-003 Registrar documento --- las
                                      fechas deben asociarse a un
                                      documento existente.

  Estado                              Pendiente
  -----------------------------------------------------------------------

## Historia de usuario

> Como Personal de seguros, quiero registrar las fechas de vigencia y
> vencimiento de cada documento, para controlar su período de validez y
> permitir su seguimiento.

## Dependencias

HU-003 Registrar documento --- las fechas deben asociarse a un documento
existente.

## Precondiciones

-   El documento debe estar registrado.
-   El Personal de seguros debe tener acceso autorizado.

## Reglas de negocio

### RN-01 --- Fechas por documento

Cada documento sujeto a seguimiento registra fecha de vigencia y fecha
de vencimiento.

### RN-02 --- Integridad de datos

Las fechas deben validarse y mantenerse consistentes.

### RN-03 --- Sin duplicidades

Los datos de vigencia y vencimiento deben mantenerse sin duplicidades
según las reglas de datos del PRD.

## Descripción funcional

El Personal de seguros registra las fechas de vigencia y vencimiento del
documento. El sistema valida los campos obligatorios y almacena las
fechas asociadas al documento. La relación exacta permitida entre ambas
fechas no está detallada en el PRD y queda como **Pendiente de
definición**.

## Criterios de aceptación

### CA-01 --- Registro de fechas

**Dado que** existe un documento registrado.

**Cuando** el Personal de seguros registra las fechas requeridas.

**Entonces** el sistema almacena las fechas asociadas al documento.

### CA-02 --- Campos obligatorios

**Dado que** se registran las fechas del documento.

**Cuando** falta una fecha requerida.

**Entonces** el sistema no completa la operación.

## Caso exitoso

Entrada: fechas de vigencia y vencimiento → Validación: campos
obligatorios y consistencia → Procesamiento: asociación al documento →
Resultado: fechas registradas.

## Casos de error

### Error 1

-   **Condición:** Fecha obligatoria ausente
-   **Acción:** Intentar guardar
-   **Resultado:** Rechazar la operación
-   **Datos que NO deben modificarse:** No modificar fechas válidas
    existentes.

## Integridad / no modificación

Si la operación falla, no deben modificarse parcialmente las fechas ni
el estado del documento.

## Gherkin / BDD

``` gherkin
Feature: Registro de fechas de vigencia y vencimiento

  Scenario: Registrar fechas correctamente
    Given existe un documento registrado
    When el Personal de seguros registra las fechas requeridas
    Then el sistema almacena las fechas asociadas al documento
```
