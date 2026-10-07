# HU-007 --- Identificar documentos próximos a vencer

## Identificación

  -----------------------------------------------------------------------
  Campo                               Valor
  ----------------------------------- -----------------------------------
  ID                                  HU-007

  Título                              Identificar documentos próximos a
                                      vencer

  Módulo                              Seguimiento documental

  Actor principal                     Sistema

  Prioridad                           CRÍTICA

  Estimación                          Pendiente de refinamiento

  Dependencias                        HU-004 Registrar fechas de vigencia
                                      y vencimiento --- se requiere la
                                      fecha de vencimiento. HU-006
                                      Clasificar documentos por estado
                                      --- la identificación impacta el
                                      estado.

  Estado                              Pendiente
  -----------------------------------------------------------------------

## Historia de usuario

> Como Personal de seguros, quiero que el sistema identifique los
> documentos próximos a vencer, para realizar su seguimiento antes del
> vencimiento.

## Dependencias

HU-004 Registrar fechas de vigencia y vencimiento --- se requiere la
fecha de vencimiento. HU-006 Clasificar documentos por estado --- la
identificación impacta el estado.

## Precondiciones

-   El documento debe estar registrado.
-   La fecha de vencimiento debe estar registrada.

## Reglas de negocio

### RN-01 --- Umbrales

Los umbrales son 30, 15 y 7 días antes del vencimiento.

### RN-02 --- Próximo a vencer

Al alcanzar los umbrales definidos, el documento se mantiene en estado
Próximo a vencer según el criterio del PRD.

### RN-03 --- Vencido

Después de la fecha de vencimiento, el estado cambia a Vencido.

## Descripción funcional

El sistema compara la fecha de vencimiento con la fecha actual para
identificar documentos a 30, 15 o 7 días de vencer. Cuando corresponde,
el documento se identifica como Próximo a vencer. Después de la fecha de
vencimiento cambia a Vencido. El tratamiento exacto durante la propia
fecha de vencimiento queda como **Pendiente de definición**.

## Criterios de aceptación

### CA-01 --- Umbrales

**Dado que** existe un documento con fecha de vencimiento.

**Cuando** la fecha se encuentra a 30, 15 o 7 días de la fecha actual.

**Entonces** el sistema identifica el documento como Próximo a vencer.

### CA-02 --- Vencido

**Dado que** la fecha de vencimiento de un documento ya pasó.

**Cuando** el sistema evalúa el documento.

**Entonces** cambia su estado a Vencido.

## Caso exitoso

Entrada: fecha de vencimiento → Validación: fecha registrada →
Procesamiento: comparación con fecha actual → Resultado: identificación
del próximo vencimiento o vencimiento.

## Casos de error

### Error 1

-   **Condición:** Fecha de vencimiento no disponible
-   **Acción:** Intentar identificar el umbral
-   **Resultado:** No realizar una identificación incorrecta
-   **Datos que NO deben modificarse:** No modificar el estado ni la
    fecha.

## Integridad / no modificación

La identificación no debe modificar la fecha de vencimiento. Ante error,
no debe cambiarse el estado de forma parcial o incorrecta.

## Gherkin / BDD

``` gherkin
Feature: Identificación de documentos próximos a vencer

  Scenario: Identificar documento próximo a vencer
    Given existe un documento con fecha de vencimiento
    When faltan 30, 15 o 7 días para su vencimiento
    Then el sistema lo identifica como Próximo a vencer

  Scenario: Identificar documento vencido
    Given existe un documento registrado
    When ha pasado su fecha de vencimiento
    Then el sistema cambia su estado a Vencido
```
