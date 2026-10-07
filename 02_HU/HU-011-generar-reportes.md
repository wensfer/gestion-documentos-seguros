# HU-011 --- Generar reportes

## Identificación

  -----------------------------------------------------------------------
  Campo                               Valor
  ----------------------------------- -----------------------------------
  ID                                  HU-011

  Título                              Generar reportes

  Módulo                              Reportes

  Actor principal                     Responsable-Supervisor /
                                      Administrador

  Prioridad                           BAJA

  Estimación                          Pendiente de refinamiento

  Dependencias                        HU-003 Registrar documento --- los
                                      reportes utilizan información
                                      documental. HU-006 Clasificar
                                      documentos por estado --- los
                                      reportes incluyen estados. HU-004
                                      Registrar fechas de vigencia y
                                      vencimiento --- los reportes
                                      incluyen vencimientos.

  Estado                              Pendiente
  -----------------------------------------------------------------------

## Historia de usuario

> Como Responsable/Supervisor o Administrador, quiero generar reportes
> del estado y vencimiento de los documentos, para disponer de
> información consolidada para su seguimiento.

## Dependencias

HU-003 Registrar documento --- los reportes utilizan información
documental. HU-006 Clasificar documentos por estado --- los reportes
incluyen estados. HU-004 Registrar fechas de vigencia y vencimiento ---
los reportes incluyen vencimientos.

## Precondiciones

-   El usuario debe tener un rol autorizado para reportes.
-   Debe existir información documental registrada para producir
    contenido en el reporte.

## Reglas de negocio

### RN-01 --- Actores autorizados

Los reportes corresponden al Responsable/Supervisor y Administrador.

### RN-02 --- Contenido

Los reportes contemplan estado de documentos y vencimientos.

## Descripción funcional

El usuario autorizado solicita un reporte basado en la información
registrada de documentos, estados y vencimientos. El formato de
exportación, campos exactos y opciones de impresión no están definidos
en el PRD y quedan como **Pendiente de definición**.

## Criterios de aceptación

### CA-01 --- Generación de reporte

**Dado que** existe información documental registrada.

**Cuando** el Responsable/Supervisor o Administrador solicita un
reporte.

**Entonces** el sistema presenta la información correspondiente a
estados y vencimientos.

### CA-02 --- Acceso

**Dado que** un usuario no tiene autorización para reportes.

**Cuando** intenta acceder a la funcionalidad.

**Entonces** el sistema impide la operación.

## Caso exitoso

Entrada: solicitud de reporte → Validación: autorización y datos
disponibles → Procesamiento: consulta y organización → Resultado:
reporte con información correspondiente.

## Casos de error

### Error 1

-   **Condición:** Usuario no autorizado
-   **Acción:** Solicitar reporte
-   **Resultado:** Bloquear la operación
-   **Datos que NO deben modificarse:** No modificar datos.

### Error 2

-   **Condición:** Sin información correspondiente
-   **Acción:** Solicitar reporte
-   **Resultado:** No inventar registros inexistentes
-   **Datos que NO deben modificarse:** No modificar información
    original.

## Integridad / no modificación

La generación del reporte no debe modificar documentos, estados, fechas
ni historial.

## Gherkin / BDD

``` gherkin
Feature: Generación de reportes

  Scenario: Generar reporte de documentos
    Given existe información documental registrada
    And el usuario tiene un rol autorizado
    When solicita un reporte de estados y vencimientos
    Then el sistema presenta la información correspondiente
```
