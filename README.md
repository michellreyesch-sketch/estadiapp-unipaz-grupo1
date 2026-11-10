:root {
  --azul: #1F3A5F;
  --azul-claro: #315681;
  --verde: #2A9D8F;
  --verde-claro: #e4f5f1;
  --ambar: #E9A23B;
  --fondo: #f3f6fb;
  --texto: #26364a;
  --muted: #718096;
  --borde: #e2e8f0;
  --blanco: #fff;
  --sombra: 0 10px 30px rgba(31, 58, 95, .08);
  --sombra-hover: 0 16px 38px rgba(31, 58, 95, .14);
  --radio: 16px;
}

* {
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  min-height: 100vh;
  margin: 0;
  background:
    radial-gradient(ellipse at 90% 8%, rgba(42, 157, 143, .08), transparent 28rem),
    var(--fondo);
  color: var(--texto);
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  line-height: 1.55;
}

button,
input,
select {
  font: inherit;
}

button,
label,
a {
  -webkit-tap-highlight-color: transparent;
}

.container {
  width: min(1160px, calc(100% - 40px));
  margin: 0 auto;
}

/* Encabezado */
.site-header {
  position: relative;
  overflow: hidden;
  padding: 38px 0 56px;
  background: linear-gradient(120deg, #172d4b 0%, var(--azul) 58%, #285c70 100%);
  color: var(--blanco);
}

.site-header::before,
.site-header::after {
  position: absolute;
  content: "";
  border: 1px solid rgba(255, 255, 255, .1);
  border-radius: 50%;
  pointer-events: none;
}

.site-header::before {
  width: 430px;
  height: 430px;
  top: -265px;
  right: 12%;
  box-shadow: 0 0 0 42px rgba(255,255,255,.025), 0 0 0 88px rgba(255,255,255,.02);
}

.site-header::after {
  width: 230px;
  height: 230px;
  right: -60px;
  bottom: -155px;
  border-color: rgba(233, 162, 59, .35);
}

.header-content {
  position: relative;
  z-index: 1;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
}

h1,
h2,
h3,
p {
  margin-top: 0;
}

h1 {
  margin-bottom: 8px;
  font-size: clamp(2rem, 5vw, 3.2rem);
  font-weight: 800;
  letter-spacing: -.045em;
  line-height: 1.1;
}

.header-description {
  max-width: 610px;
  margin-bottom: 0;
  color: #d7e3ef;
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

.site-header .eyebrow {
  color: #83e3d3;
}

.header-mark {
  display: grid;
  width: 88px;
  height: 88px;
  flex: 0 0 auto;
  place-items: center;
  border: 1px solid rgba(255,255,255,.25);
  border-radius: 26px;
  background: rgba(255,255,255,.1);
  color: #ffd28b;
  font-size: 3.3rem;
  font-weight: 800;
  transform: rotate(5deg);
  backdrop-filter: blur(8px);
}

/* Navegación */
.tabs {
  position: sticky;
  top: 12px;
  z-index: 5;
  display: flex;
  gap: 7px;
  margin: -25px auto 30px;
  padding: 7px;
  overflow-x: auto;
  border: 1px solid rgba(226, 232, 240, .9);
  border-radius: 15px;
  background: rgba(255, 255, 255, .92);
  box-shadow: var(--sombra);
  backdrop-filter: blur(12px);
}

.tab-button {
  position: relative;
  min-width: 120px;
  flex: 1;
  padding: 12px 17px;
  border: 0;
  border-radius: 10px;
  background: transparent;
  color: #607087;
  font-size: .93rem;
  font-weight: 750;
  cursor: pointer;
  transition: color .2s ease, background .2s ease, transform .2s ease;
}

.tab-button:hover {
  background: #f1f6fa;
  color: var(--azul);
}

.tab-button:active {
  transform: scale(.98);
}

.tab-button.active {
  background: var(--azul);
  color: white;
  box-shadow: 0 5px 14px rgba(31, 58, 95, .2);
}

.tab-button.active::after {
  position: absolute;
  right: 16px;
  bottom: 5px;
  left: 16px;
  height: 2px;
  border-radius: 5px;
  background: var(--ambar);
  content: "";
}

/* Secciones y títulos */
.panel {
  margin-bottom: 42px;
  animation: aparecer .35s ease both;
}

.section-heading {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 22px;
  margin: 28px 0 18px;
}

.section-heading h2 {
  margin-bottom: 6px;
  color: var(--azul);
  font-size: clamp(1.45rem, 3vw, 1.9rem);
  font-weight: 800;
  letter-spacing: -.035em;
}

.section-heading p:last-child {
  max-width: 760px;
  margin-bottom: 0;
  color: var(--muted);
}

.card {
  border: 1px solid rgba(226, 232, 240, .9);
  border-radius: var(--radio);
  background: var(--blanco);
  box-shadow: var(--sombra);
}

/* Formulario */
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
  font-size: .88rem;
  font-weight: 750;
}

input,
select {
  width: 100%;
  min-height: 46px;
  padding: 10px 13px;
  border: 1px solid #d5dee8;
  border-radius: 9px;
  outline: none;
  background-color: #fbfcfe;
  color: var(--texto);
  transition: border-color .2s ease, box-shadow .2s ease, background .2s ease;
}

input:hover,
select:hover {
  border-color: #aab9ca;
}

input:focus,
select:focus,
button:focus-visible {
  border-color: var(--verde);
  outline: 3px solid rgba(42, 157, 143, .18);
  outline-offset: 2px;
  background-color: #fff;
}

.form-actions {
  grid-column: 1 / -1;
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 11px;
  padding-top: 3px;
}

.form-message {
  color: #187a6f;
  font-size: .9rem;
  font-weight: 650;
}

.form-message.error {
  color: #b42318;
}

/* Botones */
.button {
  display: inline-flex;
  min-height: 42px;
  align-items: center;
  justify-content: center;
  gap: 7px;
  padding: 10px 15px;
  border: 1px solid transparent;
  border-radius: 9px;
  font-size: .88rem;
  font-weight: 750;
  text-align: center;
  text-decoration: none;
  cursor: pointer;
  transition: transform .18s ease, box-shadow .18s ease, background .18s ease, border-color .18s ease;
}

.button:hover {
  transform: translateY(-2px);
}

.button:active {
  transform: translateY(0);
}

.button-primary {
  background: linear-gradient(135deg, var(--verde), #238c80);
  color: white;
  box-shadow: 0 5px 12px rgba(42, 157, 143, .22);
}

.button-primary:hover {
  box-shadow: 0 8px 18px rgba(42, 157, 143, .3);
}

.button-secondary {
  border-color: var(--borde);
  background: white;
  color: var(--azul);
}

.button-secondary:hover {
  border-color: #b8c7d7;
  background: #f7fafc;
}

.button-danger {
  background: #b42318;
  color: white;
}

.hidden {
  display: none !important;
}

/* Herramientas y tabla de registros */
.list-heading {
  align-items: center;
  margin-top: 34px;
}

.list-heading h2 {
  margin-bottom: 4px;
  font-size: 1.35rem;
}

.toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.file-button {
  display: inline-flex;
  min-height: 42px;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  padding: 9px 13px;
  border: 1px solid var(--borde);
  border-radius: 9px;
  background: white;
  color: var(--azul);
  cursor: pointer;
  transition: background .2s ease, transform .2s ease;
}

.file-button:hover {
  transform: translateY(-2px);
  background: #f7fafc;
}

.table-wrap {
  overflow-x: auto;
}

table {
  width: 100%;
  border-collapse: separate;
  border-spacing: 0;
  font-size: .88rem;
}

th,
td {
  padding: 12px 14px;
  border-bottom: 1px solid #edf1f5;
  text-align: left;
  white-space: nowrap;
}

th {
  background: #f5f8fb;
  color: var(--azul);
  font-size: .77rem;
  font-weight: 800;
  letter-spacing: .035em;
  text-transform: uppercase;
}

th:first-child {
  border-top-left-radius: 12px;
}

th:last-child {
  border-top-right-radius: 12px;
}

tbody tr {
  transition: background .15s ease;
}

tbody tr:hover {
  background: #f7fbfa;
}

tbody tr:last-child td {
  border-bottom: 0;
}

.empty-state {
  padding: 26px 18px;
  color: var(--muted);
  text-align: center;
}

.row-actions {
  display: flex;
  gap: 6px;
}

.row-actions button {
  padding: 6px 9px;
  border: 1px solid var(--borde);
  border-radius: 7px;
  background: white;
  color: var(--azul);
  font-size: .8rem;
  font-weight: 700;
  cursor: pointer;
  transition: background .15s ease;
}

.row-actions button:hover {
  background: var(--verde-claro);
}

/* Tarjetas y resultados del análisis */
.metrics-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin: 18px 0 24px;
}

.metric-card {
  position: relative;
  overflow: hidden;
  padding: 20px;
  border: 1px solid var(--borde);
  border-radius: 14px;
  background: white;
  box-shadow: var(--sombra);
}

.metric-card::after {
  position: absolute;
  top: -19px;
  right: -15px;
  width: 72px;
  height: 72px;
  border-radius: 50%;
  background: rgba(42, 157, 143, .1);
  content: "";
}

.metric-card:nth-child(2)::after {
  background: rgba(233, 162, 59, .14);
}

.metric-card:nth-child(3)::after {
  background: rgba(49, 86, 129, .1);
}

.metric-card span {
  position: relative;
  z-index: 1;
  display: block;
  color: var(--muted);
  font-size: .84rem;
  font-weight: 650;
}

.metric-card strong {
  position: relative;
  z-index: 1;
  display: block;
  margin-top: 6px;
  color: var(--azul);
  font-size: clamp(1.35rem, 3vw, 1.75rem);
  font-weight: 850;
  letter-spacing: -.04em;
}

.analysis-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 17px;
}

.analysis-card {
  min-width: 0;
  padding: 20px;
  transition: transform .2s ease, box-shadow .2s ease;
}

.analysis-card:hover {
  transform: translateY(-3px);
  box-shadow: var(--sombra-hover);
}

.analysis-card h3,
.probability-card h3 {
  margin-bottom: 13px;
  color: var(--azul);
  font-size: 1.04rem;
  font-weight: 800;
}

.analysis-card p {
  color: var(--muted);
}

.compact-table {
  margin-top: 7px;
}

.compact-table th,
.compact-table td {
  padding: 9px 11px;
  white-space: normal;
}

.bar-list {
  display: grid;
  gap: 12px;
  margin-top: 16px;
}

.bar-row {
  display: grid;
  grid-template-columns: minmax(80px, 1fr) 2fr auto;
  align-items: center;
  gap: 10px;
  font-size: .85rem;
}

.bar-track {
  height: 12px;
  overflow: hidden;
  border-radius: 99px;
  background: #eaf0f4;
}

.bar-fill {
  height: 100%;
  border-radius: inherit;
  background: linear-gradient(90deg, var(--verde), #56c8b7);
  animation: crecer-barra .7s ease both;
}

.bar-value {
  min-width: 54px;
  color: var(--muted);
  font-size: .8rem;
  text-align: right;
}

.notice {
  padding: 17px 19px;
  border: 1px solid #f4d8a8;
  border-left: 5px solid var(--ambar);
  border-radius: 11px;
  background: #fff9ee;
  color: #654516;
}

/* Probabilidades e informe */
.probability-card {
  margin-bottom: 16px;
  padding: 20px;
  transition: transform .2s ease, box-shadow .2s ease;
}

.probability-card:hover {
  transform: translateY(-2px);
  box-shadow: var(--sombra-hover);
}

.probability-value {
  display: inline-flex;
  align-items: center;
  margin: 2px 0 11px;
  padding: 6px 12px;
  border-radius: 9px;
  background: var(--verde-claro);
  color: #167468;
  font-size: 1.25rem;
  font-weight: 850;
}

.interpretation {
  margin-bottom: 0;
  color: var(--muted);
}

.report-content {
  padding: clamp(20px, 4vw, 30px);
  line-height: 1.75;
}

.report-content h3 {
  margin-top: 25px;
  color: var(--azul);
}

.report-content h3:first-child {
  margin-top: 0;
}

.report-content li {
  margin-bottom: 8px;
  padding-left: 3px;
}

.report-heading {
  align-items: center;
}

.site-footer {
  padding: 22px 0 30px;
  color: var(--muted);
  font-size: .84rem;
  text-align: center;
}

.confirm-dialog {
  width: min(430px, calc(100% - 28px));
  padding: 22px;
  border: 1px solid var(--borde);
  border-radius: 16px;
  box-shadow: 0 18px 60px rgba(16, 35, 61, .25);
}

.confirm-dialog::backdrop {
  background: rgba(16, 35, 61, .55);
  backdrop-filter: blur(3px);
}

.confirm-dialog h2 {
  color: var(--azul);
}

.dialog-actions {
  display: flex;
  justify-content: flex-end;
  gap: 9px;
  margin-top: 20px;
}

@keyframes aparecer {
  from { opacity: 0; transform: translateY(8px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes crecer-barra {
  from { width: 0; }
}

/* Tabletas y celulares */
@media (max-width: 800px) {
  .form-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .analysis-grid {
    grid-template-columns: 1fr;
  }

  .section-heading,
  .list-heading {
    align-items: stretch;
    flex-direction: column;
  }

  .toolbar {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .toolbar .button,
  .toolbar .file-button {
    width: 100%;
  }

  .report-heading {
    align-items: flex-start;
  }
}

@media (max-width: 520px) {
  .container {
    width: min(100% - 24px, 1160px);
  }

  .site-header {
    padding: 29px 0 45px;
  }

  .header-mark {
    width: 60px;
    height: 60px;
    border-radius: 18px;
    font-size: 2.4rem;
  }

  .tabs {
    top: 7px;
    gap: 4px;
    margin-top: -20px;
  }

  .tab-button {
    min-width: 103px;
    padding: 11px 12px;
    font-size: .85rem;
  }

  .form-grid {
    grid-template-columns: 1fr;
    gap: 14px;
    padding: 17px;
  }

  .form-actions {
    align-items: stretch;
    flex-direction: column;
  }

  .form-actions .button {
    width: 100%;
  }

  .metrics-grid {
    grid-template-columns: 1fr;
    gap: 11px;
  }

  .metric-card {
    padding: 16px;
  }

  .bar-row {
    grid-template-columns: 76px 1fr auto;
    gap: 7px;
  }

  .analysis-card,
  .probability-card {
    padding: 16px;
  }

  .toolbar {
    gap: 7px;
  }
}

/* Respeta la configuración de accesibilidad del dispositivo */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    scroll-behavior: auto !important;
    animation-duration: .01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: .01ms !important;
  }
}

/* Versión limpia para impresión y PDF */
@media print {
  body {
    background: white;
    color: #111;
    font-size: 11pt;
  }

  .site-header,
  .tabs,
  #panel-registrar,
  #panel-analisis,
  #panel-probabilidad,
  .no-print,
  .site-footer {
    display: none !important;
  }

  main.container {
    width: 100%;
  }

  #panel-informe,
  #panel-informe[hidden] {
    display: block !important;
  }

  #panel-informe .section-heading {
    margin-top: 0;
  }

  .report-content {
    padding: 0;
    border: 0;
    box-shadow: none;
  }

  .card {
    box-shadow: none;
  }
}
