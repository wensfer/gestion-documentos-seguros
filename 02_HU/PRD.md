# PRD - Gestión y seguimiento de documentos en empresas aseguradoras

**Versión:** v0.3 - Primera generación
**Estado:** REQUERIE REVISIÓN
**Fecha:** 2026-09-06

---
## 1. INTRODUCCIÓN

### 1.1 Propósito
Documento de especificaciones de requisitos para el sistema de gestión y seguimiento de documentos empresariales aseguradoras. Este sistema centraliza la gestión, control y seguimiento de documentos y sus fechas de vigencia dentro de empresas aseguradoras.

### 1.2 Alcance
**Cubre:**
- Registro y gestión de usuarios (administrador, personal de seguros, responsable/supervisor)
- Registro y control de documentos: pólizas, certificados seguros, documentos del cliente, documentos para renovación y otros configurables relacionados con la póliza
- Control de fechas de vigencia y vencimiento con estados: Vigente (30/15/7 días antes), Próximo a vencer, Vencido
- Generación de alertas de vencimiento (30, 15 y 7 días antes)
- Consultas y reportes de historial y estado de documentos

**No cubre:**
- Integraciones con sistemas externos (versión inicial v0.4)
- Funcionalidades de procesamiento documental completo
- Módulos de pago o cobranza de seguros
- Acceso directo por parte de clientes (sus datos son gestionados por personal autorizado)

### 1.3 Audiencia y uso del documento
- **Estudiantes:** Definición y validación de requisitos
- **Usuarios finales:** Personal de seguros, administrativos, ejecutivos
- **Desarrolladores:** Guía de implementación
- **Analistas:** Validación de casos de uso
- **Testers:** Base para diseños de pruebas
- **Responsables del proyecto:** Seguimiento de alcance y viabilidad

### 1.4 Referencias
- Documentos proporcionados por el estudiante (Levantamiento inicial)
- ISO/IEC/IEEE 29148 - Requirements engineering
- ISO/IEC 25010 - Quality requirements

### 1.5 Definiciones, acrónimos y abreviaturas
- **ADM:** Administrador - Gestiona la información general y los usuarios
- **SEG:** Personal de seguros - Registra y realiza seguimiento de documentos
- **SUPER:** Responsable o supervisor - Consulta el estado de los documentos
- **CLI:** Cliente - Persona o empresa a la que pertenecen los documentos y seguros

### 1.6 Descripción general del documento
El documento está organizado por secciones funcionales y no funcionales, con matriz de trazabilidad y riesgos identificados.

---
## 2. DESCRIPCIÓN GENERAL

### 2.1 Perspectiva del sistema/producto
Sistema independiente que centraliza la gestión documental para empresas aseguradoras. No reemplaza ni complementa otro sistema existente (no definidos actualmente).

### 2.2 Funciones principales
- Centralizar la gestión y seguimiento de documentos relacionados con seguros
- Control de fechas de vigencia y vencimiento de documentos
- Generación de alertas automáticas de vencimiento
- Clasificación y consulta de documentos por estado
- Registro histórico de renovaciones y estados

### 2.3 Características de los usuarios

| Rol | Responsabilidad | Nivel de conocimiento | Interacción con el sistema |
|-----|----------------|----------------------|---------------------------|
| Administrador | Gestiona la información general y los usuarios | Medio-Alto | Acceso completo, creación y aprobación |
| Personal de seguros | Registra y realiza seguimiento de documentos | Medio | Registro, consulta, actualización de estados |
| Responsable/supervisor | Consulta el estado de los documentos y realiza seguimiento | Medio | Consultas, reportes, supervisión |
| Cliente | Persona o empresa a la que pertenecen los documentos y seguros | - | No utilizará el sistema directamente; sus datos y documentos serán gestionados por personal autorizado |

### 2.4 Restricciones, supuestos y dependencias

#### Restricciones
- **Tiempo de desarrollo:** Limitado al periodo académico
- **Plataforma:** Web
- **Backend:** PHP con Laravel
- **Base de datos:** MySQL
- **Servidor:** Apache
- **Frontend:** HTML, CSS, JavaScript y Bootstrap
- **Presupuesto:** Limitado al desarrollo académico
- **Infraestructura:** Recursos disponibles para el proyecto
- **Personal:** Estudiante responsable del desarrollo
- **Institucional:** Cumplir con los requerimientos establecidos para la materia
- **Legal:** Privacidad y protección de la información de clientes
- **Seguridad:** Acceso restringido según el tipo de usuario (solo personal autorizado)
- **Sistemas existentes:** No definidos (no habrá integraciones externas en v0.4)

#### Supuestos
- El sistema será utilizado dentro del periodo académico definido
- La información de clientes requiere niveles de acceso diferenciados (gestión por personal autorizado)
- No existirán integraciones externas ni APIs en la primera versión (v0.4)
- Los datos de vigencia/vencimiento serán proporcionados por los usuarios del sistema
- El cliente no utilizará el sistema directamente; sus datos y documentos serán gestionados por personal autorizado

#### Dependencias
- Disponibilidad del estudiante desarrollador
- Definición de tecnologías antes del inicio de implementación
- Cooperación de los usuarios en el registro inicial de datos

### 2.5 Entorno operativo
- **Hardware:** Por definir
- **Sistema operativo:** Por definir
- **Red:** Por definir
- **Plataforma:** Por definir
- **Servidor:** Por definir
- **Infraestructura:** Recursos disponibles para el proyecto

---
## 3. REQUERIMIENTOS FUNCIONALES

Formato: **FR-XXX** - Descripción clara y verificable del comportamiento

| ID | Requisito | Actor | Prioridad | Estado |
|----|-----------|-------|-----------|--------|
| FR-001 | El sistema deberá permitir el registro de usuarios con rol definido | Administrador | CRÍTICA | DEFINIDO |
| FR-002 | El sistema deberá permitir el registro de clientes asociados a documentos | Administrador | CRÍTICA | DEFINIDO |
| FR-003 | El sistema deberá permitir el registro de documentos con tipos y categorías (pólizas, certificados, documentos cliente, renovación, configurables) | Personal de seguros | CRÍTICA | DEFINIDO |
| FR-004 | El sistema deberá registrar fechas de vigencia y vencimiento por documento | Personal de seguros | CRÍTICA | DEFINIDO |
| FR-005 | El sistema deberá Consultar documentos con filtros por tipo, estado, fecha | Personal de seguros, Responsable | ALTA | DEFINIDO |
| FR-006 | El sistema deberá Clasificar documentos por estado (vigente, próximo a vencer, vencido) | Sistema | CRÍTICA | DEFINIDO |
| FR-007 | El sistema deberá Identificar documentos próximos a vencer umbrales 30, 15 y 7 días antes del vencimiento y cambiar estado a "Vencido" después de la fecha | Sistema | CRÍTICA | DEFINIDO |
| FR-008 | El sistema deberá Generar alertas de vencimiento a usuarios correspondientes (30, 15 y 7 días antes) | Sistema | CRÍTICA | DEFINIDO |
| FR-009 | El sistema deberá Actualizar renovaciones y modificar fechas de vigencia | Personal de seguros | ALTA | DEFINIDO |
| FR-010 | El sistema deberá Consultar historial completo de documentos y estados | Personal de seguros, Responsable | ALTA | DEFINIDO |
| FR-011 | El sistema deberá Generar reportes de estado de documentos y vencimientos | Responsable, Administrador | BAJA | DEFINIDO |
| FR-012 | El sistema deberá Controlar acceso basado en tipo de usuario (solo personal autorizado) | Sistema | CRÍTICA | DEFINIDO |

---
## 4. REQUERIMIENTOS NO FUNCIONALES

Formato: **NFR-XXX** - Categorías con métricas verificables cuando sea posible

| ID | Requisito | Categoría | Nivel | Observaciones |
|----|-----------|-----------|-------|---------------|
| NFR-002 | El sistema deberá implementar control de acceso por rol de usuario | Security | CRÍTICA | Acceso restringido según tipo de usuario (personal autorizado) |
| NFR-004 | El sistema deberá cumplir con normas de privacidad y protección de datos | Legal/Regulatory | CRÍTICA | Privacidad información clientes |
| NFR-005 | La interfaz deverá ser accesible para usuarios con conocimientos básicos de tecnología | Usability | IMPORTANTE | Sin diseño visual definido, usará Bootstrap |
| NFR-006 | Los datos de vigencia y vencimiento deverán ser consistentes y sin duplicidades | Data Integrity | CRÍTICA | Validación en registro |
| NFR-007 | El sistema deberá funcionar en la plataforma y navegadores disponibles en el entorno académico | Compatibility | OPCIONAL | Web platform con Bootstrap |

---
## 5. REQUERIMIENTOS DE INTERFACES EXTERNAS

### 5.1 Interfaces de usuario
- **Tipo:** Web
- **Usuarios:** Administrador, Personal de seguros, Responsable/supervisor
- **Navegación:** Menús principales, listados, formularios de registro y consulta
- **Consideraciones de accesibilidad:** Nivel básico (usará Bootstrap)
- **Restricciones conocidas:** Acceso diferenciado por tipo de usuario (solo personal autorizado)

### 5.2 Interfaces de hardware
No aplica - Sistema web a definir.

### 5.3 Interfaces de software
- **APIs:** No definida inicialmente (no habrá integraciones externas en v0.4)
- **Sistemas:** No definidos (sistema independiente)
- **Servicios:** No definidos
- **Protocolos:** No definidos (comunicación interna solo)
- **Formatos de intercambio:** No definidos (sin integraciones externas)

### 5.4 Interfaces de comunicación
- **HTTP/HTTPS:** No aplicable (sistema web interno, sin comunicaciones externas en v0.4)
- **TCP/IP:** No aplicable (mismo servidor/red interna)
- **Seguridad de comunicaciones:** Control de acceso por rol (solo personal autorizado)
- **Restricciones de red:** Entorno académico, infraestructura disponible (sin externas)

---
## 6. OTROS REQUERIMIENTOS

### 6.1 Requisitos legales y regulatorios
- Considerar privacidad y protección de información de clientes (establecido en restricciones)
- Cumplir con normativa aplicable a manejo de datos en entorno académico
- **Estado:** Definido conforme restricciones legales de privacidad

### 6.2 Instalación, despliegue y distribución
- Despliegue en entorno académico/institucional
- Arquitectura: Backend PHP/Laravel + Frontend Bootstrap, Apache/MySQL
- Instalación sobre recursos disponibles (servidor Apache)
- Distribución limitada a usuarios del proyecto (personal autorizado)

### 6.3 Internacionalización y localización
No aplica - Entorno académico nacional (español).

### 6.4 Requisitos de datos
- **Datos manejados:** Usuarios, Clientes, Documentos (pólizas, certificados seguros, documentos cliente, renovación, otros configurables relacionados con la póliza), Tipos de documentos, Fechas de vigencia, Fechas de vencimiento, Estados (Vigente/Próximo a vencer/Vencido), Renovaciones, Alertas (30/15/7 días), Historial, Reportes
- **Retención:** Durante el periodo académico y ciclo de vida del documento
- **Integridad:** Validación de fechas (umbrales 30/15/7 días) y campos obligatorios en registro
- **Consistencia:** Sin duplicidad de documentos por tipo y fecha
- **Archivado:** Historial de estados (Vigente → Próximo a vencer → Vencido) y renovaciones
- **Eliminación:** Por definir (según política académica, considerando datos vencidos)

---
## 7. VERIFICACIÓN Y VALIDACIÓN

### 7.1 Métodos de verificación
| Requisito | Inspección | Prueba | Demostración | Análisis |
|-----------|------------|--------|--------------|----------|
| FR-001 a FR-012 | ✓ | ✓ | Por definir | ✓ |
| NFR-002, NFR-004, NFR-005, NFR-006, NFR-007 | ✓ | Por definición | Por definir | ✓ |

### 7.2 Criterios de aceptación
Formato preferente: **DADO QUE... CUANDO... ENTONCES...**

- **FR-003:** DADO QUE un usuario tiene permisos de personal de seguros, CUANDO registra un nuevo documento con tipo (póliza, certificado, cliente, renovación, configurable) y fechas de vigencia/vencimiento, ENTONCES el sistema debe almacenar el documento con los campos completos y asignar estado inicial "Vigente".

- **FR-007:** DADO QUE el sistema tiene documentos registrados, CUANDO una fecha de vencimiento está a 30, 15 o 7 días del fecha actual, ENTONCES el sistema debe generar una alerta visible para el usuario correspondiente y mantener estado "Próximo a vencer"; ENTONCES después de la fecha de vencimiento, el sistema debe cambiar el estado a "Vencido".

- **FR-002:** DADO QUE el administrador accede al módulo de registro, CUANDO ingresa los datos del cliente y guarda, ENTONCES el cliente debe estar disponible en las búsquedas y reportes posteriores, pero sin acceso directo al sistema.

- **FR-008:** DADO QUE el sistema identifica un umbral de alerta (30, 15 o 7 días), CUANDO la fecha está dentro de ese rango, ENTONCES debe generar la alerta correspondiente al personal de seguros asignado.

---
## 8. ÁPENDICES

### A. Glosario
- **ADM:** Administrador - Gestiona la información general y los usuarios
- **SEG:** Personal de seguros - Registra y realiza seguimiento de documentos
- **SUPER:** Responsable/supervisor - Consulta el estado y sigue documentos
- **CLI:** Cliente - Empresa o persona dueña de documentos y seguros (no usa el sistema directamente)
- **VIG:** Fecha de vigencia - Período durante cual el documento es válido
- **VEN:** Fecha de vencimiento - Fecha límite después de cual el documento está caducado
- **ESTADO:** Clasificación actual del documento (Vigente/Próximo a vencer/Vencido)
- **ALERT-30:** Alertado a los 30 días antes del vencimiento
- **ALERT-15:** Alertado a los 15 días antes del vencimiento
- **ALERT-7:** Alertado a los 7 días antes del vencimiento
- **CRÍTICA:** Prioridad crítica - Requisito obligatorio para funcionalidad mínima
- **ALTA:** Prioridad alta - Requisito importante para MVP
- **MEDIA:** Prioridad media - Requisito deseable para siguientes versiones
- **BAJA:** Prioridad baja - Requisito opcional para futuras mejoras

### B. Casos de uso y escenarios
1. **Registro de documento:** Personal de seguros registra un nuevo documento con tipo (póliza, certificado, cliente, renovación, configurable) con fechas de vigencia y vencimiento; sistema asigna estado inicial "Vigente" y clasifica automáticamente.

2. **Consulta de documentos:** Usuario filtra documentos por tipo, estado (Vigente/Próximo a vencer/Vencido) o rango de fechas; sistema muestra lista con información resumida. El cliente no accede directamente; las consultas son realizadas por personal autorizado.

3. **Generación de alertas:** Sistema identifica documentos con vencimiento en 30, 15 o 7 días y envía notificación a usuarios correspondientes (personal de seguros, responsable). Después de la fecha de vencimiento, el estado cambia automáticamente a "Vencido".

4. **Actualización de renovación:** Personal actualiza fechas de vigencia y renovación; sistema refleja cambio de estado (puede volver a "Vigente" si aplica) y actualiza historial.

5. **Control de acceso:** El sistema bloquea acceso directo por parte de clientes; todas las operaciones deben ser realizadas por personal autorizado con roles definidos (ADM, SEG, SUPER).

### C. Matriz de trazabilidad

| ID Problema | Objetivo | Funcionalidad | Requisito | Criterio de aceptación | Verificación |
|-------------|----------|---------------|-----------|------------------------|--------------|
| Control documentation | Mejorar seguimiento fechas vigencia | Registrar documentos | FR-003 | Documento registrado con tipo (póliza, certificado, cliente, renovación, configurable), fechas y estado inicial "Vigente" asignado | Prueba de inserción y consulta |
| Control documentation | Mejorar seguimiento fechas vigencia | Control fechas vencimiento | FR-004 | Fechas de vigencia y vencimiento registradas correctamente con validación de campos obligatorios | Inspección de datos |
| Control documentation | Mejorar seguimiento fechas vigencia | Identificar docs próximos a vencer | FR-007 | Sistema identifica docs con vencimiento en 30, 15 o 7 días; genera alerta y cambia estado a "Próximo a vencer"; después de la fecha, estado "Vencido" | Prueba con fechas ejemplo (30/15/7 días) |
| Control documentation | Mejorar seguimiento fechas vigencia | Generar alertas vencimiento | FR-008 | Alertas generadas y visibles para usuarios (personal autorizado) a los 30, 15 y 7 días antes del vencimiento | Demostración en entorno |
| Control documentation | Mejorar seguimiento fechas vigencia | Control acceso por rol | FR-012 | Solo usuarios autorizados (ADM, SEG, SUPER) acceden a funcionalidades; acceso bloqueado para CLI | Prueba de permisos |

**Trazabilidad completa:** Problema → Objetivo → Funcionalidad → Requisito → Criterio → Verificación

### D. Diagramas y material de apoyo
- Diagrama de flujo: Registro → Clasificación → Alertas → Consulta → Reportes
- Matriz de trazas (ver Apéndice C)

---
## 9. ÍNDICE
(Documento generado en fase inicial, índice incluirse en versión final según tamaño)

---
## 10. OBSERVACIONES Y PRÓXIMOS PASOS

### Información pendiente de definición
Los items marcados como "Por definir" a continuación son aspectos infraestructurales o de política que no impiden el inicio del desarrollo, ya que las decisiones críticas de tecnología, arquitectura y requerimientos funcionales ya están definidos:

- **Hardware/SO/Red/Plataforma/Servidor:** Definibles una vez seleccionado el entorno de despliegue académico (pueden permanecer como recursos disponibles).
- **Política de eliminación de datos:** Definible según normativas académicas y de conservación de documentos vencidos (no bloquea desarrollo funcional).
- **Métodos de verificación específicos:** Pueden refinarse durante la fase de implementación y pruebas.

**No existe información crítica pendiente** que requiera definición antes de iniciar la etapa de desarrollo. Todas las decisiones críticas sobre tecnología (PHP/Laravel, MySQL, Apache, Bootstrap), umbrales de alerta (30/15/7 días), prioridades (Crítica/Alta/Media/Baja), roles de acceso y tipos de documento ya están confirmados.

### Supuestos establecidos
- Desarrollo dentro del periodo académico establecido con pila tecnológica definida
- No habrá integraciones externas ni APIs en la versión inicial v0.4 (sistema independiente)
- Acceso restringido por tipo de usuario (solo personal autorizado: ADM, SEG, SUPER)
- El cliente no utilizará el sistema directamente; sus datos y documentos serán gestionados por personal autorizado
- Umbrales de alerta definidos: 30, 15 y 7 días antes del vencimiento; estado "Vencido" después de la fecha
- Prioridades definidas: Crítica, Alta, Media y Baja según clasificación de requisitos
- Plataforma: Web, con acceso controlado según rol

### Recomendaciones
1. Definir configuración de hardware/servidor al comenzar el despliegue en entorno académico
2. Establecer política de conservación y eliminación de datos vencidos conforme normativas institucionales
3. Durante la implementación, definir métodos de verificación más específicos para cada requisito
4. Mantener control de prioridades por clasificación CRÍTICA/ALTA/MEDIA/BAJA
5. Probar escenarios de alerta con los umbrales exactos (30, 15, 7 días antes)

### Riesgos identificados
| ID | Riesgo | Probabilidad | Impacto | Mitigación |
|----|--------|--------------|---------|------------|
| R-01 | Contraste en definiciones de roles (ADM/SEG/SUPER vs CLI) | Baja | Alta | Validación confirmada con estudiante; acceso bloqueado por diseño |
| R-02 | Pérdida de datos por eliminación prematura | Media | Alta | Políticas definidas antes de funcionalidad de eliminación |
| R-03 | Conflictos en umbrales de alerta (30/15/7 días) | Baja | Media | Definición confirmada; pruebas con escenarios límite |
| R-04 | Subestimar complejidad de clasificación de estados | Media | Media | Diseño sencillo: Vigente → Próximo a vencer → Vencido |

---
## 11. MATRIZ DE TRABABILIDAD COMPLETA

| Requirement ID | Type | Description | Priority | Status | Traces To Problem |
|----------------|------|-------------|----------|--------|-------------------|
| FR-001 | Functional | Registro de usuarios con rol definido | CRÍTICA | Definido | Control documentation |
| FR-002 | Functional | Registro de clientes asociados a documentos | CRÍTICA | Definido | Control documentation |
| FR-003 | Functional | Registro de documentos con tipos y categorías (pólizas, certificados, cliente, renovación, configurables) | CRÍTICA | Definido | Control documentation |
| FR-004 | Functional | Registrar fechas de vigencia y vencimiento por documento | CRÍTICA | Definido | Control documentation |
| FR-005 | Functional | Consultar documentos con filtros por tipo, estado, fecha | ALTA | Definido | Control documentation |
| FR-006 | Functional | Clasificar documentos por estado (Vigente/Próximo a vencer/Vencido) | CRÍTICA | Definido | Control documentation |
| FR-007 | Functional | Identificar documentos próximos a vencer umbrales 30, 15 y 7 días antes del vencimiento y cambiar estado a "Vencido" después | CRÍTICA | Definido | Control documentation |
| FR-008 | Functional | Generar alertas de vencimiento a usuarios correspondientes (30, 15 y 7 días antes) | CRÍTICA | Definido | Control documentation |
| FR-009 | Functional | Actualizar renovaciones y modificar fechas de vigencia | ALTA | Definido | Control documentation |
| FR-010 | Functional | Consultar historial completo de documentos y estados | ALTA | Definido | Control documentation |
| FR-011 | Functional | Generar reportes de estado de documentos y vencimientos | BAJA | Definido | Control documentation |
| FR-012 | Functional | Controlar acceso basado en tipo de usuario (solo personal autorizado, bloqueo CLI) | CRÍTICA | Definido | Control documentation |
| NFR-002 | Non-functional | Control de acceso por rol de usuario (solo personal autorizado) | CRÍTICA | Definido | - |
| NFR-004 | Non-functional | Cumplimiento privacidad y protección datos | CRÍTICA | Definido | - |
| NFR-005 | Non-functional | Interfaz accesible para usuarios con conocimientos básicos (usando Bootstrap) | IMPORTANTE | Definido | - |
| NFR-006 | Non-functional | Datos de vigencia/vencimiento consistentes y sin duplicidades | CRÍTICA | Definido | - |
| NFR-007 | Non-functional | Compatibilidad con plataforma Web y navegadores disponibles (Bootstrap) | OPCIONAL | Definido | - |
---

**SRS/PRD v0.4 - ESTADO: LISTO PARA DESARROLLO**

**Versión:** v0.4 - Definiciones confirmadas
**Fecha:** 2026-09-06
**Estado:** LISTO PARA DESARROLLO (sin información crítica pendiente)

**Definiciones confirmadas:**
- Tecnología completa: PHP con Laravel (Backend), MySQL (Base de datos), Apache (Servidor), HTML/CSS/JavaScript/Bootstrap (Frontend)
- Plataforma: Web
- Alertas: 30, 15 y 7 días antes del vencimiento; después del vencimiento, estado "Vencido"
- No habrá integraciones externas ni APIs en la primera versión
- Documentos: pólizas, certificados relacionados con seguros, documentos del cliente, documentos para renovación y otros documentos configurables relacionados con la póliza
- Prioridades: Crítica, Alta, Media y Baja
- Cliente NO utilizará el sistema; sus datos y documentos serán gestionados por personal autorizado

**Alcance v0.4:**
- Registro y gestión de usuarios (ADM, SEG, SUPER)
- Registro y control de documentos con tipos configurables
- Control de fechas de vigencia y vencimiento con estados automáticos
- Generación de alertas en umbrales 30/15/7 días
- Control de acceso basado en rol (solo personal autorizado)
- Consultas y reportes para personal autorizado

**Generado a partir de LEVANTAMIENTO INICIAL DE INFORMACIÓN**
**Validado con definiciones confirmadas: LISTO PARA ETAPA DE DESARROLLO**
**No existen vacíos críticos que requieran definición antes de iniciar desarrollo**