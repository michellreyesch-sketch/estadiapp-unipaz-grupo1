index.html
styles.css
app.js
README.md
:root {
  --azul: #1F3A5F;
  --verde: #2A9D8F;
  --ambar: #E9A23B;
  --coral: #e76f51;
  --crema: #fffaf1;
  --fondo: #f7f3eb;
  --texto: #293747;
  --muted: #718096;
  --borde: #eadfce;
  --blanco: #fff;
  --sombra: 0 12px 30px rgba(67, 49, 26, .09);
  --radio: 18px;
}

* { box-sizing: border-box; }

body {
  margin: 0;
  background:
    radial-gradient(circle at 8% 16%, #f9e3be80, transparent 22rem),
    var(--fondo);
  color: var(--texto);
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  line-height: 1.55;
}

.container {
  width: min(1160px, calc(100% - 36px));
  margin: 0 auto;
}

/* Portada con colores cálidos y detalles decorativos */
.site-header {
  position: relative;
  overflow: hidden;
  padding: 48px 0 68px;
  background: linear-gradient(125deg, #1F3A5F 0%, #285c65 72%, #2A9D8F 130%);
  color: white;
}

.site-header::before,
.site-header::after {
  position: absolute;
  border-radius: 50%;
  pointer-events: none;
  content: "";
}

.site-header::before {
  width: 360px;
  height: 360px;
  top: -210px;
  right: 12%;
  border: 1px solid #ffffff30;
  box-shadow: 0 0 0 34px #ffffff0b, 0 0 0 70px #ffffff08;
}

.site-header::after {
  right: 5%;
  bottom: 9px;
  content: "🍲   🥑   ☕";
  font-size: clamp(1.7rem, 4vw, 2.8rem);
  opacity: .9;
  transform: rotate(-7deg);
}

.header-content {
  position: relative;
  z-index: 1;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
}

h1, h2, h3, p { margin-top: 0; }

h1 {
  margin-bottom: 9px;
  font-size: clamp(2rem, 5vw, 3.2rem);
  letter-spacing: -.045em;
  line-height: 1.1;
}

.header-description {
  max-width: 650px;
  margin-bottom: 0;
  color: #e4f0ed;
  font-size: 1.05rem;
}

.eyebrow {
  margin-bottom: 8px;
  color: var(--verde);
  font-size: .75rem;
  font-weight: 800;
  letter-spacing: .13em;
  text-transform: uppercase;
}

.site-header .eyebrow { color: #a7eee0; }

.header-mark {
  display: grid;
  width: 86px;
  height: 86px;
  flex: 0 0 auto;
  place-items: center;
  border: 1px solid #ffffff55;
  border-radius: 27px;
  background: #ffffff19;
  font-size: 2.7rem;
  backdrop-filter: blur(8px);
  transform: rotate(5deg);
}

/* Barra de pestañas */
.tabs {
  position: sticky;
  top: 10px;
  z-index: 5;
  display: flex;
  gap: 7px;
  margin: -25px auto 30px;
  padding: 7px;
  overflow-x: auto;
  border: 1px solid #eadfce;
  border-radius: 15px;
  background: #fffdf9ed;
  box-shadow: var(--sombra);
  backdrop-filter: blur(10px);
}

.tab-button {
  min-width: 115px;
  flex: 1;
  padding: 12px 15px;
  border: 0;
  border-radius: 10px;
  background: transparent;
  color: #617083;
  font: inherit;
  font-weight: 750;
  cursor: pointer;
  transition: .2s ease;
}

.tab-button:hover { background: #fff3de; color: var(--azul); }

.tab-button.active {
  background: var(--azul);
  color: white;
  box-shadow: 0 5px 14px #1f3a5f30;
}

/* Secciones y formularios */
.panel { margin-bottom: 40px; }

.section-heading {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 20px;
  margin: 28px 0 18px;
}

.section-heading h2 {
  margin-bottom: 6px;
  color: var(--azul);
  font-size: clamp(1.45rem, 3vw, 1.9rem);
  letter-spacing: -.03em;
}

.section-heading p:last-child { color: var(--muted); }

.card {
  border: 1px solid var(--borde);
  border-radius: var(--radio);
  background: var(--blanco);
  box-shadow: var(--sombra);
}

.form-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 18px;
  padding: 24px;
}

label {
  display: flex;
  flex-direction: column;
  gap: 7px;
  color: var(--azul);
  font-size: .9rem;
  font-weight: 720;
}

input, select {
  width: 100%;
  min-height: 46px;
  padding: 10px 12px;
  border: 1px solid #ded8ce;
  border-radius: 10px;
  background: #fffdf9;
  color: var(--texto);
  font: inherit;
}

input:focus, select:focus, button:focus-visible {
  border-color: var(--verde);
  outline: 3px solid #2A9D8F30;
  outline-offset: 2px;
}

.form-actions {
  grid-column: 1 / -1;
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 10px;
}

.form-message { color: #187a6f; font-weight: 650; }
.form-message.error { color: #b42318; }

/* Botones */
.button {
  display: inline-flex;
  min-height: 42px;
  align-items: center;
  justify-content: center;
  padding: 10px 15px;
  border: 1px solid transparent;
  border-radius: 10px;
  font: inherit;
  font-size: .88rem;
  font-weight: 750;
  cursor: pointer;
  transition: transform .18s ease, box-shadow .18s ease, background .18s ease;
}

.button:hover { transform: translateY(-2px); }

.button-primary {
  background: linear-gradient(135deg, var(--verde), #218477);
  color: white;
  box-shadow: 0 5px 12px #2A9D8F35;
}

.button-secondary {
  border-color: var(--borde);
  background: white;
  color: var(--azul);
}

.button-secondary:hover { background: #fff6e8; }
.button-danger { background: #b42318; color: white; }
.hidden { display: none !important; }

/* Registros y tablas */
.list-heading { align-items: center; margin-top: 34px; }
.list-heading h2 { font-size: 1.35rem; }

.toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.file-button {
  display: inline-flex;
  min-height: 42px;
  align-items: center;
  justify-content: center;
  padding: 9px 13px;
  border: 1px solid var(--borde);
  border-radius: 10px;
  background: white;
  color: var(--azul);
  cursor: pointer;
}

.table-wrap { overflow-x: auto; }

table {
  width: 100%;
  border-collapse: separate;
  border-spacing: 0;
  font-size: .88rem;
}

th, td {
  padding: 12px 14px;
  border-bottom: 1px solid #f0ece5;
  text-align: left;
  white-space: nowrap;
}

th {
  background: #fff6e8;
  color: var(--azul);
  font-size: .78rem;
  font-weight: 800;
  text-transform: uppercase;
}

tbody tr:hover { background: #f5fbf7; }
tbody tr:last-child td { border-bottom: 0; }

.empty-state {
  padding: 25px;
  color: var(--muted);
  text-align: center;
}

.row-actions { display: flex; gap: 6px; }

.row-actions button {
  padding: 6px 9px;
  border: 1px solid var(--borde);
  border-radius: 7px;
  background: white;
  color: var(--azul);
  cursor: pointer;
}

/* Tarjetas de análisis */
.metrics-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 15px;
  margin: 18px 0 24px;
}

.metric-card {
  position: relative;
  overflow: hidden;
  padding: 20px;
  border: 1px solid var(--borde);
  border-radius: 15px;
  background: white;
  box-shadow: var(--sombra);
}

.metric-card::after {
  position: absolute;
  top: -20px;
  right: -15px;
  width: 75px;
  height: 75px;
  border-radius: 50%;
  background: #2A9D8F18;
  content: "";
}

.metric-card span { color: var(--muted); font-size: .85rem; }
.metric-card strong {
  display: block;
  margin-top: 5px;
  color: var(--azul);
  font-size: 1.65rem;
  font-weight: 850;
}

.analysis-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 16px;
}

.analysis-card, .probability-card { padding: 20px; }

.analysis-card h3, .probability-card h3 {
  color: var(--azul);
  font-size: 1.05rem;
}

.compact-table th, .compact-table td {
  padding: 9px 11px;
  white-space: normal;
}

.bar-list { display: grid; gap: 11px; margin-top: 15px; }

.bar-row {
  display: grid;
  grid-template-columns: minmax(80px, 1fr) 2fr auto;
  align-items: center;
  gap: 9px;
  font-size: .86rem;
}

.bar-track {
  height: 12px;
  overflow: hidden;
  border-radius: 99px;
  background: #f0ece5;
}

.bar-fill {
  height: 100%;
  border-radius: inherit;
  background: linear-gradient(90deg, var(--verde), #71cbb8);
}

.bar-value { color: var(--muted); font-size: .8rem; }

.notice {
  padding: 16px;
  border-left: 5px solid var(--ambar);
  border-radius: 10px;
  background: #fff6e8;
  color: #654516;
}

.probability-card { margin-bottom: 15px; }

.probability-value {
  display: inline-block;
  margin-bottom: 10px;
  padding: 6px 12px;
  border-radius: 9px;
  background: #e4f5f1;
  color: #167468;
  font-size: 1.25rem;
  font-weight: 850;
}

.interpretation { color: var(--muted); }

.report-content { padding: 25px; line-height: 1.75; }
.report-content h3 { margin-top: 24px; color: var(--azul); }
.report-content li { margin-bottom: 8px; }

.site-footer {
  padding: 22px 0 30px;
  color: var(--muted);
  font-size: .85rem;
  text-align: center;
}

.confirm-dialog {
  width: min(430px, calc(100% - 28px));
  padding: 22px;
  border: 1px solid var(--borde);
  border-radius: 16px;
  box-shadow: var(--sombra);
}

.confirm-dialog::backdrop { background: #172d4b88; }
.dialog-actions { display: flex; justify-content: flex-end; gap: 9px; }

@media (max-width: 760px) {
  .form-grid { grid-template-columns: repeat(2, minmax(0, 1fr)); }
  .analysis-grid { grid-template-columns: 1fr; }
  .section-heading, .list-heading { align-items: stretch; flex-direction: column; }
  .toolbar { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); }
}

@media (max-width: 500px) {
  .container { width: calc(100% - 22px); }
  .site-header { padding: 32px 0 48px; }
  .header-mark { width: 60px; height: 60px; font-size: 2rem; }
  .form-grid, .metrics-grid { grid-template-columns: 1fr; }
  .form-actions { align-items: stretch; flex-direction: column; }
  .form-actions .button { width: 100%; }
  .toolbar .button, .toolbar .file-button { width: 100%; }
  .bar-row { grid-template-columns: 74px 1fr auto; gap: 6px; }
}

@media print {
  .site-header, .tabs, #panel-registrar, #panel-analisis,
  #panel-probabilidad, .no-print, .site-footer {
    display: none !important;
  }

  body { background: white; }
  main.container { width: 100%; }
  #panel-informe, #panel-informe[hidden] { display: block !important; }
  .report-content { border: 0; box-shadow: none; }
}
