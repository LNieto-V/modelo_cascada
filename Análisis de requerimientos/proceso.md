# Proceso de Definición de Requisitos (ISO/IEC/IEEE 12207 Cláusulas 6.4.2 y 6.4.3)
**Fase Metodológica:** Análisis de Requerimientos (Requirements Analysis) - Modelo de Cascada Pura

---

## 1. Propósito del Proceso
El propósito de esta fase es doble de acuerdo con el estándar ISO/IEC/IEEE 12207:
1. **Definición de Necesidades y Requerimientos de los Stakeholders (Cláusula 6.4.2):** Definir los requisitos para un sistema que satisfaga las necesidades expresadas por los stakeholders de la empresa consultora.
2. **Definición de Requisitos del Sistema (Cláusula 6.4.3):** Transformar los requisitos de los stakeholders en una descripción técnica, medible y formal del sistema (el editor standalone de procesos) que detalle sus interfaces, funciones y límites.

Bajo la metodología de **Cascada Pura**, este proceso se ejecuta al inicio del ciclo de vida y debe completarse y congelarse formalmente (Línea Base / Baseline) antes de iniciar la fase de Diseño Arquitectónico (6.4.4).

---

## 2. Entradas del Proceso (Inputs)
*   **Solicitudes de la Empresa (Consultora):** Necesidad de levantar procesos de forma concurrente para múltiples clientes.
*   **Marco Normativo de Referencia:** Estándar ISO/IEC/IEEE 24774 (Directrices para la descripción de procesos).
*   **Restricciones de Infraestructura:** Necesidad de que sea una aplicación standalone, independiente de integraciones de red obligatorias para garantizar 100% de disponibilidad.
*   **Estándares de Calidad y Ciclo de Vida:** ISO/IEC/IEEE 12207:2026.

---

## 3. Roles y Responsabilidades
*   **Analista de Procesos / Auditor:** Identifica las necesidades y asegura el cumplimiento con la norma ISO 24774.
*   **Diseñador de Procesos:** Stakeholder principal que define la interacción requerida con la interfaz del editor.
*   **Líder de Proyecto / Consultor:** Coordina la definición del alcance y la aprobación de la línea base con los clientes finales.
*   **Ingeniero de Requisitos:** Documenta y mantiene la trazabilidad bidireccional de los requisitos.

---

## 4. Actividades y Tareas del Proceso
De acuerdo con las directrices de la norma, se ejecutaron las siguientes actividades:

### Actividad 6.4.2.3: Definición de Necesidades y Requerimientos de Stakeholders
*   **Identificación de Stakeholders:** Registro y mapeo de los intereses del negocio, diseñadores de procesos, auditores, desarrolladores y clientes finales (Sección 1.1).
*   **Definición del Contexto Operacional:** Establecimiento de los límites operativos (interfaz web, soporte de archivos `.pro` y PDF, abstracción de JSON para el usuario final).
*   **Identificación y Elicitación de Necesidades:** Captura de necesidades clave (N1 a N8) enfocadas en usabilidad, almacenamiento, estructuración e impresión.
*   **Definición de Requerimientos de Stakeholders:** Redacción formal de los requerimientos de usuario (REQ-STK-01 a REQ-STK-10).

### Actividad 6.4.3.3: Definición de Requisitos del Sistema
*   **Preparación de la Definición:**
    *   Definición del límite funcional del sistema (*Functional Boundary*).
    *   Establecimiento de la estrategia de congelamiento de requerimientos (*Waterfall Baseline*).
    *   Identificación de habilitadores (herramientas de validación de JSON Schema).
*   **Definición de Requisitos del Sistema:**
    *   **Requisitos Funcionales (RF-01 a RF-13):** Operaciones del editor, manejo de archivos `.pro`, lógica de actividades y tareas, exportación e impresión.
    *   **Requisitos No Funcionales (RNF-01 a RNF-06):** Usabilidad, compatibilidad de navegadores, rendimiento crítico (< 2s), persistencia, portabilidad y mantenibilidad.
*   **Análisis de Requisitos:**
    *   Establecimiento del RNF-03 como Medida Crítica de Rendimiento (MOP).
    *   Resolución de conflictos entre requerimientos técnicos y de negocio (ocultamiento del JSON mediante una interfaz visual intuitiva).
*   **Gestión de Requisitos:**
    *   Creación de la Matriz de Trazabilidad Bidireccional (Sección 2.2-d.2).
    *   Aprobación formal del documento como Línea Base (Baseline) de Requerimientos.

---

## 5. Salidas del Proceso (Outputs)
*   **Entregables del Proceso de Definición de Requisitos y Necesidades de los Interesados (StRS 6.4.2):** Documentados en `outcomes/resultado1.md`.
*   **Especificación de Requisitos del Sistema (SyRS 6.4.3):** Documentada en `outcomes/resultado2.md`.
*   **Matriz de Trazabilidad de Requisitos:** Enlaza las necesidades de negocio con los requerimientos técnicos en ambos entregables.
*   **Lista de Verificación de Salidas (Outcomes Checklist 6.4.2.2 y 6.4.3.2):** Completas y aprobadas al 100%.

---

## 6. Criterio de Cierre y Congelamiento (Exit Criteria)
Esta fase se da por concluida una vez que:
1.  Los documentos `outcomes/resultado1.md` y `outcomes/resultado2.md` son revisados y firmados por los stakeholders correspondientes (Analista, Diseñador y Responsable de Proyecto).
2.  Las matrices de trazabilidad demuestran cobertura total de las necesidades del stakeholder y de los requisitos del sistema.
3.  Se establece formalmente el congelamiento de esta línea base (Baseline v1.0). A partir de este momento, cualquier modificación de requisitos debe canalizarse mediante el proceso de control de cambios. Se autoriza el paso a la fase de **Diseño Arquitectónico (6.4.4)**.
