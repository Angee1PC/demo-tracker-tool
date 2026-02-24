## Versión 2.15 (Estatus Dinámicos en Follow-up)
**Fecha:** 23 de Febrero de 2026

### Resumen
Se ha corregido la visualización de los estatus en la pestaña de Follow-up. Ahora, cada tarjeta muestra el estatus específico seleccionado (ej. "Submitted", "In Progress") en lugar de una etiqueta genérica.

### Detalles Técnicos
- **Archivo Principal:** `Demo Tracker Tool v2.15.html`
- **Mejoras Realizadas:**
    - Modificación de `saveRecord` para preservar y actualizar el `loanStatus` (estatus específico).
    - Corrección en `editRecord` para que al editar un registro se muestre su estatus real y no el nombre de la pestaña ("follow-up").
    - Corrección de typo en el listado de estatus ("Submited" -> "Submitted").
    - Actualización de `renderRecords` y `renderFollowUpList` para renderizar el estatus real del registro con retrocompatibilidad.
    - Incremento de versión interna a v2.15.

### Comando de Ejecución
```powershell
explorer.exe "d:\Python Projects\Demo Tracker Tool\Demo Tracker Tool V2.15.html"
```
---

## Versión 2.14 (Mejora Pegado Inteligente)
**Fecha:** 23 de Febrero de 2026

### Resumen
Se ha mejorado significativamente la funcionalidad de "Pegado Inteligente" para capturar una mayor cantidad de campos directamente desde la plantilla de Salesforce.

### Detalles Técnicos
- **Archivo Principal:** `Demo Tracker Tool V2.14.html`
- **Nuevos Campos Capturados:**
    - `Loan Number` (Soporte para patrones `LP-XXXXXXXXXX`)
    - `Loan Status`
    - `Program`
    - `Program Region`
    - `Loan Owner`
    - `Loan Requestor`
    - `Ship-To Company Name` (como Cliente)
    - `SFDC Opportunity`
    - `Total ESC` (Limpieza automática de "USD")
    - `Installation`
    - `Loan Status Date`

### Comando de Ejecución
```powershell
explorer.exe "d:\Python Projects\Demo Tracker Tool\Demo Tracker Tool V2.14.html"
```
**Explicación:** Este comando abre la herramienta de rastreo directamente en tu navegador predeterminado para comenzar a usar las nuevas mejoras de importación.

---

## Versión 3.0 (Distributed Manager Phase 2)
**Fecha:** 20 de Febrero de 2026

### Resumen
Implementación de la Fase 2 del Sistema Distribuido: Seguridad TLS, Autenticación, Cloud Ready y Dashboard Web.

### Detalles Técnicos
- **Seguridad**: Comunicación cifrada con SSL/TLS.
- **Autenticación**: Protocolo de login JSON obligatorio.
- **Interfaz**: Dashboard Web dinámico con gráficas en tiempo real.
- **Cloud**: Orquestación Docker para múltiples nodos.

### Comandos de Ejecución (PowerShell con .venv)
1. **Servidor Seguro**:
   ```powershell
   & "d:\Python Projects\Demo Tracker Tool\.venv\Scripts\python.exe" DistributedManager_Phase2/server/secure_server.py
   ```
2. **Dashboard Web**:
   ```powershell
   & "d:\Python Projects\Demo Tracker Tool\.venv\Scripts\python.exe" DistributedManager_Phase2/client/app.py
   ```
   *Acceso: http://localhost:5000*

### Justificación Técnica (Seguridad)
La implementación de **TLS/SSL** es crítica para garantizar:
- **Confidencialidad**: Cifrado punto a punto para evitar robo de credenciales.
- **Integridad**: Protección contra inyección de comandos maliciosos.
- **Autenticación**: Validación de identidad del servidor mediante certificados.

### Nota para LinkedIn (Inglés - 20 palabras)
"Secure distributed system featuring TLS/SSL encryption, Docker-based cloud orchestration, and a real-time Flask dashboard for remote process monitoring. #CloudSecurity"

---

## Versión 2.13 (Validación Actividad Java)
**Fecha:** 20 de Febrero de 2026

### Resumen
Se ha validado y refinado el proyecto de Control Escolar para cumplir con todos los requisitos académicos. Se simplificaron los comentarios para facilitar el aprendizaje de Java.

### Detalles Técnicos
- **Archivos Modificados:** `Alumno.java`, `Curso.java`, `Materia.java`, `Profesor.java`, `Main.java`.
- **Mejoras Realizadas:**
    - Ajuste de constructores (defecto, parámetros, copia) en todas las clases.
    - Implementación robusta de Relaciones (Composición, Agregación, Asociación).
    - Eliminación de caracteres especiales para evitar errores de compilación (`encoding windows-1252`).
    - Actualización de `Main.java` con pasos guiados.

### Ejecución del Proyecto
**IMPORTANTE:** Debes estar en la carpeta principal `Demo Tracker Tool` (no dentro de `Actividad_ControlEscolar`) para que funcione.

**Comando:**
```powershell
cd "d:\Python Projects\Demo Tracker Tool"; javac -d . Actividad_ControlEscolar/*.java; java Actividad_ControlEscolar.Main
```

**Explicación de la salida:**
1.  **Paso 1:** Se muestran las materias creadas con sus datos básicos.
2.  **Paso 2:** Se muestra el curso creado (composición) y el cálculo automático de los créditos totales (suma de las materias).
3.  **Paso 3:** Se crean profesores. Se demuestra cómo un profesor puede existir sin materia y cómo su sueldo se actualiza automáticamente al asignarle una (basado en las horas de la materia).
4.  **Paso 4:** Se inscribe a un alumno en el curso (asociación).
5.  **Paso 5:** Se demuestra el uso del constructor de copia para clonar objetos de forma segura.
- [x] Planning and Setup <!-- id: 0 -->
    - [x] Research Phase 1 implementation in `DistributedProcessManager` <!-- id: 1 -->
    - [x] Create `implementation_plan.md` <!-- id: 2 -->
    - [x] Set up new project structure in `DistributedManager_Phase2` <!-- id: 3 -->
- [x] Security and Authentication (Task 4) <!-- id: 4 -->
    - [x] Generate TLS/SSL certificates <!-- id: 5 -->
    - [x] Implement secure socket communication (TLS) <!-- id: 6 -->
    - [x] Add User Authentication logic <!-- id: 7 -->
- [x] Cloud Integration (Task 5) <!-- id: 8 -->
    - [x] Update Docker configuration for "Cloud" simulation <!-- id: 9 -->
    - [x] Ensure system is scalable/containerized <!-- id: 10 -->
- [x] Interface and Improvements (Task 6) <!-- id: 11 -->
    - [x] Build a Web GUI using Flask/FastAPI <!-- id: 12 -->
    - [x] Implement real-time monitoring visualization <!-- id: 13 -->
    - [x] Add alerts and logging <!-- id: 14 -->
- [x] Final Documentation and Verification <!-- id: 15 -->
    - [x] Update# Release Notes - Demo Tracker Tool

## [Versión 2.17] - 2026-02-23
### Mejoras de Usabilidad
- **Status Dropdown Refactor**: Se reemplazó el campo de texto con búsqueda (datalist) por un menú desplegable (`<select>`) estándar. Ahora todas las opciones son visibles siempre al hacer clic, eliminando la necesidad de borrar el texto previo para ver el resto del menú.
- **Opción "Open"**: Se añadió oficialmente la opción "Open" al listado de estatus para compatibilidad con el flag de registros internos.

### Detalles Técnicos
- **Archivo Principal:** `Demo Tracker Tool v2.17.html`
- **Versión:** v2.17 (Tools) actualizados en encabezado y lógica de respaldo.

### Comando de Ejecución
```powershell
explorer.exe "d:\Python Projects\Demo Tracker Tool\Demo Tracker Tool V2.17.html"
```

---

## [Versión 2.16] - 2026-02-24
### Resumen
Se ha implementado una nueva funcionalidad para la gestión de "Activation Parts" que permite generar plantillas de "Material Master" y "GYPSY" de forma más eficiente.

### Detalles Técnicos
- **Archivo Principal:** `Demo Tracker Tool v2.16.html`
- **Nuevas Funcionalidades:**
    - **Generación de Plantillas:** Se añadió la capacidad de generar plantillas pre-formateadas para "Material Master" y "GYPSY" basadas en inputs del usuario.
    - **Validación de Campos:** Implementación de validaciones para asegurar la integridad de los datos ingresados antes de la generación de plantillas.
    - **Interfaz de Usuario:** Mejoras en la interfaz de usuario para facilitar la entrada de datos y la visualización de las plantillas generadas.
- **Versión:** v2.16 (Tools) actualizados en encabezado y lógica de respaldo.

### Comando de Ejecución
```powershell
explorer.exe "d:\Python Projects\Demo Tracker Tool\Demo Tracker Tool V2.16.html"
```
 id: 16 -->
    - [x] Generate final report in Markdown (for Word) <!-- id: 17 -->
    - [x] Create `walkthrough.md` <!-- id: 18 -->

---

## Versión 2.12 (Nueva Versión)
**Fecha:** 11 de Febrero de 2026

### Resumen
Se ha añadido la nueva pestaña "Tools" con la funcionalidad de "Activation Parts".

### Detalles Técnicos
- **Archivo Principal:** `Demo Tracker Tool V2.12.html`
- **Nuevas Funcionalidades:**
    - **Pestaña Tools:** Nueva sección para utilidades.
    - **Activation Parts:** Formulario para generar plantillas de "Material Master" y "GYPSY".
    - **Botones Generadores:** Crean texto formateado en un área de salida basándose en los inputs.

## Versión 2.11 (Estado Anterior)
**Fecha:** 11 de Febrero de 2026

### Resumen
Se ha retomado el proyecto identificando el archivo `Demo Tracker Tool V2.8.html` como la versión más reciente y funcional (v2.11), la cual coincide con la documentación `Tracker_Documentation.md`.

### Detalles Técnicos
- **Archivo Principal:** `Demo Tracker Tool V2.8.html`
- **Funcionalidades Clave Activas:**
    - Notificaciones por correo (Notify Approver, Notify SO).
    - Gestión de tareas y backlog.
    - Soporte para almacenamiento local (LocalStorage).

### Próximos Pasos
- Validación del código actual.
- Implementación de nuevas funcionalidades según requerimiento.
