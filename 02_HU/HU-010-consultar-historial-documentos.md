# HU-010 --- Consultar historial de documentos

## Identificación

  -----------------------------------------------------------------------
  Campo                               Valor
  ----------------------------------- -----------------------------------
  ID                                  HU-010

  Título                              Consultar historial de documentos

  Módulo                              Historial

  Actor principal                     Personal de seguros /
                                      Responsable-Supervisor

  Prioridad                           ALTA

  Estimación                          Pendiente de refinamiento

  Dependencias                        HU-003 Registrar documento --- debe
                                      existir el documento. HU-009
                                      Actualizar renovación --- las
                                      renovaciones forman parte del
                                      historial.

  Estado                              Pendiente
  -----------------------------------------------------------------------

## Historia de usuario

> Como Personal de seguros o Responsable/Supervisor, quiero consultar el
> historial completo de documentos y estados, para revisar su evolución
> durante el seguimiento.

## Dependencias

HU-003 Registrar documento --- debe existir el documento. HU-009
Actualizar renovación --- las renovaciones forman parte del historial.

## Precondiciones

-   El usuario debe estar autorizado.
-   El documento debe estar registrado.

## Reglas de negocio

### RN-01 --- Archivado

El sistema conserva historial de estados y renovaciones.

### RN-02 --- Estados históricos

El historial contempla Vigente, Próximo a vencer y Vencido.

## Descripción funcional

El usuario autorizado consulta el historial disponible de un documento,
incluyendo sus estados y renovaciones registradas. Otros datos
específicos que integren el historial quedan como **Pendiente de
definición**.

## Criterios de aceptación

### CA-01 --- Consulta de historial

**Dado que** existe un documento con información histórica.

**Cuando** el usuario autorizado consulta el historial.

**Entonces** el sistema muestra los estados y renovaciones disponibles.

### CA-02 --- Solo lectura

**Dado que** el historial es consultado.

**Cuando** el usuario visualiza la información.

**Entonces** los datos históricos no son modificados por la consulta.

## Caso exitoso

Entrada: documento seleccionado → Validación: autorización y existencia
→ Procesamiento: recuperación del historial → Resultado: historial
presentado.

## Casos de error

### Error 1

-   **Condición:** Documento inexistente
-   **Acción:** Intentar consultar
-   **Resultado:** No presentar un historial ajeno o inexistente
-   **Datos que NO deben modificarse:** No modificar información.

### Error 2

-   **Condición:** Usuario no autorizado
-   **Acción:** Intentar consultar
-   **Resultado:** Bloquear acceso
-   **Datos que NO deben modificarse:** No modificar el historial.

## Integridad / no modificación

La consulta del historial es de lectura y no debe modificar registros
históricos ni el documento.

## Gherkin / BDD

``` gherkin
Feature: Consulta del historial de documentos

  Scenario: Consultar historial
    Given existe un documento con historial
    And el usuario está autorizado
    When consulta el historial del documento
    Then el sistema muestra los estados y renovaciones disponibles
    And no modifica la información
```
