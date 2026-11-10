
<!DOCTYPE html>
<html lang="es-CO">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="theme-color" content="#1F3A5F" />
  <title>EstadíApp UNIPAZ</title>
  <style>
    :root {
      --azul: #1F3A5F;
      --verde: #2A9D8F;
      --ambar: #E9A23B;
      --fondo: #f5f7fb;
      --blanco: #ffffff;
      --texto: #1c2d3d;
      --muted: #6b7a8f;
      --borde: #dfe7f0;
      --rojo: #c94d4d;
      --sombra: 0 10px 22px rgba(31, 58, 95, 0.08);
      --radio: 16px;
    }

    * { box-sizing: border-box; }

    html { scroll-behavior: smooth; }

    body {
      margin: 0;
      font-family: Arial, Helvetica, sans-serif;
      background: var(--fondo);
      color: var(--texto);
      line-height: 1.5;
    }

    button, input, select {
      font: inherit;
    }

    .app-header {
      background: linear-gradient(135deg, var(--azul), #294d79 70%);
      color: white;
      padding: 26px 20px;
      box-shadow: 0 4px 18px rgba(31, 58, 95, 0.18);
    }

    .header-inner {
      max-width: 1200px;
      margin: 0 auto;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 16px;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 14px;
    }

    .brand-mark {
      width: 48px;
      height: 48px;
      border-radius: 14px;
      display: grid;
      place-items: center;
      background: rgba(255,255,255,0.12);
      border: 1px solid rgba(255,255,255,0.25);
      font-weight: bold;
      font-size: 1.1rem;
    }

    .brand h1 {
      margin: 0;
      font-size: clamp(1.2rem, 2vw, 1.8rem);
      letter-spacing: -0.02em;
    }

    .brand p {
      margin: 2px 0 0;
      font-size: 0.78rem;
      color: rgba(255,255,255,0.75);
    }

    .header-tag {
      border: 1px solid rgba(255,255,255,0.18);
      border-radius: 999px;
      padding: 8px 12px;
      font-size: 0.78rem;
      white-space: nowrap;
      background: rgba(255,255,255,0.04);
    }

    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 26px 20px 40px;
    }

    .study-heading {
      margin-bottom: 18px;
    }

    .eyebrow {
      margin: 0 0 8px;
      text-transform: uppercase;
      letter-spacing: 0.1em;
      font-size: 0.68rem;
      font-weight: bold;
      color: var(--verde);
    }

    .study-heading h2 {
      margin: 0;
      font-size: clamp(1.35rem, 2vw, 2.1rem);
      color: var(--azul);
      line-height: 1.25;
    }

    .study-heading > p {
      margin: 10px 0 0;
      color: var(--muted);
      font-size: 0.95rem;
    }

    .summary-strip {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: 16px;
    }

    .summary-chip {
      background: var(--blanco);
      border: 1px solid var(--borde);
      color: #42526a;
      border-radius: 999px;
      padding: 7px 11px;
      font-size: 0.72rem;
    }

    .summary-chip strong {
      color: var(--azul);
    }

    .tabs {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin: 18px 0 20px;
      background: #edf3f8;
      padding: 7px;
      border-radius: 12px;
      width: fit-content;
      max-width: 100%;
    }

    .tab-button {
      border: none;
      background: transparent;
      color: #5b6c82;
      font-weight: 700;
      font-size: 0.85rem;
      padding: 10px 16px;
      border-radius: 9px;
      cursor: pointer;
      transition: 0.2s ease;
    }

    .tab-button:hover {
      color: var(--azul);
    }

    .tab-button.active {
      background: var(--blanco);
      color: var(--azul);
      box-shadow: 0 2px 6px rgba(31,58,95,0.08);
    }

    .tab-panel {
      display: none;
    }

    .tab-panel.active {
      display: block;
      animation: fadeIn 0.2s ease;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(4px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .card {
      background: var(--blanco);
      border: 1px solid var(--borde);
      border-radius: var(--radio);
      box-shadow: var(--sombra);
    }

    .card + .card {
      margin-top: 18px;
    }

    .card-head {
      padding: 18px 20px 0;
    }

    .card-head h3 {
      margin: 0;
      color: var(--azul);
      font-size: 1.04rem;
    }

    .card-head p {
      margin: 5px 0 0;
      color: var(--muted);
      font-size: 0.76rem;
    }

    .card-body {
      padding: 18px 20px 20px;
    }

    .form-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 16px;
    }

    .field {
      min-width: 0;
    }

    .field label {
      display: block;
      margin-bottom: 7px;
      color: #42526a;
      font-size: 0.76rem;
      font-weight: 700;
    }

    .required {
      color: var(--rojo);
    }

    .field input, .field select {
      width: 100%;
      min-height: 44px;
      padding: 10px 12px;
      border: 1px solid #d7e0eb;
      border-radius: 9px;
      background: white;
      color: var(--texto);
      outline: none;
      transition: 0.15s ease;
    }

    .field input:focus, .field select:focus {
      border-color: var(--verde);
      box-shadow: 0 0 0 3px rgba(42, 157, 143, 0.12);
    }

    .field input[readonly] {
      background: #f7f9fb;
      color: #5b6f82;
    }

    .field small {
      display: block;
      margin-top: 6px;
      font-size: 0.68rem;
      color: var(--muted);
      min-height: 15px;
    }

    .form-actions {
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: 16px;
    }

    .btn {
      border: none;
      border-radius: 9px;
      padding: 10px 15px;
      font-weight: 700;
      cursor: pointer;
      transition: 0.15s ease;
      font-size: 0.78rem;
    }

    .btn:hover {
      transform: translateY(-1px);
    }

    .btn-primary {
      background: var(--verde);
      color: white;
    }

    .btn-primary:hover {
      background: #22847d;
    }

    .btn-secondary {
      background: #eef3f8;
      color: #42526a;
    }

    .btn-secondary:hover {
      background: #e5edf5;
    }

    .btn-danger {
      background: #fff0f0;
      color: #af4d4d;
    }

    .btn-danger:hover {
      background: #ffe4e4;
    }

    .btn-amber {
      background: #fff4db;
      color: #8a5d08;
    }

    .btn-amber:hover {
      background: #ffe8b8;
    }

    .notice {
      min-height: 18px;
      font-weight: 700;
      font-size: 0.76rem;
    }

    .notice.success {
      color: #0b7d6a;
    }

    .notice.error {
      color: var(--rojo);
    }

    .table-toolbar {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      flex-wrap: wrap;
    }

    .table-toolbar h3 {
      margin: 0;
      color: var(--azul);
      font-size: 1rem;
    }

    .table-toolbar p {
      margin: 4px 0 0;
      color: var(--muted);
      font-size: 0.7rem;
    }

    .table-actions {
      display: flex;
      align-items: center;
      gap: 10px;
      flex-wrap: wrap;
    }

    .total-badge {
      background: #edf5f8;
      color: var(--azul);
      border-radius: 999px;
      padding: 6px 10px;
      font-size: 0.72rem;
      font-weight: 700;
    }

    .table-wrap {
      overflow-x: auto;
      margin-top: 14px;
    }

    table {
      width: 100%;
      min-width: 780px;
      border-collapse: collapse;
      font-size: 0.76rem;
    }

    th {
      text-align: left;
      background: #f6f9fc;
      color: #61718a;
      font-size: 0.67rem;
      letter-spacing: 0.05em;
      text-transform: uppercase;
      padding: 11px 10px;
      border-bottom: 1px solid var(--borde);
    }

    td {
      padding: 12px 10px;
      border-top: 1px solid #edf1f5;
      white-space: nowrap;
    }

    tbody tr:hover {
      background: #fbfcfe;
    }

    .index-cell {
      color: var(--muted);
      font-weight: 700;
    }

    .rating {
      color: #a66d14;
      letter-spacing: 0.08em;
      font-size: 0.9rem;
    }

    .icon-button {
      background: #fff0f0;
      color: #af4d4d;
      border: none;
      border-radius: 7px;
      font-weight: 700;
      padding: 6px 8px;
      cursor: pointer;
    }

    .empty-state {
      padding: 30px 15px;
      text-align: center;
      color: var(--muted);
      font-size: 0.78rem;
      border-top: 1px solid var(--borde);
    }

    .empty-state strong {
      display: block;
      color: var(--azul);
      margin-bottom: 4px;
    }

    .metrics-grid {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 14px;
      margin-bottom: 18px;
    }

    .metric {
      position: relative;
      overflow: hidden;
      padding: 18px 16px;
    }

    .metric::after {
      content: "";
      position: absolute;
      width: 54px;
      height: 54px;
      right: -14px;
      top: -14px;
      border-radius: 50%;
      background: rgba(42,157,143,0.08);
    }

    .metric-label {
      font-size: 0.68rem;
      letter-spacing: 0.03em;
      text-transform: uppercase;
      color: var(--muted);
      font-weight: 700;
    }

    .metric-value {
      position: relative;
      z-index: 1;
      font-size: clamp(1.3rem, 2vw, 2rem);
      color: var(--azul);
      font-weight: 800;
      margin-top: 6px;
      letter-spacing: -0.04em;
    }

    .metric-note {
      position: relative;
      z-index: 1;
      margin-top: 4px;
      color: var(--muted);
      font-size: 0.68rem;
    }

    .analysis-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 16px;
    }

    .chart-list {
      display: grid;
      gap: 12px;
    }

    .chart-row {
      display: grid;
      grid-template-columns: minmax(90px, 1fr) 2fr auto;
      gap: 10px;
      align-items: center;
      font-size: 0.72rem;
    }

    .chart-label {
      color: #51657b;
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
    }

    .bar-track {
      height: 10px;
      background: #edf2f6;
      border-radius: 999px;
      overflow: hidden;
    }

    .bar-fill {
      height: 100%;
      background: var(--verde);
      border-radius: inherit;
      min-width: 0;
    }

    .bar-fill.blue {
      background: var(--azul);
    }

    .bar-fill.amber {
      background: var(--ambar);
    }

    .chart-count {
      color: #64748b;
      font-size: 0.7rem;
      text-align: right;
      min-width: 56px;
    }

    .stats-list {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 10px 12px;
    }

    .stat-item {
      border-bottom: 1px solid #edf1f5;
      padding-bottom: 8px;
    }

    .stat-item span {
      display: block;
      font-size: 0.66rem;
      color: var(--muted);
      margin-bottom: 4px;
    }

    .stat-item strong {
      color: var(--azul);
      font-size: 0.92rem;
    }

    .helper {
      margin: 12px 0 0;
      color: var(--muted);
      font-size: 0.7rem;
    }

    .prob-controls {
      display: grid;
      grid-template-columns: repeat(2, minmax(0,1fr));
      gap: 14px;
    }

    .prob-result {
      margin-top: 16px;
      padding: 16px;
      border-radius: 12px;
      background: #edf9f6;
      border: 1px solid #d4ece7;
    }

    .result-label {
      color: #52736b;
      font-weight: 700;
      font-size: 0.72rem;
    }

    .prob-result strong {
      display: block;
      margin-top: 4px;
      color: var(--verde);
      font-size: clamp(1.7rem, 2vw, 2.2rem);
      letter-spacing: -0.04em;
    }

    .prob-result p {
      margin: 5px 0 0;
      color: #5d716b;
      font-size: 0.72rem;
    }

    .report-title {
      margin: 0 0 4px;
      color: var(--azul);
      font-size: 1.1rem;
    }

    .report-date {
      margin: 0 0 16px;
      color: var(--muted);
      font-size: 0.72rem;
    }

    .report-content {
      white-space: pre-wrap;
      font-size: 0.78rem;
      line-height: 1.8;
      color: #42526a;
    }

    .report-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-left: auto;
    }

    .footer {
      max-width: 1200px;
      margin: 24px auto 0;
      padding: 14px 20px 0;
      border-top: 1px solid var(--borde);
      display: flex;
      justify-content: space-between;
      gap: 12px;
      flex-wrap: wrap;
      color: #7d8ca0;
      font-size: 0.68rem;
    }

    @media (max-width: 760px) {
      .header-inner {
        flex-wrap: wrap;
      }

      .form-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .metrics-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .analysis-grid {
        grid-template-columns: 1fr;
      }

      .prob-controls {
        grid-template-columns: 1fr;
      }
    }

    @media (max-width: 480px) {
      .container {
        padding-left: 15px;
        padding-right: 15px;
      }

      .form-grid {
        grid-template-columns: 1fr;
      }

      .metrics-grid {
        grid-template-columns: 1fr;
      }

      .tabs {
        width: 100%;
      }

      .tab-button {
        flex: 1;
        min-width: 0;
      }

      .card-head, .card-body {
        padding-left: 16px;
        padding-right: 16px;
      }
    }
  </style>
</head>
<body>
  <header class="app-header">
    <div class="header-inner">
      <div class="brand">
        <div class="brand-mark" aria-hidden="true">EU</div>
        <div>
          <h1>EstadíApp UNIPAZ</h1>
          <p>Observatorio del servicio cafetero</p>
        </div>
      </div>
      <div class="header-tag">UNIPAZ · Colombia</div>
    </div>
  </header>

  <main class="container">
    <section class="study-heading">
      <p class="eyebrow">Estudio estadístico</p>
      <h2>Análisis estadístico de los tiempos de atención y características del servicio en las cafeterías de UNIPAZ</h2>
      <p>Registro de observaciones para describir tiempos, compra y satisfacción del servicio.</p>

      <div class="summary-strip" aria-label="Variables del estudio">
        <span class="summary-chip"><strong>Nominal:</strong> cafetería y producto</span>
        <span class="summary-chip"><strong>Cuantitativa continua:</strong> tiempo en fila</span>
        <span class="summary-chip"><strong>Numérica:</strong> valor de compra</span>
        <span class="summary-chip"><strong>Ordinal:</strong> satisfacción 1–5</span>
      </div>
    </section>

    <nav class="tabs" aria-label="Pestañas de la aplicación">
      <button class="tab-button active" type="button" data-panel="registrar" aria-selected="true">Registrar</button>
      <button class="tab-button" type="button" data-panel="analisis" aria-selected="false">Análisis</button>
      <button class="tab-button" type="button" data-panel="probabilidad" aria-selected="false">Probabilidad</button>
      <button class="tab-button" type="button" data-panel="informe" aria-selected="false">Informe</button>
    </nav>

    <section class="tab-panel active" id="panel-registrar">
      <article class="card">
        <div class="card-head">
          <div>
            <h3>Nueva observación</h3>
            <p>Registra una visita y valida todos los datos antes de guardar.</p>
          </div>
        </div>
        <div class="card-body">
          <form id="record-form" novalidate>
            <div class="form-grid">
              <div class="field">
                <label for="fechaHora">Fecha y hora <span class="required">*</span></label>
                <input id="fechaHora" name="fechaHora" type="datetime-local" required />
                <small>Se propone la fecha y hora actuales y puede editarse.</small>
              </div>

              <div class="field">
                <label for="franja">Franja horaria</label>
                <input id="franja" name="franja" type="text" readonly />
                <small>Se asigna automáticamente según la hora registrada.</small>
              </div>

              <div class="field">
                <label for="cafeteria">Cafetería <span class="required">*</span></label>
                <select id="cafeteria" name="cafeteria" required>
                  <option value="">Selecciona una opción</option>
                  <option>Cafetería 1</option>
                  <option>Cafetería 2</option>
                  <option>Cafetería 3</option>
                </select>
                <small>Variable cualitativa nominal.</small>
              </div>

              <div class="field">
                <label for="tiempo">Tiempo en fila (min) <span class="required">*</span></label>
                <input id="tiempo" name="tiempo" type="number" min="0" step="any" placeholder="Ej. 4.5" required />
                <small>Puede incluir decimales.</small>
              </div>

              <div class="field">
                <label for="valorCompra">Valor de compra ($) <span class="required">*</span></label>
                <input id="valorCompra" name="valorCompra" type="number" min="0" step="1" placeholder="Ej. 12000" required />
                <small>En pesos colombianos (COP).</small>
              </div>

              <div class="field">
                <label for="producto">Producto principal <span class="required">*</span></label>
                <select id="producto" name="producto" required>
                  <option value="">Selecciona una opción</option>
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
                  <option value="">Selecciona una opción</option>
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                  <option value="4">4</option>
                  <option value="5">5</option>
                </select>
                <small>Escala ordinal de 1 a 5.</small>
              </div>
            </div>

            <div class="form-actions">
              <button class="btn btn-primary" type="submit">Guardar registro</button>
              <button class="btn btn-secondary" type="reset">Limpiar</button>
              <span id="form-message" class="notice" aria-live="polite"></span>
            </div>
          </form>
        </div>
      </article>

      <article class="card">
        <div class="card-body">
          <div class="table-toolbar">
            <div>
              <h3>Registros del estudio</h3>
              <p>Los datos se guardan automáticamente en el navegador.</p>
            </div>
            <div class="table-actions">
              <span class="total-badge" id="totalRegistros">0 registros</span>
              <button id="clearAll" class="btn btn-danger" type="button">Borrar todo</button>
            </div>
          </div>

          <div class="table-wrap">
            <table aria-label="Tabla de registros">
              <thead>
                <tr>
                  <th>N.º</th>
                  <th>Fecha y hora</th>
                  <th>Franja</th>
                  <th>Cafetería</th>
                  <th>Tiempo (min)</th>
                  <th>Compra ($)</th>
                  <th>Producto</th>
                  <th>Satisfacción</th>
                  <th>Acción</th>
                </tr>
              </thead>
              <tbody id="recordsBody"></tbody>
            </table>
            <div id="emptyRecords" class="empty-state">
              <strong>Aún no hay observaciones</strong>
              Completa el formulario para guardar el primer registro.
            </div>
          </div>
        </div>
      </article>
    </section>

    <section class="tab-panel" id="panel-analisis">
      <div class="metrics-grid">
        <article class="card metric">
          <div class="metric-label">Observaciones</div>
          <div class="metric-value" id="metricCount">0</div>
          <div class="metric-note">registros válidos</div>
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
          <div class="metric-note">escala 1–5</div>
        </article>
      </div>

      <div class="analysis-grid">
        <article class="card">
          <div class="card-head">
            <div>
              <h3>Registros por cafetería</h3>
              <p>Frecuencia por local.</p>
            </div>
          </div>
          <div class="card-body">
            <div class="chart-list" id="cafeteriaChart"></div>
          </div>
        </article>

        <article class="card">
          <div class="card-head">
            <div>
              <h3>Productos principales</h3>
              <p>Distribución por tipo de consumo.</p>
            </div>
          </div>
          <div class="card-body">
            <div class="chart-list" id="productoChart"></div>
          </div>
        </article>

        <article class="card">
          <div class="card-head">
            <div>
              <h3>Satisfacción</h3>
              <p>Distribución de la escala ordinal.</p>
            </div>
          </div>
          <div class="card-body">
            <div class="chart-list" id="satisfaccionChart"></div>
          </div>
        </article>

        <article class="card">
          <div class="card-head">
            <div>
              <h3>Resumen descriptivo</h3>
              <p>Indicadores calculados con los registros.</p>
            </div>
          </div>
          <div class="card-body">
            <div class="stats-list" id="resumenStats"></div>
            <p class="helper">Se usan medidas de tendencia central y dispersión para resumir la muestra.</p>
          </div>
        </article>
      </div>
    </section>

    <section class="tab-panel" id="panel-probabilidad">
      <article class="card">
        <div class="card-head">
          <div>
            <h3>Probabilidades empíricas</h3>
            <p>Estadística descriptiva de eventos observados.</p>
          </div>
        </div>
        <div class="card-body">
          <div class="prob-controls">
            <div class="field">
              <label for="probVariable">Variable</label>
              <select id="probVariable">
                <option value="cafeteria">Cafetería</option>
                <option value="producto">Producto principal</option>
                <option value="satisfaccion">Satisfacción</option>
                <option value="franja">Franja horaria</option>
              </select>
            </div>

            <div class="field">
              <label for="probEvento">Evento</label>
              <select id="probEvento">
                <option value="">Selecciona un evento</option>
              </select>
            </div>
          </div>

          <div class="prob-result" aria-live="polite">
            <div class="result-label" id="probLabel">Probabilidad del evento</div>
            <strong id="probValue">—</strong>
            <p id="probDetail">Registra datos para calcular la probabilidad.</p>
          </div>

          <p class="helper">Fórmula: P(evento) = número de registros con el evento ÷ total de registros.</p>
        </div>
      </article>
    </section>

    <section class="tab-panel" id="panel-informe">
      <article class="card">
        <div class="card-head">
          <div>
            <h3>Informe del estudio</h3>
            <p>Resumen actualizado basado en los registros almacenados.</p>
          </div>

          <div class="report-actions">
            <button id="copyReport" class="btn btn-secondary" type="button">Copiar texto</button>
            <button id="printReport" class="btn btn-amber" type="button">Imprimir / PDF</button>
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

  <footer class="footer">
    <span>EstadíApp UNIPAZ · Herramienta educativa de estadística descriptiva</span>
    <span>Datos almacenados localmente en este navegador</span>
  </footer>

  <script>
    (() => {
      "use strict";

      const STORAGE_KEY = "estadIAppUNIPAZ.registros.v1";
      const CAFETERIAS = ["Cafetería 1", "Cafetería 2", "Cafetería 3"];
      const PRODUCTOS = ["Almuerzo", "Desayuno", "Fritos", "Bebida", "Snack"];
      const FRANJAS = ["Mañana", "Tarde", "Noche"];

      let registros = loadRecords();

      const form = document.getElementById("record-form");
      const fechaHoraInput = document.getElementById("fechaHora");
      const franjaInput = document.getElementById("franja");
      const formMessage = document.getElementById("form-message");
      const recordsBody = document.getElementById("recordsBody");
      const emptyRecords = document.getElementById("emptyRecords");
      const totalRegistros = document.getElementById("totalRegistros");

      function loadRecords() {
        try {
          const data = JSON.parse(localStorage.getItem(STORAGE_KEY) || "[]");
          return Array.isArray(data) ? data.filter(validRecord) : [];
        } catch (error) {
          console.warn("No se pudieron cargar los registros locales:", error);
          return [];
        }
      }

      function validRecord(item) {
        if (!item || typeof item !== "object") return false;
        return (
          typeof item.id === "string" &&
          typeof item.fechaHora === "string" &&
          CAFETERIAS.includes(item.cafeteria) &&
          Number.isFinite(Number(item.tiempo)) &&
          Number(item.tiempo) >= 0 &&
          Number.isFinite(Number(item.valorCompra)) &&
          Number(item.valorCompra) >= 0 &&
          PRODUCTOS.includes(item.producto) &&
          Number(item.satisfaccion) >= 1 &&
          Number(item.satisfaccion) <= 5
        );
      }

      function saveRecords() {
        try {
          localStorage.setItem(STORAGE_KEY, JSON.stringify(registros));
          return true;
        } catch (error) {
          console.error("No se pudo guardar:", error);
          showMessage("No se pudo guardar la información en este navegador.", "error");
          return false;
        }
      }

      function showMessage(text, kind = "") {
        formMessage.textContent = text;
        formMessage.className = "notice " + (kind ? kind : "");
        if (text) {
          window.setTimeout(() => {
            if (formMessage.textContent === text) {
              formMessage.textContent = "";
              formMessage.className = "notice";
            }
          }, 4000);
        }
      }

      function nowLocalString() {
        const now = new Date();
        const offset = now.getTimezoneOffset() * 60000;
        return new Date(now.getTime() - offset).toISOString().slice(0, 16);
      }

      function franjaPorFechaHora(value) {
        const fecha = new Date(value);
        if (Number.isNaN(fecha.getTime())) return "";
        const hora = fecha.getHours();
        if (hora >= 5 && hora < 12) return "Mañana";
        if (hora >= 12 && hora < 18) return "Tarde";
        return "Noche";
      }

      function formatDateTime(value) {
        const fecha = new Date(value);
        if (Number.isNaN(fecha.getTime())) return "Fecha no válida";
        return new Intl.DateTimeFormat("es-CO", {
          dateStyle: "short",
          timeStyle: "short"
        }).format(fecha);
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
          minimumFractionDigits: 0,
          maximumFractionDigits: digits
        }).format(value);
      }

      function escapeHtml(str) {
        return String(str).replace(/[&<>"']/g, char => ({
          "&": "&amp;",
          "<": "&lt;",
          ">": "&gt;",
          '"': "&quot;",
          "'": "&#39;"
        }[char]));
      }

      function renderTable() {
        totalRegistros.textContent = `${registros.length} ${registros.length === 1 ? "registro" : "registros"}`;
        emptyRecords.style.display = registros.length ? "none" : "block";

        recordsBody.innerHTML = registros.map((item, index) => {
          const satisfaccionEstrellas = "★".repeat(Number(item.satisfaccion)) + "☆".repeat(5 - Number(item.satisfaccion));
          return `
            <tr>
              <td class="index-cell">${index + 1}</td>
              <td>${escapeHtml(formatDateTime(item.fechaHora))}</td>
              <td>${escapeHtml(item.franja || franjaPorFechaHora(item.fechaHora))}</td>
              <td>${escapeHtml(item.cafeteria)}</td>
              <td>${formatNumber(Number(item.tiempo), 2)}</td>
              <td>${escapeHtml(formatMoney(item.valorCompra))}</td>
              <td>${escapeHtml(item.producto)}</td>
              <td class="rating" aria-label="${Number(item.satisfaccion)} de 5">${satisfaccionEstrellas}</td>
              <td><button class="icon-button" type="button" data-delete="${item.id}">Eliminar</button></td>
            </tr>
          `;
        }).join("");
      }

      function mean(arr) {
        if (!arr.length) return NaN;
        return arr.reduce((sum, v) => sum + v, 0) / arr.length;
      }

      function median(arr) {
        if (!arr.length) return NaN;
        const sorted = [...arr].sort((a, b) => a - b);
        const mid = Math.floor(sorted.length / 2);
        if (sorted.length % 2 === 0) {
          return (sorted[mid - 1] + sorted[mid]) / 2;
        }
        return sorted[mid];
      }

      function range(arr) {
        if (!arr.length) return NaN;
        return Math.max(...arr) - Math.min(...arr);
      }

      function stdDev(arr) {
        if (arr.length < 2) return arr.length ? 0 : NaN;
        const avg = mean(arr);
        return Math.sqrt(arr.reduce((acc, v) => acc + (v - avg) ** 2, 0) / (arr.length - 1));
      }

      function mode(arr) {
        if (!arr.length) return "—";
        const map = new Map();
        arr.forEach(v => map.set(v, (map.get(v) || 0) + 1));
        const maxCount = Math.max(...map.values());
        const modes = [...map.entries()]
          .filter(([, count]) => count === maxCount)
          .map(([value]) => value);
        return modes.join(", ");
      }

      function countBy(arr, keyName, categories) {
        return categories.map((category) => ({
          label: category,
          count: arr.filter(item => String(item[keyName]) === String(category)).length
        }));
      }

      function buildBarChart(selector, data, colorClass = "") {
        const root = document.getElementById(selector);
        if (!registros.length) {
          root.innerHTML = '<div class="empty-state"><strong>Sin datos</strong>Agrega registros para ver la gráfica.</div>';
          return;
        }

        const maxCount = Math.max(1, ...data.map(item => item.count));
        root.innerHTML = data.map(item => {
          const porcentaje = (item.count / registros.length) * 100;
          return `
            <div class="chart-row">
              <span class="chart-label">${escapeHtml(item.label)}</span>
              <div class="bar-track" aria-label="${escapeHtml(item.label)}: ${item.count}">
                <div class="bar-fill ${colorClass}" style="width:${(item.count / maxCount) * 100}%"></div>
              </div>
              <span class="chart-count">${item.count} · ${formatNumber(porcentaje, 1)}%</span>
            </div>
          `;
        }).join("");
      }

      function renderAnalysis() {
        const tiempos = registros.map(item => Number(item.tiempo));
        const compras = registros.map(item => Number(item.valorCompra));
        const ratings = registros.map(item => Number(item.satisfaccion));

        document.getElementById("metricCount").textContent = registros.length;
        document.getElementById("metricTiempo").textContent = registros.length ? `${formatNumber(mean(tiempos), 2)} min` : "—";
        document.getElementById("metricCompra").textContent = registros.length ? formatMoney(mean(compras)) : "—";
        document.getElementById("metricSatisfaccion").textContent = registros.length ? `${formatNumber(mean(ratings), 2)} / 5` : "—";

        buildBarChart("cafeteriaChart", countBy(registros, "cafeteria", CAFETERIAS), "blue");
        buildBarChart("productoChart", countBy(registros, "producto", PRODUCTOS));
        buildBarChart("satisfaccionChart", countBy(registros, "satisfaccion", [1,2,3,4,5]), "amber");

        const resumen = [
          ["Mediana del tiempo", registros.length ? `${formatNumber(median(tiempos), 2)} min` : "—"],
          ["Rango del tiempo", registros.length ? `${formatNumber(range(tiempos), 2)} min` : "—"],
          ["Desviación estándar", registros.length ? `${formatNumber(stdDev(tiempos), 2)} min` : "—"],
          ["Moda de satisfacción", registros.length ? `${mode(ratings)} / 5` : "—"],
          ["Compra mínima", registros.length ? formatMoney(Math.min(...compras)) : "—"],
          ["Compra máxima", registros.length ? formatMoney(Math.max(...compras)) : "—"]
        ];

        const resumenNode = document.getElementById("resumenStats");
        resumenNode.innerHTML = resumen.map(([label, value]) => `
          <div class="stat-item">
            <span>${escapeHtml(label)}</span>
            <strong>${escapeHtml(value)}</strong>
          </div>
        `).join("");
      }

      function renderProbability() {
        const variable = document.getElementById("probVariable").value;
        const eventoSelect = document.getElementById("probEvento");
        const categorias = variable === "cafeteria"
          ? CAFETERIAS
          : variable === "producto"
            ? PRODUCTOS
            : variable === "satisfaccion"
              ? ["1","2","3","4","5"]
              : FRANJAS;

        eventoSelect.innerHTML = `<option value="">Selecciona un evento</option>${categorias.map(v => `<option value="${escapeHtml(v)}">${escapeHtml(v)}</option>`).join("")}`;
      }

      function calculateProbability() {
        const variable = document.getElementById("probVariable").value;
        const evento = document.getElementById("probEvento").value;
        const label = document.getElementById("probVariable").selectedOptions[0].text;

        if (!registros.length) {
          document.getElementById("probLabel").textContent = "Probabilidad del evento";
          document.getElementById("probValue").textContent = "—";
          document.getElementById("probDetail").textContent = "Registra observaciones para calcular la probabilidad.";
          return;
        }

        if (!evento) {
          document.getElementById("probLabel").textContent = "Probabilidad del evento";
          document.getElementById("probValue").textContent = "—";
          document.getElementById("probDetail").textContent = "Selecciona un evento para calcular la probabilidad empírica.";
          return;
        }

        let matches = 0;
        for (const item of registros) {
          let actual = "";
          if (variable === "franja") {
            actual = item.franja || franjaPorFechaHora(item.fechaHora);
          } else {
            actual = item[variable];
          }
          if (String(actual) === String(evento)) matches++;
        }

        const probability = matches / registros.length;
        document.getElementById("probLabel").textContent = `P(${label} = ${evento})`;
        document.getElementById("probValue").textContent = `${formatNumber(probability * 100, 1)}%`;
        document.getElementById("probDetail").textContent = `${matches} de ${registros.length} registros (${formatNumber(probability, 3)} proporción).`;
      }

      function buildReport() {
        const dateNode = document.getElementById("reportDate");
        const contentNode = document.getElementById("reportContent");

        const now = new Intl.DateTimeFormat("es-CO", {
          dateStyle: "long",
          timeStyle: "short"
        }).format(new Date());

        dateNode.textContent = `Generado el ${now}`;

        if (!registros.length) {
          contentNode.textContent = "No hay registros aún. Agrega observaciones desde la pestaña Registrar para generar el informe.";
          return;
        }

        const tiempos = registros.map(item => Number(item.tiempo));
        const compras = registros.map(item => Number(item.valorCompra));
        const satisfacción = registros.map(item => Number(item.satisfaccion));

        const frecuenciaCafeterias = countBy(registros, "cafeteria", CAFETERIAS).sort((a, b) => b.count - a.count);
        const frecuenciaProductos = countBy(registros, "producto", PRODUCTOS).sort((a, b) => b.count - a.count);

        const topCafe = frecuenciaCafeterias[0];
        const topProducto = frecuenciaProductos[0];

        const text = [
          "OBJETIVO Y ALCANCE",
          "Este estudio describe los tiempos de atención y algunas características del servicio de las cafeterías de UNIPAZ. La información corresponde a las observaciones registradas en esta aplicación, por lo que se considera un conjunto de datos locales del navegador.",
          "",
          "TAMAÑO DE LA MUESTRA",
          `Se registraron ${registros.length} observaciones.`,
          "",
          "RESULTADOS DESCRIPTIVOS",
          `• Tiempo en fila: promedio ${formatNumber(mean(tiempos), 2)} min; mediana ${formatNumber(median(tiempos), 2)} min; rango ${formatNumber(range(tiempos), 2)} min; desviación estándar ${formatNumber(stdDev(tiempos), 2)} min.`,
          `• Valor de compra: promedio ${formatMoney(mean(compras))}; mínimo ${formatMoney(Math.min(...compras))}; máximo ${formatMoney(Math.max(...compras))}.`,
          `• Satisfacción: promedio ${formatNumber(mean(satisfacción), 2)} sobre 5; moda ${mode(satisfacción)}.`,
          `• Cafetería con mayor frecuencia: ${topCafe.label} (${topCafe.count} registros, ${(topCafe.count / registros.length * 100).toFixed(1)}%).`,
          `• Producto principal más frecuente: ${topProducto.label} (${topProducto.count} registros, ${(topProducto.count / registros.length * 100).toFixed(1)}%).`,
          "",
          "CONSIDERACIONES",
          "La probabilidad empírica se calcula como frecuencia relativa y representa la proporción observada en la muestra recolectada. Los registros se almacenan localmente en el navegador y no se envían a ningún servidor."
        ].join("\n");

        contentNode.textContent = text;
      }

      function updateTabs() {
        const buttons = document.querySelectorAll(".tab-button");
        buttons.forEach(button => {
          button.addEventListener("click", () => {
            const panelName = button.dataset.panel;
            buttons.forEach(btn => {
              const active = btn === button;
              btn.classList.toggle("active", active);
              btn.setAttribute("aria-selected", String(active));
            });

            document.querySelectorAll(".tab-panel").forEach(panel => {
              const active = panel.id === `panel-${panelName}`;
              panel.classList.toggle("active", active);
              panel.style.display = active ? "block" : "none";
            });

            if (panelName === "analisis") renderAnalysis();
            if (panelName === "probabilidad") renderProbability();
            if (panelName === "informe") buildReport();
          });
        });
      }

      function setInitialDate() {
        fechaHoraInput.value = nowLocalString();
        franjaInput.value = franjaPorFechaHora(fechaHoraInput.value);
      }

      fechaHoraInput.addEventListener("input", () => {
        franjaInput.value = franjaPorFechaHora(fechaHoraInput.value);
      });

      form.addEventListener("submit", (event) => {
        event.preventDefault();

        const data = new FormData(form);
        const fechaHora = String(data.get("fechaHora") || "").trim();
        const cafeteria = String(data.get("cafeteria") || "").trim();
        const tiempo = Number(data.get("tiempo"));
        const valorCompra = Number(data.get("valorCompra"));
        const producto = String(data.get("producto") || "").trim();
        const satisfaccion = Number(data.get("satisfaccion"));

        if (!fechaHora || Number.isNaN(new Date(fechaHora).getTime())) {
          showMessage("Debe ingresar una fecha y hora válida.", "error");
          return;
        }

        if (!CAFETERIAS.includes(cafeteria)) {
          showMessage("Seleccione una cafetería válida.", "error");
          return;
        }

        if (!Number.isFinite(tiempo) || tiempo < 0) {
          showMessage("El tiempo en fila es requerido y debe ser mayor o igual a cero.", "error");
          return;
        }

        if (!Number.isFinite(valorCompra) || valorCompra < 0 || !Number.isInteger(valorCompra)) {
          showMessage("El valor de compra debe ser un número entero y mayor o igual a cero.", "error");
          return;
        }

        if (!PRODUCTOS.includes(producto)) {
          showMessage("Seleccione un producto principal válido.", "error");
          return;
        }

        if (!Number.isInteger(satisfaccion) || satisfaccion < 1 || satisfaccion > 5) {
          showMessage("La satisfacción debe ser un valor entre 1 y 5.", "error");
          return;
        }

        const nuevoRegistro = {
          id: (window.crypto && crypto.randomUUID) ? crypto.randomUUID() : `${Date.now()}-${Math.random().toString(16).slice(2)}`,
          fechaHora,
          franja: franjaPorFechaHora(fechaHora),
          cafeteria,
          tiempo,
          valorCompra,
          producto,
          satisfaccion
        };

        registros.unshift(nuevoRegistro);

        if (!saveRecords()) {
          registros.shift();
          return;
        }

        renderAll();
        form.reset();
        setInitialDate();
        showMessage("Registro guardado correctamente.", "success");
      });

      form.addEventListener("reset", () => {
        setTimeout(() => {
          setInitialDate();
        }, 0);
      });

      document.getElementById("recordsBody").addEventListener("click", (event) => {
        const target = event.target.closest("[data-delete]");
        if (!target) return;

        const id = target.getAttribute("data-delete");
        const item = registros.find(registro => registro.id === id);
        if (!item) return;

        const confirmDelete = window.confirm(`¿Desea eliminar este registro de ${item.cafeteria} del ${formatDateTime(item.fechaHora)}?`);
        if (!confirmDelete) return;

        registros = registros.filter(registro => registro.id !== id);
        saveRecords();
        renderAll();
      });

      document.getElementById("clearAll").addEventListener("click", () => {
        if (!registros.length) {
          showMessage("No hay registros para eliminar.", "");
          return;
        }

        const confirmar = window.confirm(`¿Está seguro de eliminar los ${registros.length} registros registrados?`);
        if (!confirmar) return;

        registros = [];
        saveRecords();
        renderAll();
        showMessage("Se eliminaron todos los registros.", "success");
      });

      document.getElementById("probVariable").addEventListener("change", () => {
        renderProbability();
        calculateProbability();
      });

      document.getElementById("probEvento").addEventListener("change", calculateProbability);

      document.getElementById("copyReport").addEventListener("click", async () => {
        const text = `${document.querySelector(".report-title").textContent}\n${document.getElementById("reportDate").textContent}\n\n${document.getElementById("reportContent").textContent}`;

        try {
          await navigator.clipboard.writeText(text);
          document.getElementById("copyReport").textContent = "Copiado";
          setTimeout(() => { document.getElementById("copyReport").textContent = "Copiar texto"; }, 1500);
        } catch (error) {
          const temp = document.createElement("textarea");
          temp.value = text;
          temp.style.position = "fixed";
          temp.style.opacity = "0";
          document.body.appendChild(temp);
          temp.select();
          try {
            document.execCommand("copy");
            document.getElementById("copyReport").textContent = "Copiado";
          } catch {
            document.getElementById("copyReport").textContent = "No disponible";
          }
          setTimeout(() => { document.getElementById("copyReport").textContent = "Copiar texto"; }, 1500);
          document.body.removeChild(temp);
        }
      });

      document.getElementById("printReport").addEventListener("click", () => {
        window.print();
      });

      function renderAll() {
        renderTable();
        renderAnalysis();
        renderProbability();
        calculateProbability();
        buildReport();
      }

      setInitialDate();
      updateTabs();
      renderAll();
    })();
  </script>
</body>
</html>
