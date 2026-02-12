# Documentación del código: Project Data Tracker & Tasks (App) v2.11

Este archivo HTML contiene una aplicación completa de "Single Page Application" (SPA) que se ejecuta enteramente en el navegador. Utiliza `LocalStorage` para guardar los datos, por lo que funciona sin conexión a internet y sin backend.

A continuación se detalla la estructura del archivo y la función de cada sección clave para facilitar futuros cambios o mantenimiento.

## 1. Estructura General (HTML)

El archivo está dividido en tres grandes bloques dentro de la etiqueta `<body>`:

1.  **Header (`<header>`)**:
    *   Contiene el título de la aplicación, el logo y la información de la versión.
    *   Es estático y visible en todo momento.

2.  **Main Content (`<main>`)**:
    *   Aquí reside la lógica visual de las pestañas.
    *   **Navegación de Pestañas**: Un conjunto de botones (`<button id="tab-btn-...">`) que permiten cambiar entre las diferentes vistas.
    *   **Contenedores de Pestañas (`<div id="tab-content">`)**:
        *   `#tab-tasks`: Gestión de tareas pendientes.
        *   `#tab-data-entry`: Formulario principal para crear o editar registros.
        *   `#tab-backlog`: Tabla para gestionar pedidos con SO# asignado.
        *   `#tab-follow-up`: Lista de proyectos en seguimiento activo.
        *   `#tab-history`: Historial completo de proyectos completados o guardados.
        *   `#tab-support`: Sección de ayuda, links y notas.

3.  **Modales**:
    *   `#backlog-modal`: Ventana emergente oculta por defecto, usada para editar los detalles de producción en la pestaña de Backlog.

## 2. Estilos (CSS)
*   Se utiliza **Tailwind CSS** vía CDN para el 95% de los estilos.
*   Bloque `<style>` interno:
    *   Personalizaciones específicas como animaciones de carga (`spinner`).
    *   Transiciones suaves para abrir/cerrar detalles (`.record-details`).
    *   Badges de conteo en las pestañas.

## 3. Lógica de Negocio (JavaScript)

El script principal se encuentra al final del `<body>`. Aquí están las funciones clave agrupadas por responsabilidad:

### A. Gestión de Datos y Almacenamiento
*   **Constantes (`const ..._KEY`)**: Definen las claves usadas en el `localStorage` del navegador.
*   **`loadRecordsFromLocal()` / `saveRecordsToLocal()`**: Funciones críticas que leen y escriben el arreglo principal de datos (`dataRecords`).
*   **`generateUniqueId()`**: Crea IDs únicos para cada nuevo registro o tarea.

### B. Gestión de Tareas (Tab: Tasks To Do)
*   **`addTask()`**: Crea una nueva tarea.
*   **`renderTasks()`**: Dibuja la lista de tareas pendientes y completadas en el HTML. Controla colores por prioridad.
*   **`openLoanFromTask()`**: Lógica inteligente que permite saltar de una tarea directamente al proyecto asociado.

### C. Formulario de Entrada (Tab: Data Entry)
*   **Mapeo de Campos**: Los objetos `fields` y `selectFields` conectan las variables de JS con los inputs del HTML.
*   **`passToFollowUp()`**: Guarda un registro nuevo en estado "follow-up".
*   **`updateRecordFromEdit()`**: Guarda los cambios de un registro existente.
*   **`resetForm()`**: Limpia el formulario para un nuevo ingreso.
*   **`applyInternalDefaults()`**: Rellena automáticamente ciertos campos si se marca como "Internal".

### D. Renderizado de Listas (Follow-up & History)
*   **`renderFollowUpList()`**: Genera las tarjetas visuales para la pestaña de seguimiento.
*   **`renderRecords()`**: Genera la lista del historial, incluyendo la barra de búsqueda y filtros.
*   **`generateTimelineHTML()`**: Crea la línea de tiempo visual (pasos: Loan -> UCID -> NGQ -> ... -> Ship) basada en los datos del registro.

### E. Sistema de Backlog
*   **`renderBacklog()`**: Filtra y muestra solo los registros que tienen un "SO Number" en una tabla.
*   **`openBacklogEdit()`**: Abre el modal para editar fechas de envío y estado de producción.

### F. Utilidades
*   **Exportación/Importación**: Funciones `exportToCSV()`, `downloadBackupJSON()` y `restoreBackupJSON()` para respaldar datos.
*   **Emails**: `sendApprovalEmail()` y `sendNotifySOEmail()` generan enlaces `mailto:` para abrir el cliente de correo predeterminado con plantillas prellenas.

## Guía Rápida para Cambios Comunes

### ¿Cómo agregar un nuevo campo al formulario?
1.  **HTML**: Agrega el `<input>` o `<select>` dentro del `<form id="record-form">` en la sección `#tab-data-entry`. Asegúrate de darle un `id` único.
2.  **JS (Mapeo)**: Agrega la referencia al nuevo ID dentro del objeto `fields` (si es input) o `selectFields` (si es dropdown) al inicio del script.
3.  **JS (Guardado)**: En la función `passToFollowUp` y `updateRecordFromEdit`, agrega la línea para guardar el valor en el objeto `recordData`.
4.  **JS (Edición)**: En la función `editRecord`, agrega la línea para que al editar un registro, el campo recupere su valor guardado.
5.  **JS (Visualización)**: Si quieres que el dato se vea en las tarjetas, edita los templates HTML dentro de `renderFollowUpList` y `renderRecords`.

### ¿Cómo cambiar los colores de los estados?
Busca la función **`getMilestoneBadge(value, type)`**. Ahí hay un `switch` que define qué clases de Tailwind (colores de fondo y texto) se aplican según el valor del campo (ej. "Yes" = verde, "No" = gris).

### ¿Cómo ajustar la lógica de notificaciones por correo?
Busca las funciones **`sendApprovalEmail()`** o **`sendNotifySOEmail()`**. Ahí puedes editar el texto del `subject` y el `body` de las plantillas de correo.
