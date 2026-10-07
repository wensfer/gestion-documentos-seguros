# HU-005 --- Consultar documentos

## Identificación

  -----------------------------------------------------------------------
  Campo                               Valor
  ----------------------------------- -----------------------------------
  ID                                  HU-005

  Título                              Consultar documentos

  Módulo                              Gestión documental

  Actor principal                     Personal de seguros /
                                      Responsable-Supervisor

  Prioridad                           ALTA

  Estimación                          Pendiente de refinamiento

  Dependencias                        HU-003 Registrar documento ---
                                      deben existir documentos para
                                      consultar. HU-006 Clasificar
                                      documentos por estado --- necesaria
                                      para consultar por estado.

  Estado                              Pendiente
  -----------------------------------------------------------------------

## Historia de usuario

> Como Personal de seguros o Responsable/Supervisor, quiero consultar
> documentos mediante filtros por tipo, estado o fecha, para localizar
> la información necesaria para su seguimiento.

## Dependencias

HU-003 Registrar documento --- deben existir documentos para consultar.
HU-006 Clasificar documentos por estado --- necesaria para consultar por
estado.

## Precondiciones

-   El usuario debe estar autorizado.
-   Deben existir documentos registrados para obtener resultados.

## Reglas de negocio

### RN-01 --- Filtros disponibles

La consulta permite filtrar por tipo, estado o fecha.

### RN-02 --- Estados consultables

Los estados contemplados son Vigente, Próximo a vencer y Vencido.

### RN-03 --- Cliente sin acceso

El cliente no accede directamente a las consultas.

## Descripción funcional

El usuario autorizado consulta los documentos y aplica filtros por tipo,
estado o fecha. El sistema presenta una lista con información resumida
de los documentos coincidentes. El detalle exacto de la información
resumida queda como **Pendiente de definición**.

## Criterios de aceptación

### CA-01 --- Consulta por filtro

**Dado que** existen documentos registrados.

**Cuando** el usuario autorizado aplica un filtro por tipo, estado o
fecha.

**Entonces** el sistema muestra los documentos coincidentes.

### CA-02 --- Acceso restringido

**Dado que** el cliente no es usuario directo.

**Cuando** se intenta acceder a la consulta como cliente.

**Entonces** el sistema bloquea el acceso.

## Caso exitoso

Entrada: filtro de consulta → Validación: usuario autorizado y criterio
→ Procesamiento: búsqueda → Resultado: lista de documentos coincidentes.

## Casos de error

### Error 1

-   **Condición:** Sin coincidencias
-   **Acción:** Ejecutar la consulta
-   **Resultado:** No presentar registros ajenos al criterio
-   **Datos que NO deben modificarse:** No modificar ningún documento.

### Error 2

-   **Condición:** Acceso no autorizado
-   **Acción:** Intentar consultar
-   **Resultado:** Bloquear el acceso
-   **Datos que NO deben modificarse:** No modificar información.

## Integridad / no modificación

La consulta es de lectura y no debe modificar documentos, fechas,
estados ni historial.

## Gherkin / BDD

``` gherkin
Feature: Consulta de documentos

  Scenario: Consultar documentos por filtro
    Given existen documentos registrados
    And el usuario está autorizado
    When filtra por tipo, estado o fecha
    Then el sistema muestra los documentos coincidentes
```
