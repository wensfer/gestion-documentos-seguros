# HU-003 --- Registrar documento

## Identificación

  -----------------------------------------------------------------------
  Campo                               Valor
  ----------------------------------- -----------------------------------
  ID                                  HU-003

  Título                              Registrar documento

  Módulo                              Gestión documental

  Actor principal                     Personal de seguros

  Prioridad                           CRÍTICA

  Estimación                          Pendiente de refinamiento

  Dependencias                        HU-002 Registrar cliente --- el
                                      documento debe poder asociarse al
                                      cliente correspondiente.

  Estado                              Pendiente
  -----------------------------------------------------------------------

## Historia de usuario

> Como Personal de seguros, quiero registrar documentos con su tipo y
> categoría, para disponer de la información necesaria para su control y
> seguimiento.

## Dependencias

HU-002 Registrar cliente --- el documento debe poder asociarse al
cliente correspondiente.

## Precondiciones

-   El Personal de seguros debe tener acceso autorizado.
-   El cliente correspondiente debe estar registrado para realizar la
    asociación cuando corresponda.

## Reglas de negocio

### RN-01 --- Tipos de documento

Se contemplan pólizas, certificados relacionados con seguros, documentos
del cliente, documentos para renovación y otros configurables
relacionados con la póliza.

### RN-02 --- Estado inicial

Un documento registrado con la información y fechas requeridas recibe
estado inicial Vigente.

### RN-03 --- Consistencia

No debe existir duplicidad de documentos por tipo y fecha.

## Descripción funcional

El Personal de seguros registra un documento indicando el tipo o
categoría correspondiente. El PRD exige campos obligatorios y contempla
fechas de vigencia y vencimiento para completar el seguimiento. Otros
campos específicos quedan como **Pendiente de definición**. Al completar
correctamente el registro, el documento queda disponible para
clasificación y seguimiento.

## Criterios de aceptación

### CA-01 --- Registro exitoso

**Dado que** el Personal de seguros tiene permisos.

**Cuando** registra un documento con tipo y datos requeridos.

**Entonces** el sistema almacena el documento y lo deja disponible para
seguimiento.

### CA-02 --- Tipo válido

**Dado que** se registra un documento.

**Cuando** se selecciona su tipo.

**Entonces** el tipo corresponde a una categoría contemplada por el
sistema.

### CA-03 --- Datos incompletos

**Dado que** se intenta registrar un documento.

**Cuando** faltan campos obligatorios.

**Entonces** el sistema no completa el registro.

## Caso exitoso

Entrada: tipo/categoría y datos requeridos → Validación: campos
obligatorios y consistencia → Procesamiento: registro → Resultado:
documento disponible para seguimiento.

## Casos de error

### Error 1

-   **Condición:** Campos obligatorios incompletos
-   **Acción:** Intentar guardar
-   **Resultado:** Rechazar el registro
-   **Datos que NO deben modificarse:** No registrar parcialmente el
    documento.

### Error 2

-   **Condición:** Duplicidad por tipo y fecha
-   **Acción:** Intentar registrar el documento duplicado
-   **Resultado:** Rechazar el registro inconsistente
-   **Datos que NO deben modificarse:** No modificar documentos
    existentes.

## Integridad / no modificación

Ante un fallo no debe crearse un documento parcial ni modificarse un
documento previamente registrado.

## Gherkin / BDD

``` gherkin
Feature: Registro de documentos

  Scenario: Registrar documento correctamente
    Given el Personal de seguros tiene permisos
    When registra un documento con tipo y datos requeridos
    Then el sistema almacena el documento
    And lo deja disponible para seguimiento
```
