# HU-009 --- Actualizar renovación

## Identificación

  -----------------------------------------------------------------------
  Campo                               Valor
  ----------------------------------- -----------------------------------
  ID                                  HU-009

  Título                              Actualizar renovación

  Módulo                              Renovaciones

  Actor principal                     Personal de seguros

  Prioridad                           ALTA

  Estimación                          Pendiente de refinamiento

  Dependencias                        HU-003 Registrar documento --- debe
                                      existir el documento. HU-004
                                      Registrar fechas de vigencia y
                                      vencimiento --- la renovación
                                      modifica fechas.

  Estado                              Pendiente
  -----------------------------------------------------------------------

## Historia de usuario

> Como Personal de seguros, quiero actualizar las renovaciones y las
> fechas de vigencia de un documento, para mantener actualizada su
> situación después de una renovación.

## Dependencias

HU-003 Registrar documento --- debe existir el documento. HU-004
Registrar fechas de vigencia y vencimiento --- la renovación modifica
fechas.

## Precondiciones

-   El documento debe estar registrado.
-   El Personal de seguros debe estar autorizado.

## Reglas de negocio

### RN-01 --- Actualización de fechas

La renovación permite modificar las fechas de vigencia correspondientes.

### RN-02 --- Estado

Después de la renovación, el documento puede volver a Vigente si aplica.

### RN-03 --- Historial

La renovación debe actualizar el historial del documento.

## Descripción funcional

El Personal de seguros registra la renovación y actualiza las fechas
correspondientes. El sistema refleja el estado resultante y conserva la
renovación en el historial. Los datos adicionales específicos de una
renovación quedan como **Pendiente de definición**.

## Criterios de aceptación

### CA-01 --- Renovación exitosa

**Dado que** existe un documento registrado.

**Cuando** el Personal de seguros actualiza su renovación y fechas.

**Entonces** el sistema guarda los cambios y refleja el estado
correspondiente.

### CA-02 --- Historial

**Dado que** la renovación se completa correctamente.

**Cuando** el sistema guarda los cambios.

**Entonces** registra la renovación en el historial.

## Caso exitoso

Entrada: documento y nuevas fechas → Validación: información requerida →
Procesamiento: actualización → Resultado: fechas, estado e historial
actualizados.

## Casos de error

### Error 1

-   **Condición:** Información de renovación incompleta
-   **Acción:** Intentar actualizar
-   **Resultado:** No completar la renovación
-   **Datos que NO deben modificarse:** No reemplazar los datos válidos
    anteriores.

## Integridad / no modificación

Si la renovación falla, deben conservarse los datos anteriores y
evitarse actualizaciones parciales.

## Gherkin / BDD

``` gherkin
Feature: Actualización de renovaciones

  Scenario: Actualizar renovación correctamente
    Given existe un documento registrado
    When el Personal de seguros actualiza las fechas de renovación
    Then el sistema guarda las nuevas fechas
    And refleja el estado correspondiente
    And actualiza el historial
```
