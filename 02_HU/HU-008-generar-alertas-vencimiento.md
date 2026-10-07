# HU-008 --- Generar alertas de vencimiento

## Identificación

  -----------------------------------------------------------------------
  Campo                               Valor
  ----------------------------------- -----------------------------------
  ID                                  HU-008

  Título                              Generar alertas de vencimiento

  Módulo                              Alertas

  Actor principal                     Sistema

  Prioridad                           CRÍTICA

  Estimación                          Pendiente de refinamiento

  Dependencias                        HU-007 Identificar documentos
                                      próximos a vencer --- la alerta se
                                      genera al identificar los umbrales.

  Estado                              Pendiente
  -----------------------------------------------------------------------

## Historia de usuario

> Como Personal de seguros, quiero recibir alertas de los documentos
> próximos a vencer, para realizar oportunamente su seguimiento.

## Dependencias

HU-007 Identificar documentos próximos a vencer --- la alerta se genera
al identificar los umbrales.

## Precondiciones

-   El documento debe estar registrado.
-   Debe existir una fecha de vencimiento válida.
-   El sistema debe identificar uno de los umbrales definidos.

## Reglas de negocio

### RN-01 --- Umbrales de alerta

Las alertas se generan a los 30, 15 y 7 días antes del vencimiento.

### RN-02 --- Visibilidad

La alerta debe ser visible para el usuario correspondiente.

### RN-03 --- Destinatario

El criterio del PRD indica como destinatario al Personal de seguros
asignado; el escenario también contempla usuarios correspondientes,
incluido Responsable.

## Descripción funcional

Cuando el sistema identifica un documento en un umbral de 30, 15 o 7
días, genera una alerta visible para el usuario correspondiente. El
canal adicional de notificación y la lógica exacta de asignación del
responsable quedan como **Pendiente de definición**.

## Criterios de aceptación

### CA-01 --- Generación de alerta

**Dado que** el sistema identifica un umbral de 30, 15 o 7 días.

**Cuando** la fecha se encuentra dentro del umbral.

**Entonces** genera una alerta visible para el usuario correspondiente.

### CA-02 --- Correspondencia

**Dado que** se genera una alerta.

**Cuando** existe personal asignado al seguimiento.

**Entonces** la alerta corresponde al personal autorizado indicado.

## Caso exitoso

Entrada: documento identificado en umbral → Validación: fecha y
destinatario disponible → Procesamiento: generación → Resultado: alerta
visible.

## Casos de error

### Error 1

-   **Condición:** Fecha inválida o ausente
-   **Acción:** Intentar generar la alerta
-   **Resultado:** No generar una alerta incorrecta
-   **Datos que NO deben modificarse:** No modificar fechas ni estado
    por causa del error de alerta.

### Error 2

-   **Condición:** Asignación de destinatario no definida
-   **Acción:** Intentar determinar destinatario
-   **Resultado:** Pendiente de definición
-   **Datos que NO deben modificarse:** No alterar el documento.

## Integridad / no modificación

Si falla la generación de la alerta, no deben modificarse las fechas ni
producirse cambios parciales en el documento.

## Gherkin / BDD

``` gherkin
Feature: Generación de alertas de vencimiento

  Scenario: Generar alerta de vencimiento
    Given existe un documento próximo a vencer
    When alcanza un umbral de 30, 15 o 7 días
    Then el sistema genera una alerta visible para el usuario correspondiente
```
