# Definición de Requisitos del Sistema
**Proyecto:** Editor de Procesos Standalone según ISO/IEC/IEEE 24774
**Procesos aplicados:** ISO/IEC/IEEE 15288 / 12207 (Cláusulas 6.4.3)
**Metodología de Desarrollo:** Cascada (Waterfall)

---

## 1. Introducción y Propósito del Proceso

El proceso 6.4.3 — System Requirements Definition — de la norma ISO/IEC/IEEE 12207 tiene como propósito transformar los requisitos del stakeholder en una descripción técnica, medible y formal del sistema (el editor standalone de procesos) que detalle sus interfaces, funciones y límites.

Este documento reúne el conjunto completo de entregables exigidos por dicho proceso para el proyecto "Editor de Procesos Standalone", constituyendo la línea base (baseline) de requisitos del sistema.

### Verificación de Salidas del Proceso (Outcomes Checklist - 6.4.3.2)
Como resultado de la ejecución de este proceso, se asegura y documenta el cumplimiento de las salidas exigidas por la norma:
- `[x]` **a)** La descripción del sistema, incluyendo interfaces, funciones y límites, está definida. *(Ref: Actividad a.1 y Requisitos Funcionales)*
- `[x]` **b)** Los requisitos del sistema (funcionales, rendimiento, proceso, no funcionales) y restricciones están definidos. *(Ref: Sección 2.1 y 2.2)*
- `[x]` **c)** Las medidas críticas de rendimiento (CPM) están definidas. *(Ref: Actividad c.2 mediante el RNF-03)*
- `[x]` **d)** Los requisitos del sistema han sido analizados. *(Ref: Actividad c.1)*
- `[x]` **e)** Los sistemas habilitadores/servicios para la definición de requisitos están disponibles. *(Ref: Actividad a.3)*
- `[x]` **f)** La trazabilidad desde los requisitos del sistema hacia los requerimientos de los stakeholders está desarrollada. *(Ref: Actividad d.2 - Matriz)*

---

Para dar cumplimiento formal a la norma, la transformación de las necesidades de los stakeholders a requisitos del sistema se ejecutó a través de las siguientes cuatro actividades (6.4.3.3):

### a) Preparación para la definición de requisitos del sistema
1.  **Límite funcional del sistema (Functional Boundary):** El sistema es una aplicación aislada (*standalone*). Sus límites (fronteras) están contenidos en el navegador del usuario. Sus entradas se limitan a archivos físicos locales `.pro` e interacción mediante teclado/ratón. Sus salidas son la alteración de la vista web, exportación a `.pro` y renderización de documentos PDF.
2.  **Estrategia de definición:** Al enmarcarse en un modelo de **Cascada**, la estrategia exige una elicitación y definición total de los requisitos de forma exhaustiva antes de avanzar al diseño. El documento de requisitos será objeto de un acuerdo de congelamiento (baseline).
3.  **Sistemas habilitadores:** Se requiere acceso a repositorios de código y a herramientas de modelado JSON Schema para validar los requisitos de las estructuras de datos antes del diseño.

### b) Definición de los requisitos del sistema
Esta actividad transforma operativamente los requisitos de los stakeholders en las características explícitas y medibles que el sistema debe poseer.

#### 2.1 Requisitos Funcionales (Funciones requeridas)
*   **RF-01** Crear una nueva descripción de proceso.
*   **RF-02** Registrar nombre, propósito y resultados esperados.
*   **RF-03** Crear, modificar y eliminar elementos del proceso.
*   **RF-04** Asociar actividades al proceso.
*   **RF-05** Asociar tareas a actividades.
*   **RF-06** Reorganizar actividades y tareas.
*   **RF-07** Guardar archivos `.pro` basados en JSON.
*   **RF-08** Cargar archivos `.pro` y reconstruir la estructura.
*   **RF-09** Impedir guardar procesos incompletos.
*   **RF-10** Generar vista previa del proceso.
*   **RF-11** Permitir impresión.
*   **RF-12** Exportar a PDF.
*   **RF-13** Seleccionar orientación vertical u horizontal.

#### 2.2 Requisitos No Funcionales (Restricciones y características de calidad)
*   **RNF-01** El sistema deberá ser usable sin conocimientos de JSON.
*   **RNF-02** Compatibilidad con Chrome, Edge y Firefox.
*   **RNF-03** Tiempo de respuesta menor a 2 segundos para operaciones de edición.
*   **RNF-04** Conservación íntegra de la información almacenada.
*   **RNF-05** Portabilidad de archivos `.pro` entre instalaciones.
*   **RNF-06** Facilidad de mantenimiento y ampliación.

### c) Análisis de los requisitos del sistema
1.  **Análisis de atributos de calidad:** El conjunto de requisitos funcionales y no funcionales fue revisado y categorizado de modo que no dicte la implementación profunda, sea factible, verificable (ej. prueba de compatibilidad de navegadores RNF-02) y singular.
2.  **Medidas críticas de rendimiento (Critical Performance Measures):** Se establece formalmente el **RNF-03** (Tiempo de respuesta < 2s) como una MOP (Measure of Performance) crítica que el proceso de Arquitectura debe garantizar en sus análisis de *trade-off*.
3.  **Resolución de conflictos y restricciones:** El conflicto inicial entre "no exigir conocimientos técnicos de JSON" (RNF-01) y "generar archivos .pro basados en JSON" (RF-07) queda resuelto dictaminando que la GUI debe fungir como una barrera de abstracción total.

### d) Gestión de los requisitos del sistema
1.  **Establecimiento de Acuerdos y Línea Base:** Este conjunto unificado de RFs y RNFs constituye la versión formal a firmar por los *Stakeholders* para crear el Baseline. 
2.  **Mantenimiento de Trazabilidad Bidireccional (Matriz de Trazabilidad de Requisitos):** A continuación, se detalla la matriz de trazabilidad bidireccional formal que mapea las necesidades de negocio, los requisitos de los stakeholders, los requisitos funcionales y no funcionales del sistema, y el método de verificación establecido para el aseguramiento de la calidad en el modelo de cascada:

| ID Req. Stakeholder | Necesidad Asociada | Descripción del Requisito Stakeholder | Requisitos del Sistema (RF/RNF) Asignados | Método de Verificación |
| :--- | :--- | :--- | :--- | :--- |
| **REQ-STK-01** | **N1** (Procesos multi-cliente) | Permitir crear una descripción de proceso asociando el nombre del cliente y el del proceso de acuerdo con la norma ISO/IEC/IEEE 24774. | RF-01, RF-02, RNF-04 | Inspección visual / Demostración interactiva en GUI |
| **REQ-STK-02** | **N2** (Cargue/Descargue) | Asegurar el uso de plantillas adecuadas para el cargue y descargue de datos estructurados. | RF-03, RF-04, RF-07 | Prueba unitaria del parser JSON Schema y demostración de carga |
| **REQ-STK-03** | **N5** (Ejecución por URL) | Permitir la ejecución y carga automática del editor a través de la URL (query params/hash). | RF-05, RNF-05 | Pruebas de integración del enrutador y carga automática del estado |
| **REQ-STK-04** | **N4** (Estricto con datos) | Validar de forma estricta los datos ingresados para evitar inconsistencias en el esquema del proceso. | RF-06, RNF-03 | Prueba funcional con payloads corruptos (caja negra) |
| **REQ-STK-05** | **N6** (Exportable PDF) | Exportar descripciones de procesos directamente en documentos PDF formalizados. | RF-08 | Inspección visual de la maquetación y tipografía del PDF |
| **REQ-STK-06** | **N3** (Disponibilidad 100%) | No requerir integraciones de sistemas externos (SoS) para garantizar 100% de disponibilidad. | RNF-01, RNF-02 | Simulación de desconexión de red / Pruebas offline |
