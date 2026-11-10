<!DOCTYPE html>
<html lang="es-CO">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#1F3A5F">
  <meta name="description" content="Aplicación de aula para registrar y analizar observaciones de cafeterías universitarias.">
  <title>Estadística en el campus | UNIPAZ</title>
  <link rel="stylesheet" href="styles.css">
  <script src="app.js" defer></script>
</head>
<body>
  <header class="site-header">
    <div class="container header-content">
      <div>
        <p class="eyebrow">Proyecto de aula · UNIPAZ</p>
        <h1>Estadística en el campus</h1>
        <p class="header-description">Observa, registra y analiza la experiencia en las cafeterías.</p>
      </div>
      <span class="header-mark" aria-hidden="true">∑</span>
    </div>
  </header>

  <main class="container">
    <nav class="tabs" aria-label="Secciones de la aplicación" role="tablist">
      <button class="tab-button active" id="tab-registrar" type="button" role="tab" aria-selected="true" aria-controls="panel-registrar" data-tab="registrar">Registrar</button>
      <button class="tab-button" id="tab-analisis" type="button" role="tab" aria-selected="false" aria-controls="panel-analisis" data-tab="analisis">Análisis</button>
      <button class="tab-button" id="tab-probabilidad" type="button" role="tab" aria-selected="false" aria-controls="panel-probabilidad" data-tab="probabilidad">Probabilidad</button>
      <button class="tab-button" id="tab-informe" type="button" role="tab" aria-selected="false" aria-controls="panel-informe" data-tab="informe">Informe</button>
    </nav>

    <section class="panel active" id="panel-registrar" role="tabpanel" aria-labelledby="tab-registrar">
      <div class="section-heading">
        <div>
          <p class="eyebrow">Recolección de datos</p>
          <h2>Registrar observación</h2>
          <p>Registra una visita por observación. La fecha y la hora se completan automáticamente, pero puedes editarlas.</p>
        </div>
      </div>

      <form id="observation-form" class="card form-grid">
        <label>
          Cafetería
          <select id="cafeteria" name="cafeteria" required>
            <option value="">Selecciona una cafetería</option>
            <option value="Cafetería 1">Cafetería 1</option>
            <option value="Cafetería 2">Cafetería 2</option>
            <option value="Cafetería 3">Cafetería 3</option>
          </select>
        </label>

        <label>
          Producto principal
          <select id="producto" name="producto" required>
            <option value="">Selecciona un producto</option>
            <option value="Almuerzo">Almuerzo</option>
            <option value="Desayuno">Desayuno</option>
            <option value="Fritos">Fritos</option>
            <option value="Bebida">Bebida</option>
            <option value="Snack">Snack</option>
          </select>
        </label>

        <label>
          Tiempo en fila (minutos)
          <input id="tiempo" name="tiempo" type="number" min="0" step="0.1" required>
        </label>

        <label>
          Valor de compra (COP)
          <input id="valor" name="valor" type="number" min="0" step="100" required>
        </label>

        <label>
          Satisfacción (1 a 5)
          <select id="satisfaccion" name="satisfaccion" required>
            <option value="">Selecciona una calificación</option>
            <option value="1">1 · Muy baja</option>
            <option value="2">2 · Baja</option>
            <option value="3">3 · Aceptable</option>
            <option value="4">4 · Alta</option>
            <option value="5">5 · Muy alta</option>
          </select>
        </label>

        <label>
          Fecha
          <input id="fecha" name="fecha" type="date" required>
        </label>

        <label>
          Hora
          <input id="hora" name="hora" type="time" required>
        </label>

        <div class="form-actions">
          <button class="button button-primary" type="submit" id="submit-button">Guardar observación</button>
          <button class="button button-secondary hidden" type="button" id="cancel-edit">Cancelar edición</button>
          <span id="form-message" class="form-message" role="status" aria-live="polite"></span>
        </div>
      </form>

      <div class="section-heading list-heading">
        <div>
          <h2>Observaciones registradas</h2>
          <p id="record-count">Todavía no hay observaciones.</p>
        </div>
        <div class="toolbar">
          <button class="button button-secondary" type="button" id="export-csv">Exportar CSV</button>
          <button class="button button-secondary" type="button" id="export-json">Respaldar JSON</button>
          <label class="button button-secondary file-button">
            Importar CSV
            <input id="import-csv" type="file" accept=".csv,text/csv" hidden>
          </label>
          <label class="button button-secondary file-button">
            Restaurar JSON
            <input id="import-json" type="file" accept=".json,application/json" hidden>
          </label>
        </div>
      </div>

      <div class="table-wrap card">
        <table>
          <thead>
            <tr>
              <th>Fecha</th><th>Hora</th><th>Franja</th><th>Cafetería</th>
              <th>Producto</th><th>Fila (min)</th><th>Compra (COP)</th><th>Satisfacción</th><th>Acciones</th>
            </tr>
          </thead>
          <tbody id="records-body"></tbody>
        </table>
        <p id="empty-records" class="empty-state">Los registros aparecerán aquí.</p>
      </div>
    </section>

    <section class="panel" id="panel-analisis" role="tabpanel" aria-labelledby="tab-analisis" hidden>
      <div class="section-heading">
        <div>
          <p class="eyebrow">Descripción de los datos</p>
          <h2>Análisis estadístico</h2>
          <p>Las medidas se calculan con las observaciones guardadas en este navegador. La desviación estándar es muestral.</p>
        </div>
      </div>
      <div id="analysis-content"></div>
    </section>

    <section class="panel" id="panel-probabilidad" role="tabpanel" aria-labelledby="tab-probabilidad" hidden>
      <div class="section-heading">
        <div>
          <p class="eyebrow">Eventos y relaciones</p>
          <h2>Probabilidad</h2>
          <p>Se considera satisfacción alta una calificación de 4 o 5. Las probabilidades se muestran como proporción y porcentaje.</p>
        </div>
      </div>
      <div id="probability-content"></div>
    </section>

    <section class="panel" id="panel-informe" role="tabpanel" aria-labelledby="tab-informe" hidden>
      <div class="section-heading report-heading">
        <div>
          <p class="eyebrow">Síntesis para el proyecto</p>
          <h2>Informe de resultados</h2>
          <p>Las conclusiones se actualizan automáticamente con los datos registrados.</p>
        </div>
        <button class="button button-primary no-print" id="print-report" type="button">Imprimir o guardar como PDF</button>
      </div>
      <div id="report-content" class="report-content card"></div>
    </section>

    <footer class="site-footer">
      <p>Herramienta educativa. Registra observaciones anónimas y evita incluir información personal.</p>
    </footer>
  </main>

  <dialog id="confirm-dialog" class="confirm-dialog">
    <form method="dialog">
      <h2>Confirmar acción</h2>
      <p id="confirm-message"></p>
      <div class="dialog-actions">
        <button class="button button-secondary" value="cancel">Cancelar</button>
        <button class="button button-danger" value="confirm">Confirmar</button>
      </div>
    </form>
  </dialog>
</body>
</html>
