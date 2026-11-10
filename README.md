<!DOCTYPE html>
<html lang="es-CO">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#1F3A5F">
  <title>EstadíApp UNIPAZ</title>
  <style>
    :root {
      --azul: #1F3A5F;
      --verde: #2A9D8F;
      --ambar: #E9A23B;
      --fondo: #f4f7fa;
      --blanco: #fff;
      --texto: #243247;
      --muted: #6b7b90;
      --borde: #dfe7ef;
      --rojo: #bc4949;
      --sombra: 0 8px 24px rgba(31, 58, 95, .07);
      --radio: 15px;
    }

    * { box-sizing: border-box; }

    body {
      margin: 0;
      background: var(--fondo);
      color: var(--texto);
      font-family: Arial, Helvetica, sans-serif;
      line-height: 1.5;
    }

    button, input, select { font: inherit; }
    button { cursor: pointer; }

    .app-header {
      padding: 22px 20px;
      color: white;
      background: linear-gradient(125deg, #172d4a, var(--azul), #2b527c);
    }

    .header-inner, main, .footer-inner {
      width: min(1200px, calc(100% - 40px));
      margin: 0 auto;
    }

    .header-inner {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
    }

    .brand { display: flex; align-items: center; gap: 13px; }
    .brand-mark {
      display: grid;
      place-items: center;
      width: 46px;
      height: 46px;
      border-radius: 14px;
      background: rgba(255,255,255,.14);
      border: 1px solid rgba(255,255,255,.2);
      font-weight: 800;
    }

    .brand h1 { margin: 0; font-size: 21px; }
    .brand p { margin: 2px 0 0; font-size: 12px; color: rgba(255,255,255,.75); }
    .header-tag { font-size: 12px; color: #eef4fa; }

    main { padding: 26px 0 42px; }

    .study-heading { margin-bottom: 20px; }
    .eyebrow {
      margin: 0 0 6px;
      color: var(--verde);
      text-transform: uppercase;
      font-size: 10px;
      font-weight: 800;
      letter-spacing: .12em;
    }

    .study-heading h2 {
      margin: 0;
      max-width: 930px;
      color: var(--azul);
      font-size: clamp(20px, 3vw, 28px);
      line-height: 1.25;
    }

    .study-heading > p:not(.eyebrow) {
      margin: 8px 0 0;
      color: var(--muted);
      font-size: 13px;
    }

    .chips { display: flex; gap: 8px; flex-wrap: wrap; margin-top: 14px; }
    .chip {
      padding: 6px 10px;
      border: 1px solid var(--borde);
      border-radius: 999px;
      color: #53647a;
      background: white;
      font-size: 11px;
    }
    .chip strong { color: var(--azul); }

    .tabs {
      display: flex;
      gap: 5px;
      width: fit-content;
      max-width: 100%;
      padding: 5px;
      margin: 20px 0;
      overflow-x: auto;
      border-radius: 12px;
      background: #e8eef4;
    }

    .tab-button {
      padding: 10px 16px;
      border: 0;
      border-radius: 9px;
      background: transparent;
      color: #617187;
      font-size: 12px;
      font-weight: 700;
      white-space: nowrap;
    }

    .tab-button.active {
      background: white;
      color: var(--azul);
      box-shadow: 0 2px 7px rgba(31,58,95,.1);
    }

    .tab-panel { display: none; }
    .tab-panel.active { display: block; }

    .card {
      border: 1px solid var(--borde);
      border-radius: var(--radio);
      background: var(--blanco);
      box-shadow: var(--sombra);
    }
    .card + .card { margin-top: 16px; }
    .card-head { padding: 18px 20px 0; }
    .card-head h3 { margin: 0; color: var(--azul); font-size: 16px; }
    .card-head p { margin: 4px 0 0; color: var(--muted); font-size: 12px; }
    .card-body { padding: 18px 20px 20px; }

    .form-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 14px;
    }

    .field { min-width: 0; }
    .field label {
      display: block;
      margin-bottom: 6px;
      color: #405168;
      font-size: 12px;
      font-weight: 700;
    }
    .required { color: var(--rojo); }

    .field input, .field select {
      width: 100%;
      min-height: 42px;
      padding: 9px 11px;
      border: 1px solid #d5dfe9;
      border-radius: 8px;
      background: white;
      color: var(--texto);
      outline: none;
    }

    .field input:focus, .field select:focus {
      border-color: var(--verde);
      box-shadow: 0 0 0 3px rgba(42,157,143,.12);
    }

    .field input[readonly] { background: #f5f8fa; color: #64748b; }
    .field small { display: block; min-height: 15px; margin-top: 4px; color: var(--muted); font-size: 10px; }

    .actions, .toolbar, .toolbar-actions {
      display: flex;
      align-items: center;
      gap: 9px;
      flex-wrap: wrap;
    }
    .actions { margin-top: 15px; }

    .btn {
      padding: 9px 13px;
      border: 0;
      border-radius: 8px;
      font-size: 12px;
      font-weight: 700;
    }
    .btn-primary { background: var(--verde); color: white; }
    .btn-primary:hover { background: #218477; }
    .btn-secondary { background: #edf2f6; color: #475569; }
    .btn-secondary:hover { background: #e2eaf1; }
    .btn-danger { background: #fff0ef; color: #a94340; }
    .btn-amber { background: #fff2d6; color: #86590a; }

    .notice { min-height: 18px; font-size: 12px; font-weight: 700; }
    .notice.success { color: #167668; }
    .notice.error { color: var(--rojo); }

    .table-card { overflow: hidden; }
    .toolbar { justify-content: space-between; }
    .toolbar h3 { margin: 0; color: var(--azul); font-size: 16px; }
    .toolbar p { margin: 3px 0 0; color: var(--muted); font-size: 11px; }
    .count-badge {
      padding: 6px 10px;
      border-radius: 999px;
      color: var(--azul);
      background: #edf3fa;
      font-size: 11px;
      font-weight: 700;
    }

    .table-wrap { width: 100%; margin-top: 14px; overflow-x: auto; }
    table { width: 100%; border-collapse: collapse; font-size: 12px; }
    .records-table { min-width: 800px; }
    th {
      padding: 10px;
      background: #f5f8fb;
      color: #64748b;
      text-align: left;
      text-transform: uppercase;
      letter-spacing: .04em;
      font-size: 9px;
      white-space: nowrap;
    }
    td { padding: 11px 10px; border-top: 1px solid #edf1f5; white-space: nowrap; }
    .rating { color: #a76b10; letter-spacing: .05em; }
    .icon-button {
      padding: 6px 9px;
      border: 0;
      border-radius: 7px;
      background: #fff0ef;
      color: #a94340;
      font-size: 11px;
      font-weight: 700;
    }

    .empty-state { padding: 26px 12px; text-align: center; color: var(--muted); font-size: 12px; }
    .empty-state strong { display: block; color: var(--azul); margin-bottom: 4px; }

    .metrics-grid {
      display: grid;
      grid-template-columns: repeat(4, minmax(0,1fr));
      gap: 12px;
      margin-bottom: 16px;
    }
    .metric { padding: 16px; }
    .metric-label { color: var(--muted); font-size: 10px; font-weight: 700; }
    .metric-value { margin-top: 4px; color: var(--azul); font-size: 22px; font-weight: 800; }
    .metric-note { color: var(--muted); font-size: 10px; }

    .analysis-grid { display: grid; grid-template-columns: repeat(2, minmax(0,1fr)); gap: 15px; }
    .analysis-grid .card { margin: 0; }
    .chart-list { display: grid; gap: 11px; }
    .chart-row {
      display: grid;
      grid-template-columns: minmax(80px,1fr) 2fr auto;
      align-items: center;
      gap: 9px;
      font-size: 11px;
    }
    .chart-label { overflow: hidden; text-overflow: ellipsis; white-space: nowrap; color: #53647a; }
    .bar-track { height: 9px; overflow: hidden; border-radius: 99px; background: #edf1f5; }
    .bar-fill { height: 100%; border-radius: inherit; background: var(--verde); }
    .bar-fill.blue { background: var(--azul); }
    .bar-fill.amber { background: var(--ambar); }
    .chart-count { min-width: 65px; color: #65748a; text-align: right; font-size: 10px; }

    .stats-list { display: grid; grid-template-columns: repeat(2,minmax(0,1fr)); gap: 10px; }
    .stat-item { border-bottom: 1px solid #edf1f5; padding-bottom: 8px; }
    .stat-item span { display: block; color: var(--muted); font-size: 10px; }
    .stat-item strong { color: var(--azul); font-size: 14px; }
    .helper { margin: 12px 0 0; color: var(--muted); font-size: 11px; }

    .prob-grid { display: grid; grid-template-columns: repeat(2,minmax(0,1fr)); gap: 14px; }
    .prob-options {
      display: grid;
      grid-template-columns: repeat(2,minmax(0,1fr));
      gap: 12px;
      margin-top: 14px;
    }
    .optional-note { color: var(--muted); font-size: 11px; }
    .results-grid {
      display: grid;
      grid-template-columns: repeat(3,minmax(0,1fr));
      gap: 11px;
      margin-top: 16px;
    }
    .result-card {
      min-width: 0;
      padding: 12px;
      border: 1px solid var(--borde);
      border-radius: 10px;
      background: #fbfcfe;
    }
    .result-label { color: var(--muted); font-size: 10px; font-weight: 700; }
    .result-value { margin-top: 3px; color: var(--azul); font-size: 19px; font-weight: 800; }
    .result-operation { margin-top: 4px; color: #58677b; font-size: 10px; overflow-wrap: anywhere; }
    .interpretation {
      margin-top: 14px;
      padding: 13px;
      border: 1px solid #d7ece7;
      border-radius: 10px;
      background: #f0f8f6;
      color: #345b54;
      font-size: 12px;
    }

    .contingency-controls {
      display: grid;
      grid-template-columns: repeat(2,minmax(0,1fr));
      gap: 12px;
      margin-bottom: 14px;
    }
    .contingency-table { min-width: 520px; }
    .contingency-table th, .contingency-table td { text-align: center; }
    .contingency-table th:first-child, .contingency-table td:first-child { text-align: left; }
    .total-cell { font-weight: 800; background: #f4f7fa; }
    .no-data {
      padding: 14px;
      border-radius: 9px;
      background: #f7f9fb;
      color: var(--muted);
      font-size: 12px;
    }

    .report-title { margin: 0; color: var(--azul); font-size: 17px; }
    .report-date { color: var(--muted); font-size: 11px; }
    .report-content { white-space: pre-wrap; color: #435267; font-size: 12px; line-height: 1.8; }
    .report-actions { display: flex; flex-wrap: wrap; gap: 8px; }

    footer { border-top: 1px solid var(--borde); color: #7d8ca0; font-size: 10px; }
    .footer-inner { display: flex; justify-content: space-between; gap: 10px; flex-wrap: wrap; padding: 14px 0 24px; }

    @media (max-width: 760px) {
      .header-tag { display: none; }
      .form-grid, .prob-grid, .prob-options, .contingency-controls { grid-template-columns: repeat(2,minmax(0,1fr)); }
      .metrics-grid { grid-template-columns: repeat(2,minmax(0,1fr)); }
      .analysis-grid { grid-template-columns: 1fr; }
      .results-grid { grid-template-columns: repeat(2,minmax(0,1fr)); }
    }

    @media (max-width: 480px) {
      .header-inner, main, .footer-inner { width: calc(100% - 28px); }
      .app-header { padding: 17px 0; }
      .brand h1 { font-size: 18px; }
      .brand-mark { width: 40px; height: 40px; }
      .form-grid, .prob-grid, .prob-options, .contingency-controls { grid-template-columns: 1fr; }
      .tabs { width: 100%; }
      .tab-button { flex: 1; padding: 9px 8px; font-size: 10px; }
      .results-grid { grid-template-columns: 1fr 1fr; }
      .card-head, .card-body { padding-left: 15px; padding-right: 15px; }
    }

    @media print {
      .app-header, .tabs, #panel-registrar, #panel-analisis, #panel-probabilidad, footer, .report-actions { display: none !important; }
      #panel-informe { display: block !important; }
      body { background: white; }
      .card { box-shadow: none; }
    }
  </style>
</head>
<body>
  <header class="app-header">
    <div class="header-inner">
      <div class="brand">
        <div class="brand-mark" aria-hidden="true">E·U</div>
        <div>
          <h1>EstadíApp UNIPAZ</h1>
          <p>Observatorio del servicio en cafeterías</p>
        </div>
      </div>
      <span class="header-tag">Instituto Universitario de la Paz · Colombia</span>
    </div>
  </header>

  <main>
    <section class="study-heading">
      <p class="eyebrow">Estudio estadístico</p>
      <h2>Análisis estadístico de los tiempos de atención y características del servicio en las cafeterías de UNIPAZ</h2>
      <p>Registra observaciones y consulta sus resultados descriptivos y probabilísticos.</p>
      <div class="chips">
        <span class="chip"><strong>Nominal:</strong> cafetería y producto</span>
        <span class="chip"><strong>Continua:</strong> tiempo en fila</span>
        <span class="chip"><strong>Numérica:</strong> valor de compra</span>
        <span class="chip"><strong>Ordinal:</strong> satisfacción 1–5</span>
      </div>
    </section>

    <nav class="tabs" aria-label="Secciones de la aplicación">
      <button class="tab-button active" type="button" data-tab="registrar" aria-selected="true">Registrar</button>
      <button class="tab-button" type="button" data-tab="analisis" aria-selected="false">Análisis</button>
      <button class="tab-button" type="button" data-tab="probabilidad" aria-selected="false">Probabilidad</button>
      <button class="tab-button" type="button" data-tab="informe" aria-selected="false">Informe</button>
    </nav>

    <!-- Registro de observaciones -->
    <section class="tab-panel active" id="panel-registrar">
      <article class="card">
        <div class="card-head">
          <h3>Nueva observación</h3>
          <p>Todos los campos son obligatorios. La franja horaria se calcula automáticamente.</p>
        </div>
        <div class="card-body">
          <form id="recordForm" novalidate>
            <div class="form-grid">
              <div class="field">
                <label for="fechaHora">Fecha y hora <span class="required">*</span></label>
                <input id="fechaHora" name="fechaHora" type="datetime-local" required>
                <small>Editable; se propone el momento actual.</small>
              </div>
              <div class="field">
                <label for="franja">Franja horaria automática</label>
                <input id="franja" name="franja" type="text" readonly>
                <small>Mañana, tarde o noche.</small>
              </div>
              <div class="field">
                <label for="cafeteria">Cafetería <span class="required">*</span></label>
                <select id="cafeteria" name="cafeteria" required>
                  <option value="">Selecciona una cafetería</option>
                  <option>Cafetería 1</option>
                  <option>Cafetería 2</option>
                  <option>Cafetería 3</option>
                </select>
                <small>Variable cualitativa nominal.</small>
              </div>
              <div class="field">
                <label for="tiempo">Tiempo en fila (min) <span class="required">*</span></label>
                <input id="tiempo" name="tiempo" type="number" min="0" step="any" placeholder="Ej. 4.5" required>
                <small>Admite decimales.</small>
              </div>
              <div class="field">
                <label for="valorCompra">Valor de compra ($) <span class="required">*</span></label>
                <input id="valorCompra" name="valorCompra" type="number" min="0" step="1" placeholder="Ej. 12000" required>
                <small>Pesos colombianos, sin separadores.</small>
              </div>
              <div class="field">
                <label for="producto">Producto principal <span class="required">*</span></label>
                <select id="producto" name="producto" required>
                  <option value="">Selecciona un producto</option>
                  <option>Almuerzo</option>
                  <option>Desayuno</option>
                  <option>Fritos</option>
                  <option>Bebida</option>
                  <option>Snack</option>
                </select>
                <small>Variable cualitativa nominal.</small>
              </div>
              <div class="field">
                <label for="satisfaccion">Satisfacción <span class="required">*</span></label>
                <select id="satisfaccion" name="satisfaccion" required>
                  <option value="">Selecciona una calificación</option>
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                  <option value="4">4</option>
                  <option value="5">5</option>
                </select>
                <small>Escala ordinal de 1 a 5.</small>
              </div>
            </div>
            <div class="actions">
              <button class="btn btn-primary" type="submit">Guardar registro</button>
              <button class="btn btn-secondary" type="reset">Limpiar formulario</button>
              <span class="notice" id="formMessage" role="status" aria-live="polite"></span>
            </div>
          </form>
        </div>
      </article>

      <article class="card table-card">
        <div class="card-body">
          <div class="toolbar">
            <div>
              <h3>Registros del estudio</h3>
              <p>Los registros se conservan automáticamente en este navegador.</p>
            </div>
            <div class="toolbar-actions">
              <span class="count-badge" id="totalRegistros">0 registros</span>
              <button class="btn btn-danger" id="clearAll" type="button">Borrar todo</button>
            </div>
          </div>
          <div class="table-wrap">
            <table class="records-table" aria-label="Registros de observaciones">
              <thead>
                <tr>
                  <th>N.º</th><th>Fecha y hora</th><th>Franja</th><th>Cafetería</th>
                  <th>Tiempo (min)</th><th>Compra (COP)</th><th>Producto</th>
                  <th>Satisfacción</th><th>Acción</th>
                </tr>
              </thead>
              <tbody id="recordsBody"></tbody>
            </table>
            <div class="empty-state" id="emptyRecords">
              <strong>Aún no hay observaciones</strong>
              Completa el formulario para registrar la primera.
            </div>
          </div>
        </div>
      </article>
    </section>

    <!-- Análisis descriptivo -->
    <section class="tab-panel" id="panel-analisis">
      <div class="metrics-grid">
        <article class="card metric">
          <div class="metric-label">Observaciones</div>
          <div class="metric-value" id="metricCount">0</div>
          <div class="metric-note">registros guardados</div>
        </article>
        <article class="card metric">
          <div class="metric-label">Tiempo promedio</div>
          <div class="metric-value" id="metricTiempo">—</div>
          <div class="metric-note">minutos en fila</div>
        </article>
        <article class="card metric">
          <div class="metric-label">Compra promedio</div>
          <div class="metric-value" id="metricCompra">—</div>
          <div class="metric-note">pesos colombianos</div>
        </article>
        <article class="card metric">
          <div class="metric-label">Satisfacción promedio</div>
          <div class="metric-value" id="metricSatisfaccion">—</div>
          <div class="metric-note">escala de 1 a 5</div>
        </article>
      </div>

      <div class="analysis-grid">
        <article class="card">
          <div class="card-head"><h3>Registros por cafetería</h3><p>Frecuencia y proporción.</p></div>
          <div class="card-body"><div class="chart-list" id="cafeteriaChart"></div></div>
        </article>
        <article class="card">
          <div class="card-head"><h3>Producto principal</h3><p>Distribución por producto.</p></div>
          <div class="card-body"><div class="chart-list" id="productoChart"></div></div>
        </article>
        <article class="card">
          <div class="card-head"><h3>Satisfacción</h3><p>Frecuencia para cada nivel de la escala.</p></div>
          <div class="card-body"><div class="chart-list" id="satisfaccionChart"></div></div>
        </article>
        <article class="card">
          <div class="card-head"><h3>Resumen descriptivo</h3><p>Medidas de resumen de los datos.</p></div>
          <div class="card-body">
            <div class="stats-list" id="resumenStats"></div>
            <p class="helper">La desviación estándar mostrada es muestral.</p>
          </div>
        </article>
      </div>
    </section>

    <!-- Probabilidad -->
    <section class="tab-panel" id="panel-probabilidad">
      <article class="card">
        <div class="card-head">
          <h3>Probabilidades de eventos</h3>
          <p>Define el evento A y, opcionalmente, el evento B para calcular probabilidades empíricas.</p>
        </div>
        <div class="card-body">
          <div class="prob-grid">
            <div>
              <div class="field">
                <label for="variableA">Variable del evento A</label>
                <select id="variableA"></select>
              </div>
              <div class="prob-options" id="opcionesA"></div>
            </div>

            <div>
              <div class="field">
                <label for="variableB">Variable cualitativa del evento B (opcional)</label>
                <select id="variableB"></select>
              </div>
              <div class="prob-options" id="opcionesB"></div>
              <p class="optional-note">Deja B sin seleccionar para calcular únicamente P(A).</p>
            </div>
          </div>

          <div class="actions">
            <button class="btn btn-primary" id="calcularProbabilidad" type="button">Calcular</button>
            <span class="notice" id="probMessage" role="status" aria-live="polite"></span>
          </div>

          <div id="resultadosProbabilidad" aria-live="polite"></div>
        </div>
      </article>

      <article class="card">
        <div class="card-head">
          <h3>Tabla de contingencia</h3>
          <p>Selecciona dos variables cualitativas para ver frecuencias conjuntas y totales.</p>
        </div>
        <div class="card-body">
          <div class="contingency-controls">
            <div class="field">
              <label for="filaContingencia">Variable para filas</label>
              <select id="filaContingencia"></select>
            </div>
            <div class="field">
              <label for="columnaContingencia">Variable para columnas</label>
              <select id="columnaContingencia"></select>
            </div>
          </div>
          <div id="contingencyResult"></div>
        </div>
      </article>
    </section>

    <!-- Informe -->
    <section class="tab-panel" id="panel-informe">
      <article class="card">
        <div class="card-head toolbar">
          <div>
            <h3>Informe del estudio</h3>
            <p>Resumen actualizado con base en los datos almacenados.</p>
          </div>
          <div class="report-actions">
            <button class="btn btn-secondary" id="copyReport" type="button">Copiar texto</button>
            <button class="btn btn-amber" id="printReport" type="button">Imprimir / guardar PDF</button>
          </div>
        </div>
        <div class="card-body">
          <h4 class="report-title">Análisis estadístico de los tiempos de atención y características del servicio en las cafeterías de UNIPAZ</h4>
          <p class="report-date" id="reportDate"></p>
          <div class="report-content" id="reportContent"></div>
        </div>
      </article>
    </section>
  </main>

  <footer>
    <div class="footer-inner">
      <span>EstadíApp UNIPAZ · Herramienta educativa de estadística descriptiva</span>
      <span>Información almacenada localmente en este navegador.</span>
    </div>
  </footer>

  <script>
    (() => {
      "use strict";

      const STORAGE_KEY = "estadIAppUNIPAZ.registros.v1";
      const CAFETERIAS = ["Cafetería 1", "Cafetería 2", "Cafetería 3"];
      const PRODUCTOS = ["Almuerzo", "Desayuno", "Fritos", "Bebida", "Snack"];
      const SATISFACCIONES = ["1", "2", "3", "4", "5"];
      const FRANJAS = ["Mañana", "Tarde", "Noche"];

      const VARIABLES = {
        cafeteria: { label: "Cafetería", tipo: "cualitativa", categorias: CAFETERIAS },
        tiempo: { label: "Tiempo en fila (min)", tipo: "cuantitativa" },
        valorCompra: { label: "Valor de compra (COP)", tipo: "cuantitativa" },
        producto: { label: "Producto principal", tipo: "cualitativa", categorias: PRODUCTOS },
        satisfaccion: { label: "Satisfacción", tipo: "cualitativa", categorias: SATISFACCIONES },
        franja: { label: "Franja horaria", tipo: "cualitativa", categorias: FRANJAS }
      };

      const VARIABLES_CUALITATIVAS = ["cafeteria", "producto", "satisfaccion"];
      const $ = (selector) => document.querySelector(selector);
      let registros = loadRecords();

      function loadRecords() {
        try {
          const data = JSON.parse(localStorage.getItem(STORAGE_KEY) || "[]");
          return Array.isArray(data) ? data.filter(isValidRecord) : [];
        } catch (error) {
          console.warn("No se pudieron cargar los registros guardados.", error);
          return [];
        }
      }

      function isValidRecord(item) {
        return item &&
          typeof item.id === "string" &&
          typeof item.fechaHora === "string" &&
          CAFETERIAS.includes(item.cafeteria) &&
          Number.isFinite(Number(item.tiempo)) && Number(item.tiempo) >= 0 &&
          Number.isFinite(Number(item.valorCompra)) && Number(item.valorCompra) >= 0 &&
          PRODUCTOS.includes(item.producto) &&
          Number(item.satisfaccion) >= 1 && Number(item.satisfaccion) <= 5;
      }

      function saveRecords() {
        try {
          localStorage.setItem(STORAGE_KEY, JSON.stringify(registros));
          return true;
        } catch (error) {
          console.error("No fue posible guardar los registros.", error);
          showFormMessage("No se pudieron guardar los datos en este navegador.", "error");
          return false;
        }
      }

      function currentLocalDateTime() {
        const now = new Date();
        return new Date(now.getTime() - now.getTimezoneOffset() * 60000)
          .toISOString()
          .slice(0, 16);
      }

      function getFranja(dateString) {
        const date = new Date(dateString);
        if (Number.isNaN(date.getTime())) return "";
        const hour = date.getHours();
        if (hour >= 5 && hour < 12) return "Mañana";
        if (hour >= 12 && hour < 18) return "Tarde";
        return "Noche";
      }

      function formatDateTime(value) {
        const date = new Date(value);
        if (Number.isNaN(date.getTime())) return "Fecha no válida";
        return new Intl.DateTimeFormat("es-CO", {
          dateStyle: "short",
          timeStyle: "short"
        }).format(date);
      }

      function formatMoney(value) {
        return new Intl.NumberFormat("es-CO", {
          style: "currency",
          currency: "COP",
          maximumFractionDigits: 0
        }).format(Number(value) || 0);
      }

      function formatNumber(value, digits = 2) {
        if (!Number.isFinite(value)) return "—";
        return new Intl.NumberFormat("es-CO", {
          maximumFractionDigits: digits
        }).format(value);
      }

      function formatPercent(value) {
        if (!Number.isFinite(value)) return "No definida";
        return `${formatNumber(value * 100, 2)}%`;
      }

      function escapeHtml(value) {
        return String(value).replace(/[&<>"']/g, (char) => ({
          "&": "&amp;",
          "<": "&lt;",
          ">": "&gt;",
          '"': "&quot;",
          "'": "&#39;"
        }[char]));
      }

      function showFormMessage(text, type = "") {
        const node = $("#formMessage");
        node.textContent = text;
        node.className = `notice ${type}`;
        if (text) {
          window.setTimeout(() => {
            if (node.textContent === text) {
              node.textContent = "";
              node.className = "notice";
            }
          }, 4000);
        }
      }

      function showProbMessage(text, type = "") {
        const node = $("#probMessage");
        node.textContent = text;
        node.className = `notice ${type}`;
      }

      // Fecha actual y franja horaria calculada.
      $("#fechaHora").value = currentLocalDateTime();
      $("#franja").value = getFranja($("#fechaHora").value);
      $("#fechaHora").addEventListener("input", () => {
        $("#franja").value = getFranja($("#fechaHora").value);
      });
      $("#fechaHora").addEventListener("change", () => {
        $("#franja").value = getFranja($("#fechaHora").value);
      });

      // Registrar una observación, validando cada campo antes de persistirla.
      $("#recordForm").addEventListener("submit", (event) => {
        event.preventDefault();

        const fechaHora = $("#fechaHora").value;
        const cafeteria = $("#cafeteria").value;
        const tiempoRaw = $("#tiempo").value.trim();
        const valorRaw = $("#valorCompra").value.trim();
        const producto = $("#producto").value;
        const satisfaccionRaw = $("#satisfaccion").value;
        const tiempo = Number(tiempoRaw);
        const valorCompra = Number(valorRaw);
        const satisfaccion = Number(satisfaccionRaw);

        if (!fechaHora || Number.isNaN(new Date(fechaHora).getTime())) {
          showFormMessage("Ingresa una fecha y hora válidas.", "error");
          return;
        }
        if (!CAFETERIAS.includes(cafeteria)) {
          showFormMessage("Selecciona una cafetería válida.", "error");
          return;
        }
        if (tiempoRaw === "" || !Number.isFinite(tiempo) || tiempo < 0) {
          showFormMessage("El tiempo en fila debe ser mayor o igual a cero.", "error");
          return;
        }
        if (valorRaw === "" || !Number.isInteger(valorCompra) || valorCompra < 0) {
          showFormMessage("El valor de compra debe ser un entero mayor o igual a cero.", "error");
          return;
        }
        if (!PRODUCTOS.includes(producto)) {
          showFormMessage("Selecciona un producto principal válido.", "error");
          return;
        }
        if (!Number.isInteger(satisfaccion) || satisfaccion < 1 || satisfaccion > 5) {
          showFormMessage("La satisfacción debe ser un número entero entre 1 y 5.", "error");
          return;
        }

        const record = {
          id: window.crypto && crypto.randomUUID
            ? crypto.randomUUID()
            : `${Date.now()}-${Math.random().toString(16).slice(2)}`,
          fechaHora,
          franja: getFranja(fechaHora),
          cafeteria,
          tiempo,
          valorCompra,
          producto,
          satisfaccion
        };

        registros.unshift(record);
        if (!saveRecords()) {
          registros.shift();
          return;
        }

        renderAll();
        $("#recordForm").reset();
        $("#fechaHora").value = currentLocalDateTime();
        $("#franja").value = getFranja($("#fechaHora").value);
        showFormMessage("Registro guardado correctamente.", "success");
      });

      $("#recordForm").addEventListener("reset", () => {
        window.setTimeout(() => {
          $("#fechaHora").value = currentLocalDateTime();
          $("#franja").value = getFranja($("#fechaHora").value);
        }, 0);
      });

      // Tabla numerada y eliminación individual con confirmación.
      function renderTable() {
        $("#totalRegistros").textContent =
          `${registros.length} ${registros.length === 1 ? "registro" : "registros"}`;
        $("#emptyRecords").style.display = registros.length ? "none" : "block";

        $("#recordsBody").innerHTML = registros.map((item, index) => {
          const stars = "★".repeat(Number(item.satisfaccion)) +
            "☆".repeat(5 - Number(item.satisfaccion));
          return `
            <tr>
              <td>${index + 1}</td>
              <td>${escapeHtml(formatDateTime(item.fechaHora))}</td>
              <td>${escapeHtml(item.franja || getFranja(item.fechaHora))}</td>
              <td>${escapeHtml(item.cafeteria)}</td>
              <td>${formatNumber(Number(item.tiempo), 2)}</td>
              <td>${escapeHtml(formatMoney(item.valorCompra))}</td>
              <td>${escapeHtml(item.producto)}</td>
              <td class="rating" aria-label="${Number(item.satisfaccion)} de 5">${stars}</td>
              <td><button class="icon-button" type="button" data-delete="${escapeHtml(item.id)}">Eliminar</button></td>
            </tr>
          `;
        }).join("");
      }

      $("#recordsBody").addEventListener("click", (event) => {
        const button = event.target.closest("[data-delete]");
        if (!button) return;
        const item = registros.find((record) => record.id === button.dataset.delete);
        if (!item) return;
        if (!window.confirm(`¿Eliminar el registro de ${item.cafeteria} del ${formatDateTime(item.fechaHora)}?`)) return;

        const previous = registros;
        registros = registros.filter((record) => record.id !== item.id);
        if (!saveRecords()) {
          registros = previous;
          return;
        }
        renderAll();
      });

      $("#clearAll").addEventListener("click", () => {
        if (!registros.length) {
          showFormMessage("No hay registros para borrar.");
          return;
        }
        if (!window.confirm(`¿Deseas eliminar los ${registros.length} registros? Esta acción no se puede deshacer.`)) return;

        const previous = registros;
        registros = [];
        if (!saveRecords()) {
          registros = previous;
          return;
        }
        renderAll();
      });

      // Estadística descriptiva.
      function mean(values) {
        return values.length ? values.reduce((sum, value) => sum + value, 0) / values.length : NaN;
      }

      function median(values) {
        if (!values.length) return NaN;
        const sorted = [...values].sort((a, b) => a - b);
        const middle = Math.floor(sorted.length / 2);
        return sorted.length % 2
          ? sorted[middle]
          : (sorted[middle - 1] + sorted[middle]) / 2;
      }

      function standardDeviation(values) {
        if (!values.length) return NaN;
        if (values.length === 1) return 0;
        const average = mean(values);
        const sumSquares = values.reduce((sum, value) => sum + (value - average) ** 2, 0);
        return Math.sqrt(sumSquares / (values.length - 1));
      }

      function mode(values) {
        if (!values.length) return "—";
        const counts = new Map();
        values.forEach((value) => counts.set(value, (counts.get(value) || 0) + 1));
        const max = Math.max(...counts.values());
        return [...counts.entries()]
          .filter(([, count]) => count === max)
          .map(([value]) => value)
          .join(", ");
      }

      function countCategories(key, categories) {
        return categories.map((label) => ({
          label,
          count: registros.filter((item) => String(item[key]) === String(label)).length
        }));
      }

      function renderChart(elementId, data, color = "") {
        const container = document.getElementById(elementId);
        if (!registros.length) {
          container.innerHTML = '<div class="empty-state">Agrega registros para ver los resultados.</div>';
          return;
        }
        const max = Math.max(1, ...data.map((item) => item.count));
        container.innerHTML = data.map((item) => `
          <div class="chart-row">
            <span class="chart-label">${escapeHtml(item.label)}</span>
            <div class="bar-track">
              <div class="bar-fill ${color}" style="width:${(item.count / max) * 100}%"></div>
            </div>
            <span class="chart-count">${item.count} · ${formatNumber(item.count / registros.length * 100, 1)}%</span>
          </div>
        `).join("");
      }

      function renderAnalysis() {
        const times = registros.map((item) => Number(item.tiempo));
        const purchases = registros.map((item) => Number(item.valorCompra));
        const ratings = registros.map((item) => Number(item.satisfaccion));

        $("#metricCount").textContent = registros.length;
        $("#metricTiempo").textContent = registros.length ? `${formatNumber(mean(times))} min` : "—";
        $("#metricCompra").textContent = registros.length ? formatMoney(mean(purchases)) : "—";
        $("#metricSatisfaccion").textContent = registros.length ? `${formatNumber(mean(ratings))} / 5` : "—";

        renderChart("cafeteriaChart", countCategories("cafeteria", CAFETERIAS), "blue");
        renderChart("productoChart", countCategories("producto", PRODUCTOS));
        renderChart("satisfaccionChart", countCategories("satisfaccion", SATISFACCIONES), "amber");

        const stats = [
          ["Mediana del tiempo", registros.length ? `${formatNumber(median(times))} min` : "—"],
          ["Rango del tiempo", registros.length ? `${formatNumber(Math.max(...times) - Math.min(...times))} min` : "—"],
          ["Desviación estándar", registros.length ? `${formatNumber(standardDeviation(times))} min` : "—"],
          ["Moda de satisfacción", registros.length ? `${mode(ratings)} / 5` : "—"],
          ["Compra mínima", registros.length ? formatMoney(Math.min(...purchases)) : "—"],
          ["Compra máxima", registros.length ? formatMoney(Math.max(...purchases)) : "—"]
        ];

        $("#resumenStats").innerHTML = stats.map(([label, value]) => `
          <div class="stat-item"><span>${escapeHtml(label)}</span><strong>${escapeHtml(value)}</strong></div>
        `).join("");
      }

      // Configuración de los selectores de eventos probabilísticos.
      function populateVariableSelect(select, keys, includeBlank = false, blankText = "Selecciona una variable") {
        select.innerHTML = "";
        if (includeBlank) {
          const blank = document.createElement("option");
          blank.value = "";
          blank.textContent = blankText;
          select.appendChild(blank);
        }
        keys.forEach((key) => {
          const option = document.createElement("option");
          option.value = key;
          option.textContent = VARIABLES[key].label;
          select.appendChild(option);
        });
      }

      function populateCategorySelect(select, categories, placeholder) {
        select.innerHTML = "";
        const blank = document.createElement("option");
        blank.value = "";
        blank.textContent = placeholder;
        select.appendChild(blank);
        categories.forEach((category) => {
          const option = document.createElement("option");
          option.value = category;
          option.textContent = category;
          select.appendChild(option);
        });
      }

      function getRecordValue(record, key) {
        if (key === "franja") return record.franja || getFranja(record.fechaHora);
        return record[key];
      }

      function renderOptionsA() {
        const variable = $("#variableA").value;
        const container = $("#opcionesA");
        container.innerHTML = "";

        if (!variable) return;

        if (VARIABLES[variable].tipo === "cuantitativa") {
          const operatorField = document.createElement("div");
          operatorField.className = "field";
          operatorField.innerHTML = `
            <label for="operadorA">Condición</label>
            <select id="operadorA">
              <option value="gt">Mayor que (&gt;)</option>
              <option value="lte">Menor o igual que (≤)</option>
            </select>
          `;

          const valueField = document.createElement("div");
          valueField.className = "field";
          valueField.innerHTML = `
            <label for="valorA">Valor de comparación</label>
            <input id="valorA" type="number" step="any" placeholder="Escribe un valor">
          `;

          container.append(operatorField, valueField);
        } else {
          const categoryField = document.createElement("div");
          categoryField.className = "field";
          categoryField.style.gridColumn = "1 / -1";
          categoryField.innerHTML = `
            <label for="categoriaA">Categoría de A</label>
            <select id="categoriaA"></select>
          `;
          container.appendChild(categoryField);
          populateCategorySelect($("#categoriaA"), VARIABLES[variable].categorias, "Selecciona una categoría");
        }
      }

      function renderOptionsB() {
        const variable = $("#variableB").value;
        const container = $("#opcionesB");
        container.innerHTML = "";
        if (!variable) return;

        const categoryField = document.createElement("div");
        categoryField.className = "field";
        categoryField.style.gridColumn = "1 / -1";
        categoryField.innerHTML = `
          <label for="categoriaB">Categoría de B</label>
          <select id="categoriaB"></select>
        `;
        container.appendChild(categoryField);
        populateCategorySelect($("#categoriaB"), VARIABLES[variable].categorias, "Selecciona una categoría");
      }

      function evaluateEventA(record, variable, operator, value, category) {
        const recordValue = Number(getRecordValue(record, variable));
        if (VARIABLES[variable].tipo === "cuantitativa") {
          return operator === "gt" ? recordValue > value : recordValue <= value;
        }
        return String(getRecordValue(record, variable)) === String(category);
      }

      function renderProbabilityResults(data) {
        const {
          total, casesA, casesB, casesIntersection, probabilityA,
          probabilityB, probabilityIntersection, conditionalProbability,
          hasB, variableA, operator, valueA, categoryA, variableB, categoryB
        } = data;

        const expressionA = VARIABLES[variableA].tipo === "cuantitativa"
          ? `${VARIABLES[variableA].label} ${operator === "gt" ? ">" : "≤"} ${formatNumber(valueA, 4)}`
          : `${VARIABLES[variableA].label} = ${categoryA}`;

        let resultHtml = `
          <div class="results-grid">
            <div class="result-card">
              <div class="result-label">Total de observaciones</div>
              <div class="result-value">${total}</div>
              <div class="result-operation">N = ${total}</div>
            </div>
            <div class="result-card">
              <div class="result-label">Casos favorables de A</div>
              <div class="result-value">${casesA}</div>
              <div class="result-operation">A: ${escapeHtml(expressionA)}</div>
            </div>
            <div class="result-card">
              <div class="result-label">P(A)</div>
              <div class="result-value">${formatPercent(probabilityA)}</div>
              <div class="result-operation">P(A) = ${casesA} / ${total} = ${formatNumber(probabilityA, 4)}</div>
            </div>
        `;

        if (hasB) {
          resultHtml += `
            <div class="result-card">
              <div class="result-label">Casos de B</div>
              <div class="result-value">${casesB}</div>
              <div class="result-operation">B: ${escapeHtml(VARIABLES[variableB].label)} = ${escapeHtml(categoryB)}</div>
            </div>
            <div class="result-card">
              <div class="result-label">P(B)</div>
              <div class="result-value">${formatPercent(probabilityB)}</div>
              <div class="result-operation">P(B) = ${casesB} / ${total} = ${formatNumber(probabilityB, 4)}</div>
            </div>
            <div class="result-card">
              <div class="result-label">Casos simultáneos A ∩ B</div>
              <div class="result-value">${casesIntersection}</div>
              <div class="result-operation">Coinciden A y B en ${casesIntersection} observaciones.</div>
            </div>
            <div class="result-card">
              <div class="result-label">P(A ∩ B)</div>
              <div class="result-value">${formatPercent(probabilityIntersection)}</div>
              <div class="result-operation">P(A ∩ B) = ${casesIntersection} / ${total} = ${formatNumber(probabilityIntersection, 4)}</div>
            </div>
            <div class="result-card">
              <div class="result-label">P(A dado B)</div>
              <div class="result-value">${formatPercent(conditionalProbability)}</div>
              <div class="result-operation">
                ${casesB === 0
                  ? "No definida: no hay observaciones de B; no se divide por cero."
                  : `P(A | B) = P(A ∩ B) / P(B) = ${formatNumber(probabilityIntersection, 4)} / ${formatNumber(probabilityB, 4)} = ${formatNumber(conditionalProbability, 4)}`}
              </div>
            </div>
          `;

          let interpretation;
          if (casesB === 0) {
            interpretation = "No se puede comparar P(A) con P(A dado B), porque no hay observaciones que cumplan B. P(A dado B) queda sin definir y se evita la división por cero.";
          } else {
            const difference = conditionalProbability - probabilityA;
            if (Math.abs(difference) < 0.0000001) {
              interpretation = `P(A) y P(A dado B) son iguales (${formatPercent(probabilityA)}). En estos datos, pertenecer a B no cambia la proporción observada de A.`;
            } else if (difference > 0) {
              interpretation = `P(A dado B) (${formatPercent(conditionalProbability)}) es mayor que P(A) (${formatPercent(probabilityA)}) por ${formatNumber(difference * 100, 2)} puntos porcentuales. En esta muestra, A aparece proporcionalmente más cuando se cumple B.`;
            } else {
              interpretation = `P(A dado B) (${formatPercent(conditionalProbability)}) es menor que P(A) (${formatPercent(probabilityA)}) por ${formatNumber(Math.abs(difference) * 100, 2)} puntos porcentuales. En esta muestra, A aparece proporcionalmente menos cuando se cumple B.`;
            }
          }

          resultHtml += `<div class="interpretation"><strong>Interpretación:</strong> ${escapeHtml(interpretation)}</div>`;
        } else {
          resultHtml += `
            <div class="result-card">
              <div class="result-label">Evento B</div>
              <div class="result-value">Opcional</div>
              <div class="result-operation">Selecciona B para obtener P(B), P(A ∩ B) y P(A dado B).</div>
            </div>
            </div>
            <div class="interpretation">
              <strong>Interpretación:</strong> P(A) es ${formatPercent(probabilityA)}: la proporción de observaciones que cumplen A.
              Selecciona un evento B para comparar P(A) con P(A dado B).
            </div>
          `;
          return resultHtml;
        }

        resultHtml += "</div>";
        return resultHtml;
      }

      function calculateProbability() {
        const variableA = $("#variableA").value;
        const variableB = $("#variableB").value;
        const hasB = Boolean(variableB);
        const total = registros.length;

        if (!total) {
          showProbMessage("No hay observaciones para calcular probabilidades.", "error");
          $("#resultadosProbabilidad").innerHTML =
            '<div class="no-data">Agrega registros desde la pestaña Registrar y vuelve a calcular.</div>';
          return;
        }

        let operator = "";
        let valueA = null;
        let categoryA = "";

        if (VARIABLES[variableA].tipo === "cuantitativa") {
          operator = $("#operadorA").value;
          const rawValue = $("#valorA").value.trim();
          if (rawValue === "" || !Number.isFinite(Number(rawValue))) {
            showProbMessage("Escribe un valor numérico válido para el evento A.", "error");
            $("#valorA").focus();
            return;
          }
          valueA = Number(rawValue);
        } else {
          categoryA = $("#categoriaA").value;
          if (!categoryA) {
            showProbMessage("Selecciona una categoría para el evento A.", "error");
            $("#categoriaA").focus();
            return;
          }
        }

        let categoryB = "";
        if (hasB) {
          categoryB = $("#categoriaB").value;
          if (!categoryB) {
            showProbMessage("Selecciona una categoría para el evento B o deja B sin seleccionar.", "error");
            $("#categoriaB").focus();
            return;
          }
        }

        const casesA = registros.filter((record) =>
          evaluateEventA(record, variableA, operator, valueA, categoryA)
        ).length;
        const probabilityA = casesA / total;

        let casesB = null;
        let casesIntersection = null;
        let probabilityB = null;
        let probabilityIntersection = null;
        let conditionalProbability = null;

        if (hasB) {
          casesB = registros.filter((record) =>
            String(getRecordValue(record, variableB)) === String(categoryB)
          ).length;
          casesIntersection = registros.filter((record) =>
            evaluateEventA(record, variableA, operator, valueA, categoryA) &&
            String(getRecordValue(record, variableB)) === String(categoryB)
          ).length;

          probabilityB = casesB / total;
          probabilityIntersection = casesIntersection / total;
          conditionalProbability = casesB === 0
            ? null
            : probabilityIntersection / probabilityB;
        }

        $("#resultadosProbabilidad").innerHTML = renderProbabilityResults({
          total, casesA, casesB, casesIntersection, probabilityA,
          probabilityB, probabilityIntersection, conditionalProbability,
          hasB, variableA, operator, valueA, categoryA, variableB, categoryB
        });
        showProbMessage("Cálculo realizado con las observaciones guardadas.", "success");
      }

      function qualitativeValue(record, key) {
        return String(getRecordValue(record, key));
      }

      function renderContingencyTable() {
        const rowKey = $("#filaContingencia").value;
        const colKey = $("#columnaContingencia").value;
        const container = $("#contingencyResult");

        if (!registros.length) {
          container.innerHTML = '<div class="no-data">No hay observaciones disponibles para construir la tabla.</div>';
          return;
        }

        const rowCategories = VARIABLES[rowKey].categorias;
        const colCategories = VARIABLES[colKey].categorias;

        const rowTotals = Array(rowCategories.length).fill(0);
        const colTotals = Array(colCategories.length).fill(0);
        let grandTotal = 0;

        const bodyRows = rowCategories.map((rowCategory, rowIndex) => {
          const cells = colCategories.map((colCategory, colIndex) => {
            const count = registros.filter((record) =>
              qualitativeValue(record, rowKey) === String(rowCategory) &&
              qualitativeValue(record, colKey) === String(colCategory)
            ).length;
            rowTotals[rowIndex] += count;
            colTotals[colIndex] += count;
            grandTotal += count;
            return `<td>${count}</td>`;
          }).join("");

          return `<tr><th scope="row">${escapeHtml(rowCategory)}</th>${cells}<td class="total-cell">${rowTotals[rowIndex]}</td></tr>`;
        }).join("");

        const colTotalCells = colTotals.map((total) => `<td class="total-cell">${total}</td>`).join("");

        container.innerHTML = `
          <div class="table-wrap">
            <table class="contingency-table" aria-label="Tabla de contingencia">
              <thead>
                <tr>
                  <th>${escapeHtml(VARIABLES[rowKey].label)} \\ ${escapeHtml(VARIABLES[colKey].label)}</th>
                  ${colCategories.map((category) => `<th>${escapeHtml(category)}</th>`).join("")}
                  <th class="total-cell">Total fila</th>
                </tr>
              </thead>
              <tbody>
                ${bodyRows}
                <tr>
                  <th class="total-cell">Total columna</th>
                  ${colTotalCells}
                  <td class="total-cell">${grandTotal}</td>
                </tr>
              </tbody>
            </table>
          </div>
          <p class="helper">Total general: <strong>${grandTotal}</strong> observaciones.</p>
        `;
      }

      function initializeProbabilityControls() {
        populateVariableSelect($("#variableA"), Object.keys(VARIABLES));
        populateVariableSelect($("#variableB"), VARIABLES_CUALITATIVAS, true, "Sin evento B (opcional)");
        populateVariableSelect($("#filaContingencia"), VARIABLES_CUALITATIVAS);
        populateVariableSelect($("#columnaContingencia"), VARIABLES_CUALITATIVAS);

        $("#filaContingencia").value = "cafeteria";
        $("#columnaContingencia").value = "producto";

        $("#variableA").addEventListener("change", renderOptionsA);
        $("#variableB").addEventListener("change", renderOptionsB);
        $("#calcularProbabilidad").addEventListener("click", calculateProbability);
        $("#filaContingencia").addEventListener("change", renderContingencyTable);
        $("#columnaContingencia").addEventListener("change", renderContingencyTable);

        renderOptionsA();
        renderOptionsB();
        renderContingencyTable();
      }

      // Informe de resumen.
      function buildReport() {
        const date = new Intl.DateTimeFormat("es-CO", {
          dateStyle: "long",
          timeStyle: "short"
        }).format(new Date());
        $("#reportDate").textContent = `Generado el ${date}`;

        if (!registros.length) {
          $("#reportContent").textContent =
            "No hay observaciones disponibles. Registra datos para generar el resumen del estudio.";
          return;
        }

        const times = registros.map((record) => Number(record.tiempo));
        const purchases = registros.map((record) => Number(record.valorCompra));
        const ratings = registros.map((record) => Number(record.satisfaccion));

        const cafes = countCategories("cafeteria", CAFETERIAS).sort((a, b) => b.count - a.count);
        const products = countCategories("producto", PRODUCTOS).sort((a, b) => b.count - a.count);

        $("#reportContent").textContent = [
          "OBJETIVO Y ALCANCE",
          "Este estudio describe los tiempos de atención y características del servicio de las cafeterías de UNIPAZ, según las observaciones registradas en esta aplicación. Los resultados describen esta base de datos y no necesariamente representan a toda la población estudiantil.",
          "",
          "TAMAÑO DE LA MUESTRA",
          `Total de observaciones: ${registros.length}.`,
          "",
          "RESULTADOS DESCRIPTIVOS",
          `• Tiempo en fila: promedio ${formatNumber(mean(times))} minutos; mediana ${formatNumber(median(times))} minutos; mínimo ${formatNumber(Math.min(...times))} y máximo ${formatNumber(Math.max(...times))}.`,
          `• Valor de compra promedio: ${formatMoney(mean(purchases))}.`,
          `• Satisfacción promedio: ${formatNumber(mean(ratings))} sobre 5.`,
          `• Cafetería con más registros: ${cafes[0].label} (${cafes[0].count}).`,
          `• Producto más frecuente: ${products[0].label} (${products[0].count}).`,
          "",
          "PROBABILIDAD",
          "La pestaña Probabilidad calcula frecuencias relativas de eventos individuales, conjuntos y condicionales, además de tablas de contingencia entre variables cualitativas.",
          "",
          "NOTA",
          "La información se conserva en el almacenamiento local del navegador y no se envía a un servidor."
        ].join("\n");
      }

      // Navegación entre pestañas.
      document.querySelectorAll(".tab-button").forEach((button) => {
        button.addEventListener("click", () => {
          const name = button.dataset.tab;

          document.querySelectorAll(".tab-button").forEach((tab) => {
            const active = tab === button;
            tab.classList.toggle("active", active);
            tab.setAttribute("aria-selected", String(active));
          });

          document.querySelectorAll(".tab-panel").forEach((panel) => {
            const active = panel.id === `panel-${name}`;
            panel.classList.toggle("active", active);
          });

          if (name === "analisis") renderAnalysis();
          if (name === "probabilidad") renderContingencyTable();
          if (name === "informe") buildReport();
        });
      });

      $("#copyReport").addEventListener("click", async () => {
        const text = `${$(".report-title").textContent}\n${$("#reportDate").textContent}\n\n${$("#reportContent").textContent}`;
        try {
          await navigator.clipboard.writeText(text);
          $("#copyReport").textContent = "Copiado";
        } catch (error) {
          const temporary = document.createElement("textarea");
          temporary.value = text;
          temporary.style.position = "fixed";
          temporary.style.opacity = "0";
          document.body.appendChild(temporary);
          temporary.select();
          const copied = document.execCommand("copy");
          temporary.remove();
          $("#copyReport").textContent = copied ? "Copiado" : "No disponible";
        }
        window.setTimeout(() => { $("#copyReport").textContent = "Copiar texto"; }, 1600);
      });

      $("#printReport").addEventListener("click", () => window.print());

      function renderAll() {
        renderTable();
        renderAnalysis();
        renderContingencyTable();
        buildReport();
      }

      initializeProbabilityControls();
      renderAll();
    })();
  </script>
</body>
</html>
