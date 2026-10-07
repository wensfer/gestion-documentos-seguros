# HU-006 --- Clasificar documentos por estado

## Identificación

  -----------------------------------------------------------------------
  Campo                               Valor
  ----------------------------------- -----------------------------------
  ID                                  HU-006

  Título                              Clasificar documentos por estado

  Módulo                              Seguimiento documental

  Actor principal                     Sistema

  Prioridad                           CRÍTICA

  Estimación                          Pendiente de refinamiento

  Dependencias                        HU-003 Registrar documento --- debe
                                      existir el documento. HU-004
                                      Registrar fechas de vigencia y
                                      vencimiento --- las fechas permiten
                                      determinar su situación.

  Estado                              Pendiente
  -----------------------------------------------------------------------

## Historia de usuario

> Como Personal de seguros, quiero que los documentos sean clasificados
> automáticamente por estado, para identificar su situación actual
> durante el seguimiento.

## Dependencias

HU-003 Registrar documento --- debe existir el documento. HU-004
Registrar fechas de vigencia y vencimiento --- las fechas permiten
determinar su situación.

## Precondiciones

-   El documento debe estar registrado.
-   Las fechas necesarias para el seguimiento deben estar registradas.

## Reglas de negocio

### RN-01 --- Estados

Los estados definidos son Vigente, Próximo a vencer y Vencido.

### RN-02 --- Clasificación automática

El sistema clasifica automáticamente los documentos.

### RN-03 --- Historial de estados

El sistema conserva el historial de estados Vigente → Próximo a vencer →
Vencido.

## Descripción funcional

El sistema evalúa la información de vigencia y vencimiento y clasifica
el documento como Vigente, Próximo a vencer o Vencido. La clasificación
sirve para consultas, seguimiento y alertas. Los umbrales de próximo
vencimiento se detallan en HU-007.

## Criterios de aceptación

### CA-01 --- Clasificación

**Dado que** existe un documento con fechas registradas.

**Cuando** el sistema evalúa su situación.

**Entonces** asigna uno de los estados definidos.

### CA-02 --- Estado permitido

**Dado que** el sistema clasifica un documento.

**Cuando** determina su estado.

**Entonces** utiliza Vigente, Próximo a vencer o Vencido.

## Caso exitoso

Entrada: documento y fechas → Validación: datos disponibles →
Procesamiento: evaluación → Resultado: estado correspondiente.

## Casos de error

### Error 1

-   **Condición:** Información insuficiente
-   **Acción:** Intentar clasificar
-   **Resultado:** No asignar un estado sin sustento
-   **Datos que NO deben modificarse:** No modificar las fechas ni otros
    datos del documento.

## Integridad / no modificación

Un fallo de clasificación no debe alterar las fechas originales ni
producir cambios parciales.

## Gherkin / BDD

``` gherkin
Feature: Clasificación de documentos por estado

  Scenario: Clasificar documento
    Given existe un documento con fechas registradas
    When el sistema evalúa su situación
    Then asigna el estado correspondiente
```
