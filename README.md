# Dashboard de Seguimiento — Proyecto GAD Municipal Santo Domingo

Dashboard web interactivo para el control y seguimiento de la ejecución del cronograma del proyecto **"Consultoría de implementación de una solución informática integral de gestión administrativa, financiera y tributaria"** para el GAD Municipal de Santo Domingo.

## ¿Qué hace?

- **Métricas generales (KPIs):** avance real ponderado por duración, avance esperado a la fecha, desviación en puntos, actividades completadas, número de alertas y porcentaje de tiempo transcurrido del proyecto.
- **Alertas de retraso:** detecta automáticamente las actividades cuya fecha fin ya venció sin estar al 100%, o cuyo avance real está más de 10 puntos por debajo del esperado.
- **Avance por fase:** barra de progreso por cada fase, con una marca del avance esperado a la fecha de corte.
- **Estado de actividades:** gráfico de dona (Completado / En curso / Retrasada / Por iniciar).
- **Línea de tiempo (Gantt):** barras por actividad sobre el calendario del proyecto, con línea del día actual.
- **Tabla editable:** permite reportar el % de ejecución y registrar observaciones por actividad; todos los indicadores se recalculan al instante.
- **Importar / exportar Excel:** carga el cronograma desde un `.xlsx` y descarga una versión actualizada con los avances reportados.

## Uso

1. Abre `index.html` en cualquier navegador moderno (no requiere instalación ni servidor).
2. Edita el **% de ejecución** y las **observaciones** en la tabla.
3. Pulsa **Descargar Excel actualizado** para guardar tu reporte.
4. Para retomar un reporte previo, usa **Cargar Excel** y selecciona el archivo guardado.

> La **fecha de corte** se toma automáticamente del día en que se abre el dashboard.

## Estructura del Excel

El archivo `.xlsx` debe tener, en la primera hoja:

- Filas de cabecera: `Proyecto`, `Contrante:`, `Fecha Contrato`, `Fecha Inicio:`, `Fecha fin:`.
- Una fila de encabezado de tabla cuya primera celda diga **`Fase`**, con las columnas: Fase, Nombre de la Actividad, Tipo Actividad, Personal Asignado, Duración (días calendario), Fecha inicio, Fecha finalización, % Ejecución, Observaciones.
- El `% Ejecución` puede venir como fracción (`0`–`1`) o como porcentaje (`0`–`100`).

## Tecnología

HTML, CSS y JavaScript en un solo archivo autocontenido. Usa dos librerías por CDN:

- [Chart.js](https://www.chartjs.org/) — gráfico de dona.
- [SheetJS (xlsx)](https://sheetjs.com/) — importar/exportar Excel.

## Publicación con GitHub Pages

1. Crea un repositorio público y sube `index.html`.
2. **Settings → Pages → Source: Deploy from a branch**, rama `main`, carpeta `/ (root)`.
3. Espera 1–2 minutos: la URL pública será `https://TU-USUARIO.github.io/NOMBRE-REPO/`.

## Persistencia de datos

Al ser un sitio estático, los avances **no se guardan en el servidor**: el flujo de respaldo es exportar/cargar el archivo Excel. Para guardado automático y multiusuario se requiere una base de datos y un backend (ver alternativas propuestas por separado).

## Limitaciones

- El avance esperado se calcula de forma lineal entre la fecha de inicio y fin de cada actividad; no contempla pesos internos ni dependencias entre tareas.
- Los datos editados en el navegador se pierden al cerrar si no se descarga el Excel.

---
*Generado para el espacio de trabajo Analista Origami.*
