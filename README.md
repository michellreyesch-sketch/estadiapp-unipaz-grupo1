<!DOCTYPE html>
<html lang="es-CO">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>EstadíApp UNIPAZ</title>
<style>
/* ==========================================================
   1. VARIABLES Y ESTILOS BASE
   ========================================================== */
:root {
  --azul: #1F3A5F;
  --verde: #2A9D8F;
  --ambar: #E9A23B;
  --fondo: #F3F6FA;
  --blanco: #FFFFFF;
  --texto: #1d2733;
  --gris: #6b7785;
  --borde: #d5dde7;
  --error: #c0392b;
  --radio: 10px;
  --sombra: 0 2px 10px rgba(31, 58, 95, .10);
}
* { box-sizing: border-box; margin: 0; padding: 0; }
body {
  font-family: "Segoe UI", system-ui, -apple-system, Roboto, Arial, sans-serif;
  background: var(--fondo);
  color: var(--texto);
  line-height: 1.5;
}

/* ==========================================================
   2. ENCABEZADO Y PESTAÑAS
   ========================================================== */
header {
  background: linear-gradient(135deg, var(--azul), #2c5282);
  color: var(--blanco);
  padding: 18px 16px 0;
  border-bottom: 4px solid var(--ambar);
}
.header-in { max-width: 1100px; margin: 0 auto; }
header h1 { font-size: 1.6rem; letter-spacing: .3px; }
header h1 span { color: var(--ambar); }
header p { font-size: .9rem; opacity: .9; margin: 4px 0 14px; }

nav.tabs { display: flex; gap: 4px; overflow-x: auto; }
nav.tabs button {
  flex: 1 1 0;
  min-width: 110px;
  padding: 11px 14px;
  border: none;
  background: rgba(255,255,255,.12);
  color: var(--blanco);
  font-size: .95rem;
  font-weight: 600;
  cursor: pointer;
  border-radius: 8px 8px 0 0;
  transition: background .2s;
}
nav.tabs button:hover { background: rgba(255,255,255,.25); }
nav.tabs button.activa { background: var(--fondo); color: var(--azul); }

main { max-width: 1100px; margin: 0 auto; padding: 20px 14px 40px; }
.panel { display: none; }
.panel.activo { display: block; }

/* ==========================================================
   3. TARJETAS Y FORMULARIO
   ========================================================== */
.card {
  background: var(--blanco);
  border-radius: var(--radio);
  box-shadow: var(--sombra);
  padding: 20px;
  margin-bottom: 20px;
}
.card h2 {
  color: var(--azul);
  font-size: 1.2rem;
  margin-bottom: 4px;
  padding-left: 10px;
  border-left: 5px solid var(--verde);
}
.card .sub { color: var(--gris); font-size: .88rem; margin: 0 0 16px 15px; }

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(210px, 1fr));
  gap: 16px;
}
.campo { display: flex; flex-direction: column; }
.campo label, .campo .etq {
  font-weight: 600;
  font-size: .88rem;
  color: var(--azul);
  margin-bottom: 5px;
}
.campo small.tipo { color: var(--gris); font-weight: 400; }
input[type="date"], input[type="time"], input[type="number"], select {
  padding: 10px 12px;
  border: 1.5px solid var(--borde);
  border-radius: 8px;
  font-size: 1rem;
  background: var(--blanco);
  color: var(--texto);
  width: 100%;
}
input:focus, select:focus {
  outline: none;
  border-color: var(--verde);
  box-shadow: 0 0 0 3px rgba(42,157,143,.2);
}
select:disabled { background: #eef2f6; color: var(--gris); cursor: not-allowed; }
.campo.invalido input, .campo.invalido select { border-color: var(--error); }
.error-msg { color: var(--error); font-size: .8rem; min-height: 1.1em; margin-top: 3px; }

/* Franja horaria (solo lectura) */
.franja-box {
  padding: 10px 12px;
  border: 1.5px dashed var(--verde);
  border-radius: 8px;
  background: rgba(42,157,143,.08);
  color: var(--azul);
  font-weight: 600;
}

/* Satisfacción: botones tipo radio */
.escala { display: flex; gap: 8px; flex-wrap: wrap; }
.escala input { position: absolute; opacity: 0; pointer-events: none; }
.escala label {
  width: 46px; height: 46px;
  display: flex; align-items: center; justify-content: center;
  border: 1.5px solid var(--borde);
  border-radius: 50%;
  font-weight: 700;
  color: var(--azul);
  cursor: pointer;
  margin: 0;
  transition: all .15s;
}
.escala label:hover { border-color: var(--verde); }
.escala input:checked + label { background: var(--verde); border-color: var(--verde); color: #fff; }
.escala input:focus-visible + label { box-shadow: 0 0 0 3px rgba(42,157,143,.3); }
.escala-ref { font-size: .75rem; color: var(--gris); margin-top: 4px; }

/* Botones */
.acciones { display: flex; gap: 10px; margin-top: 20px; flex-wrap: wrap; }
.btn {
  padding: 11px 22px;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  transition: filter .2s, transform .05s;
}
.btn:active { transform: scale(.98); }
.btn:disabled { opacity: .55; cursor: not-allowed; }
.btn-primario { background: var(--verde); color: #fff; }
.btn-primario:hover { filter: brightness(1.08); }
.btn-sec { background: #e6ebf2; color: var(--azul); }
.btn-sec:hover { filter: brightness(.96); }
.btn-peligro { background: var(--error); color: #fff; }
.btn-ambar { background: var(--ambar); color: var(--azul); }
.btn-ambar:hover { filter: brightness(1.05); }
.btn-del {
  background: transparent; color: var(--error);
  border: 1.5px solid var(--error);
  padding: 5px 10px; font-size: .85rem; border-radius: 6px; font-weight: 600; cursor: pointer;
}
.btn-del:hover { background: var(--error); color: #fff; }

/* ==========================================================
   4. TABLA DE REGISTROS
   ========================================================== */
.tabla-cab {
  display: flex; justify-content: space-between; align-items: center;
  flex-wrap: wrap; gap: 10px; margin-bottom: 12px;
}
.contador {
  background: var(--ambar); color: var(--azul);
  font-weight: 800; padding: 6px 16px; border-radius: 20px;
}
.tabla-wrap { overflow-x: auto; }
table { width: 100%; border-collapse: collapse; font-size: .92rem; }
thead th {
  background: var(--azul); color: #fff; text-align: left;
  padding: 10px 8px; white-space: nowrap;
}
tbody td { padding: 9px 8px; border-bottom: 1px solid var(--borde); }
tbody tr:nth-child(even) { background: #f8fafc; }
tbody tr:hover { background: rgba(42,157,143,.08); }
.vacio { text-align: center; color: var(--gris); padding: 26px 10px; }
.etiqueta {
  display: inline-block; padding: 2px 9px; border-radius: 12px;
  background: rgba(233,162,59,.25); color: #7a4e07; font-size: .8rem; font-weight: 600;
}

/* Tabla tipo "tarjetas" en celulares */
@media (max-width: 720px) {
  table, thead, tbody, tr, td { display: block; }
  thead { display: none; }
  tbody tr {
    border: 1px solid var(--borde); border-radius: 10px;
    margin-bottom: 12px; padding: 6px 10px; background: #fff !important;
  }
  tbody td {
    display: flex; justify-content: space-between; gap: 12px;
    border-bottom: 1px dashed var(--borde); padding: 6px 0; text-align: right;
  }
  tbody td:last-child { border-bottom: none; justify-content: flex-end; }
  tbody td::before {
    content: attr(data-label); font-weight: 700; color: var(--azul); text-align: left;
  }
  .vacio { display: block; }
  .vacio::before { content: none !important; }
}

/* ==========================================================
   5. PESTAÑAS PREPARADAS (placeholders)
   ========================================================== */
.pendiente {
  border: 2px dashed var(--borde);
  border-radius: var(--radio);
  padding: 22px;
  text-align: center;
  color: var(--gris);
  background: #fbfcfe;
}
.pendiente strong { color: var(--azul); }
.chips { display: flex; flex-wrap: wrap; gap: 8px; justify-content: center; margin-top: 12px; }
.chip {
  background: rgba(31,58,95,.08); color: var(--azul);
  padding: 4px 12px; border-radius: 14px; font-size: .83rem;
}
.aviso-n {
  margin-top: 12px; font-size: .9rem; color: var(--azul);
  background: rgba(233,162,59,.18); padding: 8px 12px; border-radius: 8px; display: inline-block;
}

/* ==========================================================
   6. MODAL DE CONFIRMACIÓN Y TOAST
   ========================================================== */
dialog {
  border: none; border-radius: 12px; padding: 24px;
  max-width: 400px; width: 92%;
  box-shadow: 0 10px 40px rgba(0,0,0,.3);
  margin: auto;
}
dialog::backdrop { background: rgba(31,58,95,.55); }
dialog h3 { color: var(--azul); margin-bottom: 8px; }
dialog p { color: var(--gris); margin-bottom: 18px; font-size: .95rem; }
dialog .acciones { justify-content: flex-end; margin-top: 0; }

#toast {
  position: fixed; bottom: 20px; left: 50%;
  transform: translateX(-50%) translateY(80px);
  background: var(--azul); color: #fff;
  padding: 11px 22px; border-radius: 24px;
  border-left: 5px solid var(--ambar);
  opacity: 0; transition: all .3s; z-index: 50; max-width: 90%;
}
#toast.visible { transform: translateX(-50%) translateY(0); opacity: 1; }

footer { text-align: center; color: var(--gris); font-size: .8rem; padding: 0 12px 24px; }

/* ==========================================================
   7. HERRAMIENTAS DE DATOS (exportar, importar y respaldo)
   ========================================================== */
.datos-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 16px;
}
.datos-bloque {
  border: 1.5px solid var(--borde);
  border-radius: var(--radio);
  padding: 14px;
  background: #fbfcfe;
}
.datos-bloque h3 { color: var(--azul); font-size: 1rem; margin-bottom: 4px; }
.datos-bloque p { color: var(--gris); font-size: .83rem; margin-bottom: 10px; }
.datos-bloque .acciones { margin-top: 0; }
.datos-bloque .btn { padding: 9px 16px; font-size: .92rem; }

.msg {
  margin-top: 16px;
  padding: 12px 14px;
  border-radius: 8px;
  border-left: 5px solid var(--verde);
  background: rgba(42,157,143,.10);
  color: var(--texto);
  font-size: .92rem;
}
.msg[hidden] { display: none; }
.msg.warn { border-left-color: var(--ambar); background: rgba(233,162,59,.16); }
.msg.err  { border-left-color: var(--error); background: rgba(192,57,43,.09); }
.msg ul { margin: 6px 0 0 20px; }
.msg li { margin-bottom: 2px; }/* ==========================================================
   8. PESTAÑA ANÁLISIS
   ========================================================== */
.an-controles {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 16px;
  align-items: end;
}
.an-controles .btn { padding: 10px 16px; font-size: .92rem; }
.an-contexto {
  margin-bottom: 16px;
  padding: 10px 14px;
  background: rgba(31,58,95,.07);
  border-left: 5px solid var(--ambar);
  border-radius: 8px;
  color: var(--azul);
  font-size: .92rem;
}
.kpis {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 12px;
  margin-bottom: 8px;
}
.kpi {
  background: #fff;
  border: 1.5px solid var(--borde);
  border-top: 4px solid var(--verde);
  border-radius: 10px;
  padding: 10px 12px;
}
.kpi span { display: block; font-size: .78rem; color: var(--gris); }
.kpi b { font-size: 1.1rem; color: var(--azul); word-break: break-word; }
.an-sub { color: var(--azul); font-size: 1.05rem; margin: 22px 0 8px; }
.an-nota { color: var(--gris); font-size: .82rem; margin-top: 8px; }

.formula-lista {
  list-style: none;
  border: 1.5px solid var(--borde);
  border-radius: 10px;
  background: #fbfcfe;
  padding: 10px 14px;
  margin-bottom: 12px;
}
.formula-lista li { padding: 4px 0; font-size: .92rem; }
.formula-lista li + li { border-top: 1px dashed var(--borde); }
.fx { font-family: "Cambria Math", Cambria, "Times New Roman", serif; }
td.fx { font-size: .95rem; }
td.res { font-weight: 700; color: var(--azul); }
td.num { text-align: right; white-space: nowrap; }
tbody tr.total td { font-weight: 700; background: rgba(233,162,59,.18); }

.barras { margin-top: 14px; }
.barra-fila {
  display: grid;
  grid-template-columns: minmax(90px, 160px) 1fr minmax(90px, auto);
  gap: 10px;
  align-items: center;
  margin-bottom: 6px;
  font-size: .85rem;
}
.barra-etq { color: var(--azul); font-weight: 600; }
.barra-pista { background: #e6ebf2; border-radius: 6px; height: 18px; overflow: hidden; }
.barra-relleno { background: var(--verde); height: 100%; border-radius: 6px; min-width: 0; }
.barra-val { color: var(--gris); text-align: right; white-space: nowrap; }
@media (max-width: 720px) {
  .barra-fila { grid-template-columns: 90px 1fr; }
  .barra-val { grid-column: 1 / -1; text-align: left; margin-bottom: 4px; }
}

/* ==========================================================
   9. GRÁFICOS SVG Y LECTURA AUTOMÁTICA
   ========================================================== */
.grafico-wrap {
  margin-top: 12px;
  padding: 8px;
  background: #fff;
  border: 1.5px solid var(--borde);
  border-radius: 10px;
}
svg.grafico { display: block; width: 100%; max-width: 820px; height: auto; margin: 0 auto; }
.g-rej    { stroke: #e3e9f0; stroke-width: 1; }
.g-eje    { stroke: #1F3A5F; stroke-width: 1.5; }
.g-tick   { font-size: 11px; fill: #44546a; }
.g-cat    { font-size: 12px; font-weight: 600; fill: #1F3A5F; }
.g-titulo { font-size: 15px; font-weight: 700; fill: #1F3A5F; text-anchor: middle; }
.g-sub    { font-size: 12px; fill: #6b7785; text-anchor: middle; }
.g-eje-t  { font-size: 12px; font-weight: 600; fill: #1F3A5F; }
.g-leyenda{ font-size: 11.5px; fill: #44546a; }
.g-barra  { fill: #2A9D8F; fill-opacity: .8; stroke: #1F3A5F; stroke-width: 1; }
.g-poli   { fill: none; stroke: #E9A23B; stroke-width: 2.5; stroke-linejoin: round; stroke-linecap: round; }
.g-punto  { fill: #E9A23B; stroke: #fff; stroke-width: 1.5; }
.g-valor  { font-size: 11px; font-weight: 700; fill: #1F3A5F; }
.g-caja   { fill: rgba(42,157,143,.28); stroke: #1F3A5F; stroke-width: 2; }
.g-bigote { stroke: #1F3A5F; stroke-width: 2; }
.g-med    { stroke: #E9A23B; stroke-width: 4; }
.g-media  { fill: #1F3A5F; stroke: #fff; stroke-width: 1.5; }
.g-guia   { stroke: #8a97a8; stroke-width: 1; stroke-dasharray: 2 3; }
.g-etq    { font-size: 12px; font-weight: 700; fill: #1F3A5F; }

.lectura { list-style: none; margin-top: 6px; }
.lectura li {
  padding: 10px 14px;
  margin-bottom: 10px;
  background: #fbfcfe;
  border: 1.5px solid var(--borde);
  border-left: 5px solid var(--verde);
  border-radius: 8px;
  font-size: .93rem;
}
.lectura li small { display: block; color: var(--gris); margin-top: 4px; font-size: .8rem; }
.insignia {
  display: inline-block;
  padding: 2px 10px;
  margin-left: 6px;
  border-radius: 12px;
  font-size: .8rem;
  font-weight: 700;
}
.ins-verde { background: rgba(42,157,143,.2); color: #17695f; }
.ins-ambar { background: rgba(233,162,59,.28); color: #7a4e07; }
.ins-rojo  { background: rgba(192,57,43,.14); color: #8f2a1f; }
</style>
</head>
<body>

<!-- ==========================================================
     ENCABEZADO
     ========================================================== -->
<header>
  <div class="header-in">
    <h1>Estadí<span>App</span> UNIPAZ</h1>
    <p>Análisis estadístico de los tiempos de atención y características del servicio en las cafeterías de UNIPAZ</p>
    <nav class="tabs" role="tablist" aria-label="Secciones de la aplicación">
      <button role="tab" class="activa" data-tab="registrar">📝 Registrar</button>
      <button role="tab" data-tab="analisis">📊 Análisis</button>
      <button role="tab" data-tab="probabilidad">🎲 Probabilidad</button>
      <button role="tab" data-tab="informe">📄 Informe</button>
    </nav>
  </div>
</header>

<main>

  <!-- ========================================================
       PESTAÑA 1: REGISTRAR
       ======================================================== -->
  <section id="tab-registrar" class="panel activo">
    <div class="card">
      <h2>Nuevo registro</h2>
      <p class="sub">Completa todos los campos. La fecha y la hora se cargan automáticamente, pero puedes editarlas.</p>

      <form id="formulario" novalidate>
        <div class="grid">

          <div class="campo" id="c-fecha">
            <label for="fecha">Fecha</label>
            <input type="date" id="fecha">
            <span class="error-msg"></span>
          </div>

          <div class="campo" id="c-hora">
            <label for="hora">Hora</label>
            <input type="time" id="hora">
            <span class="error-msg"></span>
          </div>

          <div class="campo">
            <span class="etq">Franja horaria <small class="tipo">(automática)</small></span>
            <div class="franja-box" id="franja">—</div>
          </div>

          <div class="campo" id="c-cafeteria">
            <label for="cafeteria">Cafetería <small class="tipo">(cualitativa nominal)</small></label>
            <select id="cafeteria">
              <option value="">Selecciona una opción</option>
              <option>Cafetería 1</option>
              <option>Cafetería 2</option>
              <option>Cafetería 3</option>
            </select>
            <span class="error-msg"></span>
          </div>

          <div class="campo" id="c-tiempo">
            <label for="tiempo">Tiempo en fila (min) <small class="tipo">(cuantitativa continua)</small></label>
            <input type="number" id="tiempo" step="any" min="0" placeholder="Ej.: 4.5" inputmode="decimal">
            <span class="error-msg"></span>
          </div>

          <div class="campo" id="c-valor">
            <label for="valor">Valor de compra ($ COP) <small class="tipo">(cuantitativa numérica)</small></label>
            <input type="number" id="valor" step="1" min="0" placeholder="Ej.: 8500" inputmode="numeric">
            <span class="error-msg"></span>
          </div>

          <div class="campo" id="c-producto">
            <label for="producto">Producto principal <small class="tipo">(cualitativa nominal)</small></label>
            <select id="producto">
              <option value="">Selecciona una opción</option>
              <option>Almuerzo</option>
              <option>Desayuno</option>
              <option>Fritos</option>
              <option>Bebida</option>
              <option>Snack</option>
            </select>
            <span class="error-msg"></span>
          </div>

          <div class="campo" id="c-satisfaccion">
            <span class="etq">Satisfacción <small class="tipo">(cualitativa ordinal)</small></span>
            <div class="escala" role="radiogroup" aria-label="Satisfacción de 1 a 5">
              <input type="radio" name="satisfaccion" id="s1" value="1"><label for="s1">1</label>
              <input type="radio" name="satisfaccion" id="s2" value="2"><label for="s2">2</label>
              <input type="radio" name="satisfaccion" id="s3" value="3"><label for="s3">3</label>
              <input type="radio" name="satisfaccion" id="s4" value="4"><label for="s4">4</label>
              <input type="radio" name="satisfaccion" id="s5" value="5"><label for="s5">5</label>
            </div>
            <span class="escala-ref">1 = Muy insatisfecho · 5 = Muy satisfecho</span>
            <span class="error-msg"></span>
          </div>

        </div>

        <div class="acciones">
          <button type="submit" class="btn btn-primario">💾 Guardar registro</button>
          <button type="button" class="btn btn-sec" id="btn-limpiar">Limpiar formulario</button>
        </div>
      </form>
    </div>

    <!-- ======================================================
         HERRAMIENTAS DE DATOS: CSV Y RESPALDO JSON
         ====================================================== -->
    <div class="card">
      <h2>Exportar, importar y respaldo</h2>
      <p class="sub">Lleva tus datos a Excel, únelos con los de otros compañeros o guarda una copia de seguridad.</p>

      <div class="datos-grid">
        <div class="datos-bloque">
          <h3>📤 Excel (CSV)</h3>
          <p>Separador «;», coma decimal y codificación UTF-8 con BOM, listo para Excel en español. Al importar, los registros se agregan a los actuales y los repetidos se omiten.</p>
          <div class="acciones">
            <button type="button" class="btn btn-primario" id="btn-exportar-csv">Exportar CSV</button>
            <button type="button" class="btn btn-sec" id="btn-importar-csv">Importar CSV</button>
          </div>
        </div>

        <div class="datos-bloque">
          <h3>🛟 Respaldo (JSON)</h3>
          <p>Descarga todos los registros en un archivo y restáuralos cuando quieras. Podrás combinarlos con los actuales o reemplazarlos.</p>
          <div class="acciones">
            <button type="button" class="btn btn-ambar" id="btn-exportar-json">Descargar respaldo</button>
            <button type="button" class="btn btn-sec" id="btn-importar-json">Restaurar respaldo</button>
          </div>
        </div>
      </div>

      <!-- Selectores de archivo ocultos -->
      <input type="file" id="file-csv" accept=".csv,text/csv" hidden>
      <input type="file" id="file-json" accept=".json,application/json" hidden>

      <!-- Resultado de la última operación -->
      <div id="msg-datos" class="msg" role="status" aria-live="polite" hidden></div>
    </div>

    <div class="card">
      <div class="tabla-cab">
        <div>
          <h2>Registros guardados</h2>
          <p class="sub" style="margin-bottom:0">Se guardan automáticamente en este dispositivo.</p>
        </div>
        <div class="contador">Total: <span id="total">0</span></div>
      </div>

      <div class="tabla-wrap">
        <table>
          <thead>
            <tr>
              <th>N.º</th><th>Fecha</th><th>Hora</th><th>Franja</th><th>Cafetería</th>
              <th>Tiempo (min)</th><th>Valor ($)</th><th>Producto</th><th>Satisf.</th><th>Acción</th>
            </tr>
          </thead>
          <tbody id="tbody"></tbody>
        </table>
      </div>
    </div>
  </section>

  <!-- ========================================================
       PESTAÑA 2: ANÁLISIS
       ======================================================== -->
  <section id="tab-analisis" class="panel">
    <div class="card">
      <h2>Análisis estadístico descriptivo</h2>
      <p class="sub">Elige una variable y, si quieres, filtra por una variable cualitativa. Registros totales: <b class="n-registros">0</b></p>

      <div class="an-controles">
        <div class="campo">
          <label for="an-variable">Variable a analizar</label>
          <select id="an-variable">
            <optgroup label="Cuantitativas">
              <option value="tiempo" selected>Tiempo en fila (min)</option>
              <option value="valor">Valor de compra ($)</option>
            </optgroup>
            <optgroup label="Cualitativas">
              <option value="cafeteria">Cafetería</option>
              <option value="producto">Producto principal</option>
              <option value="satisfaccion">Satisfacción</option>
              <option value="franja">Franja horaria</option>
            </optgroup>
          </select>
        </div>

        <div class="campo">
          <label for="an-filtro-var">Filtrar por (opcional)</label>
          <select id="an-filtro-var"></select>
        </div>

        <div class="campo">
          <label for="an-filtro-val">Valor del filtro</label>
          <select id="an-filtro-val" disabled></select>
        </div>

        <div class="campo">
          <button type="button" class="btn btn-sec" id="an-quitar-filtro">Quitar filtro</button>
        </div>
      </div>
    </div>

    <div class="card">
      <div id="an-resultado" aria-live="polite"></div>
    </div>
  </section>

  <!-- ========================================================
       PESTAÑA 3: PROBABILIDAD (preparada)
       ======================================================== -->
  <section id="tab-probabilidad" class="panel">
    <div class="card">
      <h2>Probabilidad</h2>
      <p class="sub">Sección preparada para su programación.</p>
      <div class="pendiente" id="probabilidad-contenido">
        <p><strong>Próximamente:</strong> aquí se calcularán probabilidades con los datos recolectados.</p>
        <div class="chips">
          <span class="chip">Probabilidad empírica</span>
          <span class="chip">Probabilidad condicional</span>
          <span class="chip">Tablas de contingencia</span>
          <span class="chip">Distribución normal</span>
          <span class="chip">Eventos independientes</span>
        </div>
        <div class="aviso-n">Registros disponibles: <b class="n-registros">0</b></div>
      </div>
    </div>
  </section>

  <!-- ========================================================
       PESTAÑA 4: INFORME (preparada)
       ======================================================== -->
  <section id="tab-informe" class="panel">
    <div class="card">
      <h2>Informe final</h2>
      <p class="sub">Sección preparada para su programación.</p>
      <div class="pendiente" id="informe-contenido">
        <p><strong>Próximamente:</strong> aquí se generará el informe del estudio.</p>
        <div class="chips">
          <span class="chip">Resumen de resultados</span>
          <span class="chip">Conclusiones</span>
          <span class="chip">Recomendaciones</span>
          <span class="chip">Impresión / PDF</span>
        </div>
        <div class="aviso-n">Registros disponibles: <b class="n-registros">0</b></div>
      </div>
    </div>
  </section>

</main>

<footer>EstadíApp UNIPAZ · Estudio estadístico educativo · Los datos se almacenan solo en tu navegador.</footer>

<!-- Modal de confirmación para eliminar -->
<dialog id="modal">
  <h3>¿Eliminar registro?</h3>
  <p id="modal-texto">Esta acción no se puede deshacer.</p>
  <div class="acciones">
    <button class="btn btn-sec" id="modal-cancelar">Cancelar</button>
    <button class="btn btn-peligro" id="modal-ok">Sí, eliminar</button>
  </div>
</dialog>

<!-- Modal para restaurar un respaldo JSON -->
<dialog id="modal-restaurar">
  <h3>Restaurar respaldo</h3>
  <p id="restaurar-texto"></p>
  <div class="acciones">
    <button class="btn btn-sec" id="restaurar-cancelar">Cancelar</button>
    <button class="btn btn-peligro" id="restaurar-reemplazar">Reemplazar todo</button>
    <button class="btn btn-primario" id="restaurar-unir">Combinar (recomendado)</button>
  </div>
</dialog>

<!-- Mensaje flotante -->
<div id="toast" role="status" aria-live="polite"></div>

<script>
/* ==========================================================
   EstadíApp UNIPAZ - Lógica de la aplicación
   ========================================================== */
(function () {
  "use strict";

  /* ---------- 1. CONSTANTES Y ESTADO ---------- */
  const CLAVE_STORAGE = "estadiapp_unipaz_registros";
  const CAFETERIAS = ["Cafetería 1", "Cafetería 2", "Cafetería 3"];
  const PRODUCTOS = ["Almuerzo", "Desayuno", "Fritos", "Bebida", "Snack"];
  const TIEMPO_MAX = 180;        // minutos (límite razonable)
  const VALOR_MAX = 500000;      // pesos (límite razonable)

  let registros = [];            // arreglo principal de datos
  let idPendienteEliminar = null;

  /* ---------- 2. REFERENCIAS AL DOM ---------- */
  const $ = (id) => document.getElementById(id);
  const form = $("formulario");
  const tbody = $("tbody");
  const modal = $("modal");

  /* ---------- 3. UTILIDADES ---------- */

  /** Convierte un número a formato de pesos colombianos. */
  const formatoPesos = (n) =>
    n.toLocaleString("es-CO", { style: "currency", currency: "COP", maximumFractionDigits: 0 });

  /** Rellena con cero a la izquierda. */
  const dos = (n) => String(n).padStart(2, "0");

  /** Devuelve la fecha actual como AAAA-MM-DD (hora local). */
  function fechaActual() {
    const d = new Date();
    return `${d.getFullYear()}-${dos(d.getMonth() + 1)}-${dos(d.getDate())}`;
  }

  /** Devuelve la hora actual como HH:MM (hora local). */
  function horaActual() {
    const d = new Date();
    return `${dos(d.getHours())}:${dos(d.getMinutes())}`;
  }

  /** Calcula la franja horaria a partir de "HH:MM". */
  function calcularFranja(hora) {
    if (!/^\d{2}:\d{2}$/.test(hora || "")) return "—";
    const h = parseInt(hora.split(":")[0], 10);
    if (h >= 5 && h < 12) return "Mañana (5:00 a. m. – 11:59 a. m.)";
    if (h >= 12 && h < 15) return "Mediodía (12:00 m. – 2:59 p. m.)";
    if (h >= 15 && h < 19) return "Tarde (3:00 p. m. – 6:59 p. m.)";
    return "Noche (7:00 p. m. – 4:59 a. m.)";
  }

  /** Versión corta de la franja para guardar y mostrar en la tabla. */
  const franjaCorta = (hora) => calcularFranja(hora).split(" (")[0];

  /** Formatea AAAA-MM-DD como DD/MM/AAAA. */
  function fechaBonita(f) {
    const [a, m, d] = f.split("-");
    return `${d}/${m}/${a}`;
  }

  /** Muestra un mensaje flotante temporal. */
  let temporizadorToast;
  function avisar(texto) {
    const t = $("toast");
    t.textContent = texto;
    t.classList.add("visible");
    clearTimeout(temporizadorToast);
    temporizadorToast = setTimeout(() => t.classList.remove("visible"), 2800);
  }

  /** Escapa texto para insertarlo de forma segura en HTML. */
  function esc(s) {
    return String(s).replace(/[&<>"']/g, (c) =>
      ({ "&": "&amp;", "<": "&lt;", ">": "&gt;", '"': "&quot;", "'": "&#39;" }[c]));
  }

  /* ---------- 4. ALMACENAMIENTO (localStorage) ---------- */

  function cargarRegistros() {
    try {
      const datos = JSON.parse(localStorage.getItem(CLAVE_STORAGE));
      registros = Array.isArray(datos) ? datos : [];
    } catch (e) {
      registros = [];
    }
  }

  function guardarRegistros() {
    try {
      localStorage.setItem(CLAVE_STORAGE, JSON.stringify(registros));
    } catch (e) {
      avisar("⚠️ No se pudo guardar en el navegador (almacenamiento lleno o bloqueado).");
    }
  }

  /* ---------- 5. PESTAÑAS ---------- */

  function activarPestana(nombre) {
    document.querySelectorAll("nav.tabs button").forEach((b) =>
      b.classList.toggle("activa", b.dataset.tab === nombre));
    document.querySelectorAll(".panel").forEach((p) =>
      p.classList.toggle("activo", p.id === "tab-" + nombre));
    window.scrollTo({ top: 0, behavior: "smooth" });
  }

  document.querySelectorAll("nav.tabs button").forEach((b) =>
    b.addEventListener("click", () => activarPestana(b.dataset.tab)));

  /* ---------- 6. VALIDACIÓN ---------- */

  /** Marca u oculta el error de un campo. */
  function marcarError(idContenedor, mensaje) {
    const c = $(idContenedor);
    c.classList.toggle("invalido", !!mensaje);
    c.querySelector(".error-msg").textContent = mensaje || "";
  }

  /** Valida todos los campos. Devuelve el objeto limpio o null si hay errores. */
  function validar() {
    let ok = true;
    const fallo = (id, msg) => { marcarError(id, msg); ok = false; };

    // Fecha
    const fecha = $("fecha").value;
    if (!fecha) fallo("c-fecha", "Ingresa la fecha.");
    else if (fecha > fechaActual()) fallo("c-fecha", "La fecha no puede ser futura.");
    else if (fecha < "2000-01-01") fallo("c-fecha", "La fecha no es válida.");
    else marcarError("c-fecha", "");

    // Hora
    const hora = $("hora").value;
    if (!hora) fallo("c-hora", "Ingresa la hora.");
    else if (fecha === fechaActual() && hora > horaActual())
      fallo("c-hora", "La hora no puede ser futura.");
    else marcarError("c-hora", "");

    // Cafetería
    const cafeteria = $("cafeteria").value;
    if (!CAFETERIAS.includes(cafeteria)) fallo("c-cafeteria", "Selecciona una cafetería.");
    else marcarError("c-cafeteria", "");

    // Tiempo en fila (decimales permitidos)
    const tiempoTxt = $("tiempo").value.trim();
    const tiempo = parseFloat(tiempoTxt);
    if (tiempoTxt === "" || isNaN(tiempo)) fallo("c-tiempo", "Ingresa el tiempo en fila.");
    else if (tiempo < 0) fallo("c-tiempo", "El tiempo no puede ser negativo.");
    else if (tiempo > TIEMPO_MAX) fallo("c-tiempo", `El tiempo no puede superar ${TIEMPO_MAX} minutos.`);
    else marcarError("c-tiempo", "");

    // Valor de compra (entero positivo en pesos)
    const valorTxt = $("valor").value.trim();
    const valor = Number(valorTxt);
    if (valorTxt === "" || isNaN(valor)) fallo("c-valor", "Ingresa el valor de la compra.");
    else if (valor <= 0) fallo("c-valor", "El valor debe ser mayor que cero.");
    else if (!Number.isInteger(valor)) fallo("c-valor", "Ingresa el valor en pesos enteros, sin decimales.");
    else if (valor > VALOR_MAX) fallo("c-valor", `El valor no puede superar ${formatoPesos(VALOR_MAX)}.`);
    else marcarError("c-valor", "");

    // Producto
    const producto = $("producto").value;
    if (!PRODUCTOS.includes(producto)) fallo("c-producto", "Selecciona un producto.");
    else marcarError("c-producto", "");

    // Satisfacción
    const sel = form.querySelector('input[name="satisfaccion"]:checked');
    if (!sel) fallo("c-satisfaccion", "Selecciona un nivel de satisfacción.");
    else marcarError("c-satisfaccion", "");

    if (!ok) return null;

    return {
      id: Date.now().toString(36) + Math.random().toString(36).slice(2, 7),
      fecha,
      hora,
      franja: franjaCorta(hora),
      cafeteria,
      tiempo,
      valor,
      producto,
      satisfaccion: parseInt(sel.value, 10)
    };
  }

  /* ---------- 7. FORMULARIO ---------- */

  /** Restablece el formulario con fecha y hora actuales. */
  function reiniciarFormulario() {
    form.reset();
    $("fecha").value = fechaActual();
    $("hora").value = horaActual();
    $("franja").textContent = calcularFranja($("hora").value);
    ["c-fecha", "c-hora", "c-cafeteria", "c-tiempo", "c-valor", "c-producto", "c-satisfaccion"]
      .forEach((id) => marcarError(id, ""));
  }

  // La franja se actualiza al cambiar la hora
  $("hora").addEventListener("input", () => {
    $("franja").textContent = calcularFranja($("hora").value);
  });

  form.addEventListener("submit", (e) => {
    e.preventDefault();
    const nuevo = validar();
    if (!nuevo) {
      avisar("⚠️ Revisa los campos marcados en rojo.");
      return;
    }
    registros.push(nuevo);
    guardarRegistros();
    renderizar();
    reiniciarFormulario();
    avisar(`✅ Registro N.º ${registros.length} guardado correctamente.`);
  });

  $("btn-limpiar").addEventListener("click", reiniciarFormulario);

  /* ---------- 8. TABLA ---------- */

  function renderizar() {
    $("total").textContent = registros.length;
    document.querySelectorAll(".n-registros").forEach((el) => (el.textContent = registros.length));

    if (registros.length === 0) {
      tbody.innerHTML = '<tr><td colspan="10" class="vacio">Aún no hay registros. Completa el formulario para agregar el primero.</td></tr>';
      return;
    }

    // Numeración según el orden de registro; se muestran primero los más recientes
    const filas = registros.map((r, i) => `
      <tr>
        <td data-label="N.º"><b>${i + 1}</b></td>
        <td data-label="Fecha">${fechaBonita(r.fecha)}</td>
        <td data-label="Hora">${esc(r.hora)}</td>
        <td data-label="Franja"><span class="etiqueta">${esc(r.franja)}</span></td>
        <td data-label="Cafetería">${esc(r.cafeteria)}</td>
        <td data-label="Tiempo (min)">${r.tiempo.toLocaleString("es-CO")}</td>
        <td data-label="Valor ($)">${formatoPesos(r.valor)}</td>
        <td data-label="Producto">${esc(r.producto)}</td>
        <td data-label="Satisf.">${"★".repeat(r.satisfaccion)} (${r.satisfaccion})</td>
        <td data-label="Acción"><button class="btn-del" data-id="${r.id}" data-n="${i + 1}">Eliminar</button></td>
      </tr>`);
    tbody.innerHTML = filas.reverse().join("");
  }

  /* ---------- 9. ELIMINAR CON CONFIRMACIÓN ---------- */

  tbody.addEventListener("click", (e) => {
    const btn = e.target.closest(".btn-del");
    if (!btn) return;
    idPendienteEliminar = btn.dataset.id;
    $("modal-texto").textContent =
      `Se eliminará el registro N.º ${btn.dataset.n}. Esta acción no se puede deshacer.`;
    modal.showModal();
  });

  $("modal-cancelar").addEventListener("click", () => {
    idPendienteEliminar = null;
    modal.close();
  });

  $("modal-ok").addEventListener("click", () => {
    if (idPendienteEliminar) {
      registros = registros.filter((r) => r.id !== idPendienteEliminar);
      guardarRegistros();
      renderizar();
      avisar("🗑️ Registro eliminado.");
    }
    idPendienteEliminar = null;
    modal.close();
  });

  // Cerrar el modal al hacer clic fuera de él
  modal.addEventListener("click", (e) => {
    if (e.target === modal) { idPendienteEliminar = null; modal.close(); }
  });

  /* ==========================================================
     EXPORTAR / IMPORTAR CSV Y RESPALDO JSON
     ========================================================== */

  /* ---------- 10. CONSTANTES Y UTILIDADES DE DATOS ---------- */

  // Columnas del CSV, en el orden en que se exportan
  const ENCABEZADOS_CSV = [
    "Fecha", "Hora", "Franja horaria", "Cafetería",
    "Tiempo en fila (min)", "Valor de compra ($)", "Producto principal", "Satisfacción"
  ];
  const APP_NOMBRE = "EstadíApp UNIPAZ";   // identifica los respaldos JSON propios
  const VERSION_RESPALDO = 1;
  const MAX_ARCHIVO_BYTES = 5 * 1024 * 1024; // 5 MB
  const MAX_REGISTROS_IMPORTAR = 20000;

  let ocupado = false;          // evita procesar dos importaciones a la vez  let jsonPendiente = null;     // registros validados a la espera de la decisión del usuario

  /** Minúsculas, sin tildes y sin espacios sobrantes (para comparar textos). */
  const sinAcentos = (s) =>
    String(s).normalize("NFD").replace(/[\u0300-\u036f]/g, "")
      .replace(/\s+/g, " ").trim().toLowerCase();

  const ENCABEZADOS_NORM = ENCABEZADOS_CSV.map(sinAcentos);

  /** Genera un identificador único para un registro. */
  const nuevoId = () => Date.now().toString(36) + Math.random().toString(36).slice(2, 7);

  /** Firma de un registro: sirve para detectar duplicados al unir datos. */
  const firma = (r) =>
    [r.fecha, r.hora, r.cafeteria, r.tiempo, r.valor, r.producto, r.satisfaccion].join("|");

  /** Muestra el resultado de la última operación debajo de los botones. */
  function mostrarMensaje(tipo, titulo, lineas) {
    const box = $("msg-datos");
    box.className = "msg " + tipo;
    box.innerHTML = `<b>${esc(titulo)}</b>` +
      (lineas && lineas.length ? "<ul>" + lineas.map((l) => `<li>${esc(l)}</li>`).join("") + "</ul>" : "");
    box.hidden = false;
  }

  /** Descarga un archivo de texto generado en el navegador. */
  function descargarArchivo(nombre, contenido, tipoMime) {
    const blob = new Blob([contenido], { type: tipoMime });
    const url = URL.createObjectURL(blob);
    const a = document.createElement("a");
    a.href = url;
    a.download = nombre;
    document.body.appendChild(a);
    a.click();
    a.remove();
    setTimeout(() => URL.revokeObjectURL(url), 1000);
  }

  /** Lee un archivo como texto: UTF-8 y, si falla, Windows-1252 (CSV guardado desde Excel). */
  async function leerArchivoTexto(archivo) {
    const buffer = await archivo.arrayBuffer();
    let texto;
    try {
      texto = new TextDecoder("utf-8", { fatal: true }).decode(buffer);
    } catch (e) {
      texto = new TextDecoder("windows-1252").decode(buffer);
    }
    return texto.replace(/^\uFEFF/, ""); // quita el BOM si quedó
  }

  /** Verifica el tamaño del archivo. Devuelve un mensaje de error o null. */
  function revisarArchivo(archivo) {
    if (archivo.size === 0) return "El archivo está vacío.";
    if (archivo.size > MAX_ARCHIVO_BYTES) return "El archivo supera el tamaño máximo permitido (5 MB).";
    return null;
  }

  /* ---------- 11. NORMALIZACIÓN Y VALIDACIÓN DE REGISTROS IMPORTADOS ---------- */

  /** Convierte AAAA-MM-DD o DD/MM/AAAA en AAAA-MM-DD. Devuelve null si no es válida. */
  function parsearFecha(v) {
    if (typeof v !== "string") return null;
    const t = v.trim();
    let a, m, d, r;
    if ((r = /^(\d{4})-(\d{1,2})-(\d{1,2})$/.exec(t))) { a = +r[1]; m = +r[2]; d = +r[3]; }
    else if ((r = /^(\d{1,2})\/(\d{1,2})\/(\d{4})$/.exec(t))) { d = +r[1]; m = +r[2]; a = +r[3]; }
    else return null;
    const f = new Date(a, m - 1, d);
    if (f.getFullYear() !== a || f.getMonth() !== m - 1 || f.getDate() !== d) return null;
    return `${a}-${dos(m)}-${dos(d)}`;
  }

  /** Convierte H:MM, HH:MM o HH:MM:SS en HH:MM. Devuelve null si no es válida. */
  function parsearHora(v) {
    if (typeof v !== "string") return null;
    const r = /^(\d{1,2}):(\d{2})(?::\d{2})?$/.exec(v.trim());
    if (!r) return null;
    const h = +r[1], m = +r[2];
    if (h > 23 || m > 59) return null;
    return `${dos(h)}:${dos(m)}`;
  }

  /** Convierte texto con coma o punto decimal (o un número) en Number. NaN si no es válido. */
  function aNumero(v) {
    if (typeof v === "number") return Number.isFinite(v) ? v : NaN;
    if (typeof v !== "string") return NaN;
    const t = v.trim().replace(/\s/g, "");
    if (!/^\d+([.,]\d+)?$/.test(t)) return NaN;
    return parseFloat(t.replace(",", "."));
  }

  /**
   * Valida un registro "crudo" con las mismas reglas del formulario.
   * Devuelve { registro } si es válido o { error } con el motivo.
   * La franja horaria no se toma del archivo: siempre se recalcula desde la hora.
   */
  function normalizarRegistro(c) {
    if (!c || typeof c !== "object") return { error: "no es un registro válido" };

    const fecha = parsearFecha(c.fecha);
    if (!fecha) return { error: "fecha no válida (use AAAA-MM-DD o DD/MM/AAAA)" };
    if (fecha < "2000-01-01") return { error: "la fecha es anterior al año 2000" };
    if (fecha > fechaActual()) return { error: "la fecha no puede ser futura" };

    const hora = parsearHora(c.hora);
    if (!hora) return { error: "hora no válida (use HH:MM)" };
    if (fecha === fechaActual() && hora > horaActual()) return { error: "la hora no puede ser futura" };

    const cafeteria = typeof c.cafeteria === "string"
      ? CAFETERIAS.find((x) => sinAcentos(x) === sinAcentos(c.cafeteria)) : null;
    if (!cafeteria) return { error: "cafetería no válida (use Cafetería 1, 2 o 3)" };

    const tiempo = aNumero(c.tiempo);
    if (isNaN(tiempo)) return { error: "tiempo en fila no es un número válido" };
    if (tiempo > TIEMPO_MAX) return { error: `el tiempo en fila supera ${TIEMPO_MAX} minutos` };

    const valor = aNumero(c.valor);
    if (isNaN(valor)) return { error: "valor de compra no es un número válido" };
    if (!Number.isInteger(valor)) return { error: "el valor de compra debe ser en pesos enteros" };
    if (valor <= 0) return { error: "el valor de compra debe ser mayor que cero" };
    if (valor > VALOR_MAX) return { error: `el valor de compra supera ${formatoPesos(VALOR_MAX)}` };

    const producto = typeof c.producto === "string"
      ? PRODUCTOS.find((x) => sinAcentos(x) === sinAcentos(c.producto)) : null;
    if (!producto) return { error: "producto no válido" };

    const satisfaccion = aNumero(c.satisfaccion);
    if (!Number.isInteger(satisfaccion) || satisfaccion < 1 || satisfaccion > 5)
      return { error: "satisfacción debe ser un entero de 1 a 5" };

    return {
      registro: {
        id: nuevoId(), fecha, hora, franja: franjaCorta(hora),
        cafeteria, tiempo, valor, producto, satisfaccion
      }
    };
  }

  /* ---------- 12. UNIÓN SIN DUPLICADOS ---------- */

  /**
   * Separa los candidatos en nuevos y duplicados SIN modificar los datos actuales.
   * Un candidato es duplicado si ya existe un registro idéntico (se cuentan las
   * repeticiones, así dos registros idénticos legítimos no se pierden).
   */
  function particionar(candidatos) {
    const conteo = new Map();
    registros.forEach((r) => {
      const k = firma(r);
      conteo.set(k, (conteo.get(k) || 0) + 1);
    });
    const nuevos = [];
    let duplicados = 0;
    candidatos.forEach((r) => {
      const k = firma(r);
      const n = conteo.get(k) || 0;
      if (n > 0) { conteo.set(k, n - 1); duplicados++; }
      else nuevos.push(r);
    });
    return { nuevos, duplicados };
  }

  /** Agrega los candidatos a los registros existentes. Devuelve { agregados, duplicados }. */
  function unirRegistros(candidatos) {
    const { nuevos, duplicados } = particionar(candidatos);
    if (nuevos.length) {
      registros = registros.concat(nuevos);
      guardarRegistros();
      renderizar();
    }
    return { agregados: nuevos.length, duplicados };
  }

  /* ---------- 13. EXPORTAR / IMPORTAR CSV ---------- */

  /** Escapa una celda según las reglas del CSV (separador ;). */
  function celdaCSV(v) {
    const s = String(v);
    return /[;"\r\n]/.test(s) ? '"' + s.replace(/"/g, '""') + '"' : s;
  }

  /** Exporta los registros a CSV compatible con Excel en español. */
  function exportarCSV() {
    if (!registros.length) { avisar("⚠️ No hay registros para exportar."); return; }

    const lineas = [ENCABEZADOS_CSV.map(celdaCSV).join(";")];
    registros.forEach((r) => {
      lineas.push([
        r.fecha,
        r.hora,
        r.franja,
        r.cafeteria,
        String(r.tiempo).replace(".", ","),   // coma decimal
        r.valor,
        r.producto,
        r.satisfaccion
      ].map(celdaCSV).join(";"));
    });

    // "\uFEFF" = BOM UTF-8, para que Excel muestre bien las tildes y la ñ
    const contenido = "\uFEFF" + lineas.join("\r\n") + "\r\n";
    const nombre = `estadiapp_unipaz_registros_${fechaActual()}.csv`;
    descargarArchivo(nombre, contenido, "text/csv;charset=utf-8;");
    mostrarMensaje("ok", `CSV exportado: ${registros.length} registros.`,
      [`Archivo: ${nombre}`, "Formato: separador «;», coma decimal, UTF-8 con BOM."]);
    avisar("📤 CSV exportado.");
  }

  /**
   * Analiza un texto CSV. Devuelve filas { n, celdas } donde n es el número de fila del archivo.
   * Soporta comillas, comillas dobles escapadas y saltos de línea dentro de celdas.
   */
  function parsearCSV(texto, sep) {
    const filas = [];
    let fila = [], campo = "", entreComillas = false;
    const cerrarFila = () => {
      fila.push(campo);
      filas.push({ n: filas.length + 1, celdas: fila });
      fila = []; campo = "";
    };
    for (let i = 0; i < texto.length; i++) {
      const c = texto[i];
      if (entreComillas) {
        if (c === '"') {
          if (texto[i + 1] === '"') { campo += '"'; i++; }
          else entreComillas = false;
        } else campo += c;
      } else if (c === '"') {
        entreComillas = true;
      } else if (c === sep) {
        fila.push(campo); campo = "";
      } else if (c === "\n" || c === "\r") {
        if (c === "\r" && texto[i + 1] === "\n") i++;
        cerrarFila();
      } else {
        campo += c;
      }
    }
    if (campo !== "" || fila.length) cerrarFila();
    // Descarta filas totalmente vacías
    return filas.filter((f) => f.celdas.some((x) => x.trim() !== ""));
  }

  /** Importa un CSV generado por la aplicación y lo une a los registros existentes. */
  async function importarCSV(archivo) {
    const problema = revisarArchivo(archivo);
    if (problema) { mostrarMensaje("err", "No se pudo importar el CSV.", [problema]); return; }

    const texto = await leerArchivoTexto(archivo);

    // Detecta el separador mirando la primera línea (Excel en español usa «;»)
    const primera = texto.split(/\r?\n/)[0] || "";
    const nPuntoComa = (primera.match(/;/g) || []).length;
    const nComa = (primera.match(/,/g) || []).length;
    const sep = nPuntoComa >= nComa ? ";" : ",";

    const filas = parsearCSV(texto, sep);
    if (!filas.length) {
      mostrarMensaje("err", "No se pudo importar el CSV.", ["El archivo no contiene datos."]);
      return;
    }

    // --- Comprobar que las columnas coincidan ---
    const encabezado = filas[0].celdas.map(sinAcentos);
    const faltan = ENCABEZADOS_CSV.filter((_, i) => !encabezado.includes(ENCABEZADOS_NORM[i]));
    const sobran = filas[0].celdas.filter((_, i) => !ENCABEZADOS_NORM.includes(encabezado[i]));
    if (faltan.length || sobran.length || encabezado.length !== ENCABEZADOS_CSV.length) {
      const det = ["Las columnas del archivo no coinciden con las de EstadíApp UNIPAZ."];
      if (faltan.length) det.push("Faltan: " + faltan.join(", ") + ".");
      if (sobran.length) det.push("Columnas no reconocidas: " + sobran.map((s) => s.trim()).join(", ") + ".");
      det.push("Usa un archivo creado con el botón «Exportar CSV».");
      mostrarMensaje("err", "No se pudo importar el CSV.", det);
      return;
    }
    // Posición de cada columna (permite que estén en otro orden)
    const pos = ENCABEZADOS_NORM.map((n) => encabezado.indexOf(n));

    const datos = filas.slice(1);
    if (!datos.length) {
      mostrarMensaje("err", "No se pudo importar el CSV.", ["El archivo solo tiene encabezados, sin registros."]);
      return;
    }
    if (datos.length > MAX_REGISTROS_IMPORTAR) {
      mostrarMensaje("err", "No se pudo importar el CSV.",
        [`El archivo tiene más de ${MAX_REGISTROS_IMPORTAR} registros.`]);
      return;
    }

    // --- Validar TODAS las filas antes de agregar alguna ---
    const validos = [], errores = [];
    datos.forEach((f) => {
      if (f.celdas.length !== ENCABEZADOS_CSV.length) {
        errores.push(`Fila ${f.n}: tiene ${f.celdas.length} columnas y se esperaban ${ENCABEZADOS_CSV.length}.`);
        return;
      }
      const v = (i) => f.celdas[pos[i]];
      const res = normalizarRegistro({
        fecha: v(0), hora: v(1), /* franja (2) se recalcula */ cafeteria: v(3),
        tiempo: v(4), valor: v(5), producto: v(6), satisfaccion: v(7)
      });
      if (res.error) errores.push(`Fila ${f.n}: ${res.error}.`);
      else validos.push(res.registro);
    });

    if (errores.length) {
      const det = errores.slice(0, 5);
      if (errores.length > 5) det.push(`… y ${errores.length - 5} errores más.`);
      det.push("No se importó ningún registro. Corrige el archivo e inténtalo de nuevo.");
      mostrarMensaje("err", `El CSV tiene ${errores.length} fila(s) con errores.`, det);
      return;
    }

    // --- Unir con los existentes, omitiendo los que ya están ---
    const { agregados, duplicados } = unirRegistros(validos);
    const det = [];
    if (duplicados) det.push(`${duplicados} registro(s) omitido(s) porque ya existían.`);
    det.push(`Total actual: ${registros.length} registros.`);

    if (agregados === 0) {
      mostrarMensaje("warn", "No se importó ningún registro nuevo.", det);
      avisar("ℹ️ Todos los registros del CSV ya existían.");
    } else {
      mostrarMensaje("ok", `Se importaron ${agregados} registro(s) desde el CSV.`, det);
      avisar(`✅ ${agregados} registro(s) importado(s).`);
    }
  }

  /* ---------- 14. RESPALDO JSON ---------- */

  /** Descarga todos los registros en un archivo JSON. */
  function exportarJSON() {
    if (!registros.length) { avisar("⚠️ No hay registros para respaldar."); return; }

    const respaldo = {
      app: APP_NOMBRE,
      version: VERSION_RESPALDO,
      exportadoEl: new Date().toISOString(),
      total: registros.length,
      registros: registros
    };
    const nombre = `respaldo_estadiapp_unipaz_${fechaActual()}_${horaActual().replace(":", "")}.json`;
    descargarArchivo(nombre, JSON.stringify(respaldo, null, 2), "application/json;charset=utf-8");
    mostrarMensaje("ok", `Respaldo descargado: ${registros.length} registros.`, [`Archivo: ${nombre}`]);
    avisar("🛟 Respaldo descargado.");
  }

  /** Lee y valida un respaldo JSON; si es correcto, pregunta cómo restaurarlo. */
  async function prepararRestauracion(archivo) {
    const problema = revisarArchivo(archivo);
    if (problema) { mostrarMensaje("err", "No se pudo restaurar el respaldo.", [problema]); return; }

    const texto = await leerArchivoTexto(archivo);
    let datos;
    try {
      datos = JSON.parse(texto);
    } catch (e) {
      mostrarMensaje("err", "No se pudo restaurar el respaldo.", ["El archivo no es un JSON válido."]);
      return;
    }

    // --- Validar la estructura ---
    let lista;
    if (Array.isArray(datos)) {
      lista = datos;                                   // lista simple de registros
    } else if (datos && typeof datos === "object") {
      if (datos.app !== APP_NOMBRE) {
        mostrarMensaje("err", "No se pudo restaurar el respaldo.",
          ["El archivo no parece un respaldo de EstadíApp UNIPAZ."]);
        return;
      }
      if (typeof datos.version === "number" && datos.version > VERSION_RESPALDO) {
        mostrarMensaje("err", "No se pudo restaurar el respaldo.",
          ["El respaldo fue creado con una versión más reciente de la aplicación."]);
        return;
      }
      if (!Array.isArray(datos.registros)) {
        mostrarMensaje("err", "No se pudo restaurar el respaldo.",
          ["La estructura es incorrecta: falta la lista de registros."]);
        return;
      }
      lista = datos.registros;
    } else {
      mostrarMensaje("err", "No se pudo restaurar el respaldo.", ["La estructura del archivo no es válida."]);
      return;
    }

    if (!lista.length) {
      mostrarMensaje("err", "No se pudo restaurar el respaldo.", ["El respaldo no contiene registros."]);
      return;
    }
    if (lista.length > MAX_REGISTROS_IMPORTAR) {
      mostrarMensaje("err", "No se pudo restaurar el respaldo.",
        [`El respaldo tiene más de ${MAX_REGISTROS_IMPORTAR} registros.`]);
      return;
    }

    // Valida cada registro: si hay alguno incorrecto no se restaura nada
    const validos = [], errores = [];
    lista.forEach((item, i) => {
      const res = normalizarRegistro(item);
      if (res.error) errores.push(`Registro ${i + 1}: ${res.error}.`);
      else validos.push(res.registro);
    });
    if (errores.length) {
      const det = errores.slice(0, 5);
      if (errores.length > 5) det.push(`… y ${errores.length - 5} errores más.`);
      det.push("No se restauró ningún registro.");
      mostrarMensaje("err", `El respaldo tiene ${errores.length} registro(s) con errores.`, det);
      return;
    }

    // Si no hay datos actuales, se restaura directamente
    if (!registros.length) {
      registros = validos;
      guardarRegistros();
      renderizar();
      mostrarMensaje("ok", `Se restauraron ${validos.length} registro(s).`, [`Total actual: ${registros.length} registros.`]);
      avisar("✅ Respaldo restaurado.");
      return;
    }

    // Hay datos actuales: el usuario decide entre combinar o reemplazar
    const { duplicados } = particionar(validos);
    jsonPendiente = validos;
    $("restaurar-texto").textContent =
      `El respaldo tiene ${validos.length} registros válidos (${duplicados} ya existen en tu tabla). ` +
      `Actualmente tienes ${registros.length}. «Combinar» agrega solo los nuevos y conserva todo lo actual; ` +
      `«Reemplazar todo» borra los ${registros.length} registros actuales y deja únicamente los del respaldo.`;
    $("modal-restaurar").showModal();
  }

  // Botones del cuadro de restauración (se enlazan una sola vez)
  $("restaurar-cancelar").addEventListener("click", () => {
    jsonPendiente = null;
    $("modal-restaurar").close();
    mostrarMensaje("warn", "Restauración cancelada.", ["Tus registros no se modificaron."]);
  });

  $("restaurar-unir").addEventListener("click", () => {
    const candidatos = jsonPendiente;
    jsonPendiente = null;
    $("modal-restaurar").close();
    if (!candidatos) return;
    const { agregados, duplicados } = unirRegistros(candidatos);
    const det = [];
    if (duplicados) det.push(`${duplicados} registro(s) omitido(s) porque ya existían.`);
    det.push(`Total actual: ${registros.length} registros.`);
    if (agregados === 0) mostrarMensaje("warn", "No se agregó ningún registro nuevo.", det);
    else mostrarMensaje("ok", `Se combinaron ${agregados} registro(s) del respaldo.`, det);
    avisar("✅ Respaldo combinado.");
  });

  $("restaurar-reemplazar").addEventListener("click", () => {
    const candidatos = jsonPendiente;
    jsonPendiente = null;
    $("modal-restaurar").close();
    if (!candidatos) return;
    registros = candidatos;
    guardarRegistros();
    renderizar();
    mostrarMensaje("ok", `Se restauraron ${candidatos.length} registro(s), reemplazando los anteriores.`,
      [`Total actual: ${registros.length} registros.`]);
    avisar("✅ Respaldo restaurado.");
  });

  // Cerrar con clic fuera o con Esc equivale a cancelar
  $("modal-restaurar").addEventListener("click", (e) => {
    if (e.target === $("modal-restaurar")) $("modal-restaurar").close();
  });
  $("modal-restaurar").addEventListener("close", () => { jsonPendiente = null; });

  /* ---------- 15. ENLACE DE BOTONES Y SELECTORES DE ARCHIVO ---------- */

  /**
   * Ejecuta una operación de archivo una sola vez, aunque el usuario haga doble clic.
   * Se limpia el selector para poder elegir de nuevo el mismo archivo.
   */
  function manejarArchivo(input, operacion) {
    input.addEventListener("change", async () => {
      const archivo = input.files && input.files[0];
      input.value = "";                 // permite volver a seleccionar el mismo archivo
      if (!archivo) return;
      if (ocupado) { avisar("⏳ Espera a que termine la operación en curso."); return; }
      ocupado = true;
      try {
        await operacion(archivo);
      } catch (e) {
        mostrarMensaje("err", "Ocurrió un error al leer el archivo.", ["Verifica que sea un archivo válido e inténtalo de nuevo."]);
      } finally {
        ocupado = false;
      }
    });
  }

  $("btn-exportar-csv").addEventListener("click", exportarCSV);
  $("btn-exportar-json").addEventListener("click", exportarJSON);
  $("btn-importar-csv").addEventListener("click", () => $("file-csv").click());
  $("btn-importar-json").addEventListener("click", () => $("file-json").click());
  manejarArchivo($("file-csv"), importarCSV);
  manejarArchivo($("file-json"), prepararRestauracion);

  /* ==========================================================
     PESTAÑA ANÁLISIS
     ========================================================== */

  /* ---------- 16. DEFINICIÓN DE VARIABLES ANALIZABLES ---------- */

  const VARIABLES_ANALISIS = {
    tiempo:       { nombre: "Tiempo en fila (min)", corto: "Tiempo en fila", tipo: "Cuantitativa continua", cuant: true, unidad: "min" },
    valor:        { nombre: "Valor de compra ($)", corto: "Valor de compra", tipo: "Cuantitativa numérica", cuant: true, unidad: "$" },
    cafeteria:    { nombre: "Cafetería", corto: "Cafetería", tipo: "Cualitativa nominal", cuant: false, categorias: CAFETERIAS },
    producto:     { nombre: "Producto principal", corto: "Producto principal", tipo: "Cualitativa nominal", cuant: false, categorias: PRODUCTOS },
    satisfaccion: { nombre: "Satisfacción", corto: "Satisfacción", tipo: "Cualitativa ordinal", cuant: false, categorias: [1, 2, 3, 4, 5] },
    franja:       { nombre: "Franja horaria", corto: "Franja horaria", tipo: "Cualitativa nominal", cuant: false, categorias: ["Mañana", "Mediodía", "Tarde", "Noche"] }
  };
  const CLAVES_CUALITATIVAS = Object.keys(VARIABLES_ANALISIS).filter((k) => !VARIABLES_ANALISIS[k].cuant);

  /* ---------- 17. FORMATO COLOMBIANO ---------- */

  /** Formatea un número con punto de miles y coma decimal (convención colombiana). */
  function fmt(n, dec) {
    if (!Number.isFinite(n)) return "—";
    if (dec === undefined) dec = 2;
    const s = Math.abs(n).toFixed(dec);
    const partes = s.split(".");
    const ent = partes[0].replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    const signo = (n < 0 && parseFloat(s) !== 0) ? "-" : "";
    return signo + ent + (partes[1] ? "," + partes[1] : "");
  }

  /** Cantidad de decimales de un número (máximo 6). */
  function decimales(x) {
    const m = /\.(\d+)$/.exec(String(x));
    return m ? Math.min(6, m[1].length) : 0;
  }

  /** Devuelve funciones para escribir valores con la unidad de la variable. */
  function formateadores(v) {
    if (v.unidad === "$") {
      return { u: (n, d) => "$ " + fmt(n, d), u2: (n, d) => fmt(n, d) + " $²" };
    }
    return { u: (n, d) => fmt(n, d) + " min", u2: (n, d) => fmt(n, d) + " min²" };
  }

  /* ---------- 18. FILTROS ---------- */

  /** Llena la lista de variables por las que se puede filtrar (excluye la analizada). */
  function poblarFiltroVariable() {
    const sel = $("an-filtro-var");
    const previo = sel.value;
    const actual = $("an-variable").value;
    let html = '<option value="">Sin filtro</option>';
    CLAVES_CUALITATIVAS.forEach((k) => {
      if (k !== actual) html += `<option value="${k}">${esc(VARIABLES_ANALISIS[k].corto)}</option>`;
    });
    sel.innerHTML = html;
    sel.value = [...sel.options].some((o) => o.value === previo) ? previo : "";
  }

  /** Llena los valores del filtro con su conteo de registros. */
  function poblarFiltroValores() {
    const fv = $("an-filtro-var").value;
    const sel = $("an-filtro-val");
    const previo = sel.value;
    if (!fv) {
      sel.innerHTML = '<option value="">—</option>';
      sel.disabled = true;
      return;
    }
    const def = VARIABLES_ANALISIS[fv];
    let html = '<option value="">Todos los valores</option>';
    def.categorias.forEach((c) => {
      const cnt = registros.filter((r) => String(r[fv]) === String(c)).length;
      html += `<option value="${esc(c)}">${esc(c)} (${cnt})</option>`;
    });
    sel.innerHTML = html;
    sel.disabled = false;
    sel.value = [...sel.options].some((o) => o.value === previo) ? previo : "";
  }

  /** Devuelve los registros que cumplen el filtro seleccionado (o todos). */
  function obtenerRegistrosFiltrados() {
    const fv = $("an-filtro-var").value;
    const fval = $("an-filtro-val").value;
    if (!fv || fval === "") return registros.slice();
    return registros.filter((r) => String(r[fv]) === fval);
  }

  /* ---------- 19. CÁLCULOS ESTADÍSTICOS ---------- */

  /** Gráfico de barras horizontal hecho con HTML/CSS (versión anterior, ya no se usa en pantalla). */
  function htmlBarras(items) {
    const max = Math.max(1, ...items.map((i) => i.val));
    return '<div class="barras">' + items.map((i) =>
      `<div class="barra-fila">
         <span class="barra-etq">${esc(i.etq)}</span>
         <div class="barra-pista"><div class="barra-relleno" style="width:${(i.val / max * 100).toFixed(1)}%"></div></div>
         <span class="barra-val">${i.val} (${fmt(i.pct, 1)} %)</span>
       </div>`).join("") + "</div>";
  }

  /**
   * Agrupa los datos ordenados x en clases por la regla de Sturges.
   * d = máximo de decimales de los datos (la amplitud se redondea hacia arriba a d decimales).
   */
  function agruparDatos(x, d) {
    const n = x.length, min = x[0], max = x[n - 1], R = max - min;
    const kRaw = 1 + 3.322 * Math.log10(n);
    const k = Math.max(1, Math.round(kRaw));
    const pot = Math.pow(10, d);
    // toFixed(9) evita que errores de coma flotante cambien el resultado de ceil
    let A = Math.ceil(+((R / k) * pot).toFixed(9)) / pot;
    let rangoCero = false;
    if (A <= 0) { A = 1 / pot; rangoCero = true; }
    A = +A.toFixed(d);

    const clases = [];
    for (let j = 0; j < k; j++) {
      clases.push({
        li: +(min + j * A).toFixed(d),
        ls: +(min + (j + 1) * A).toFixed(d),
        fi: 0
      });
    }
    // Intervalos [Li, Ls), excepto el último, que incluye Ls
    x.forEach((val) => {
      for (let j = 0; j < k; j++) {
        const c = clases[j];
        if (val >= c.li && (val < c.ls || (j === k - 1 && val <= c.ls))) { c.fi++; break; }
      }
    });
    let Fi = 0;
    clases.forEach((c) => {
      Fi += c.fi;
      c.Fi = Fi;
      c.hi = c.fi / n * 100;
      c.Hi = Fi / n * 100;
      c.xi = (c.li + c.ls) / 2;
    });
    return { n, min, max, R, kRaw, k, A, clases, rangoCero };
  }

  /* ==========================================================
     NUEVO: GRÁFICOS SVG Y LECTURA AUTOMÁTICA
     ========================================================== */

  /* ---------- 19B. UTILIDADES DE GRÁFICOS ---------- */

  /** Ancho interno (viewBox) del gráfico: más angosto en celulares para que el texto siga legible. */
  const esMovil = () => window.innerWidth < 600;
  const anchoGrafico = () => (esMovil() ? 340 : 760);

  /** Redondea a un decimal para escribir coordenadas SVG compactas. */
  const p1 = (n) => (+n).toFixed(1);

  /** Calcula marcas "bonitas" para un eje entre lo y hi. Devuelve { valores, paso, dec }. */
  function ticksNice(lo, hi, cuantos) {
    if (hi <= lo) hi = lo + 1;
    const aprox = (hi - lo) / cuantos;
    const mag = Math.pow(10, Math.floor(Math.log10(aprox)));
    const norm = aprox / mag;
    const paso = (norm < 1.5 ? 1 : norm < 3 ? 2 : norm < 7 ? 5 : 10) * mag;
    const ini = Math.ceil(lo / paso - 1e-9) * paso;
    const valores = [];
    for (let v = ini; v <= hi + paso * 1e-9; v += paso) valores.push(+v.toFixed(10));
    const dec = Math.max(0, Math.min(6, -Math.floor(Math.log10(paso) + 1e-9)));
    return { valores, paso, dec };
  }

  /** Abre un SVG con su título, subtítulo y descripción accesible. */
  function svgAbrir(W, H, titulo, sub, desc) {
    return `<svg class="grafico" viewBox="0 0 ${W} ${H}" role="img" preserveAspectRatio="xMidYMid meet" aria-label="${esc(titulo + ". " + sub)}">` +
      `<title>${esc(titulo)}</title><desc>${esc(desc)}</desc>` +
      `<text class="g-titulo" x="${W / 2}" y="22">${esc(titulo)}</text>` +
      `<text class="g-sub" x="${W / 2}" y="40">${esc(sub)}</text>`;
  }

  /* ---------- 19C. HISTOGRAMA + POLÍGONO DE FRECUENCIAS ---------- */

  /** Histograma con polígono de frecuencias superpuesto, a partir de la tabla agrupada g. */
  function svgHistograma(g, d, v, n) {
    const W = anchoGrafico(), movil = esMovil();
    const m = { t: 58, r: movil ? 14 : 26, b: 112, l: movil ? 46 : 66 };
    const ph = movil ? 210 : 250;
    const H = m.t + ph + m.b;
    const pw = W - m.l - m.r;
    const y0 = m.t + ph;
    const cl = g.clases, k = g.k, A = g.A;
    const fl = (val) => fmt(val, d);

    // Eje X: se deja una clase vacía a cada lado para cerrar el polígono en cero
    const xMin = cl[0].li - A, xMax = cl[k - 1].ls + A;
    const sx = (x) => m.l + (x - xMin) / (xMax - xMin) * pw;

    // Eje Y: frecuencias enteras
    const maxF = Math.max(1, ...cl.map((c) => c.fi));
    const paso = Math.max(1, Math.round(ticksNice(0, maxF, 5).paso));
    const yTop = Math.ceil(maxF / paso) * paso;
    const sy = (f) => m.t + ph - f / yTop * ph;

    let s = svgAbrir(W, H, "Histograma y polígono de frecuencias", `${v.nombre} · n = ${n}`,
      `Histograma de ${k} clases con polígono de frecuencias superpuesto para ${v.nombre}.`);

    // Cuadrícula y marcas del eje Y
    for (let f = 0; f <= yTop; f += paso) {
      s += `<line class="g-rej" x1="${m.l}" x2="${W - m.r}" y1="${p1(sy(f))}" y2="${p1(sy(f))}"/>` +
           `<text class="g-tick" x="${m.l - 8}" y="${p1(sy(f) + 4)}" text-anchor="end">${f}</text>`;
    }

    // Barras del histograma
    cl.forEach((c, j) => {
      const x0 = sx(c.li), x1 = sx(c.ls), h = c.fi / yTop * ph;
      const lim = `[${fl(c.li)}; ${fl(c.ls)}${j === k - 1 ? "]" : ")"}`;
      s += `<rect class="g-barra" x="${p1(x0)}" y="${p1(y0 - h)}" width="${p1(x1 - x0)}" height="${p1(h)}">` +
           `<title>Clase ${j + 1} ${lim}: fi = ${c.fi} (${fmt(c.hi, 2)} %)</title></rect>`;
      if (c.fi > 0) {
        s += `<text class="g-valor" x="${p1((x0 + x1) / 2)}" y="${p1(y0 - h - 5)}" text-anchor="middle">${c.fi}</text>`;
      }
    });

    // Polígono de frecuencias: marcas de clase + una clase vacía a cada lado
    const pts = [{ x: cl[0].xi - A, f: 0 }]
      .concat(cl.map((c) => ({ x: c.xi, f: c.fi })))
      .concat([{ x: cl[k - 1].xi + A, f: 0 }]);
    s += `<polyline class="g-poli" points="${pts.map((q) => p1(sx(q.x)) + "," + p1(sy(q.f))).join(" ")}"/>`;
    pts.forEach((q) => { s += `<circle class="g-punto" cx="${p1(sx(q.x))}" cy="${p1(sy(q.f))}" r="3.5"/>`; });

    // Ejes
    s += `<line class="g-eje" x1="${m.l}" x2="${W - m.r}" y1="${y0}" y2="${y0}"/>` +
         `<line class="g-eje" x1="${m.l}" x2="${m.l}" y1="${m.t}" y2="${y0}"/>`;

    // Marcas del eje X en los límites de clase (se omiten algunas si no caben)
    const pxClase = A / (xMax - xMin) * pw;
    const salto = Math.max(1, Math.ceil(22 / pxClase));
    const lims = cl.map((c) => c.li).concat([cl[k - 1].ls]);
    lims.forEach((val, j) => {
      const x = sx(val);
      s += `<line class="g-eje" x1="${p1(x)}" x2="${p1(x)}" y1="${y0}" y2="${y0 + 5}"/>`;
      if (j % salto === 0) {
        s += `<text class="g-tick" x="${p1(x)}" y="${y0 + 17}" text-anchor="end" transform="rotate(-40 ${p1(x)} ${y0 + 17})">${fl(val)}</text>`;
      }
    });

    // Títulos de los ejes
    s += `<text class="g-eje-t" x="${p1(m.l + pw / 2)}" y="${y0 + 82}" text-anchor="middle">${esc(v.nombre)} — límites de clase</text>` +
         `<text class="g-eje-t" x="14" y="${p1(m.t + ph / 2)}" text-anchor="middle" transform="rotate(-90 14 ${p1(m.t + ph / 2)})">Frecuencia absoluta (fi)</text>`;

    // Leyenda
    const yl = y0 + 103;
    s += `<rect class="g-barra" x="${m.l}" y="${yl - 9}" width="14" height="10"/>` +
         `<text class="g-leyenda" x="${m.l + 19}" y="${yl}">Histograma</text>` +
         `<line class="g-poli" x1="${m.l + 92}" x2="${m.l + 112}" y1="${yl - 4}" y2="${yl - 4}"/>` +
         `<circle class="g-punto" cx="${m.l + 102}" cy="${yl - 4}" r="3.5"/>` +
         `<text class="g-leyenda" x="${m.l + 118}" y="${yl}">Polígono de frecuencias</text>`;

    return s + "</svg>";
  }

  /* ---------- 19D. DIAGRAMA DE CAJA Y BIGOTES ---------- */

  /** Diagrama de caja horizontal. est = { min, q1, me, q3, max, media }. */
  function svgCaja(est, v, n) {
    const W = anchoGrafico(), movil = esMovil();
    const m = { t: 56, r: movil ? 18 : 30, l: movil ? 40 : 52 };
    const pw = W - m.l - m.r;

    // Dominio del eje con un pequeño margen a cada lado
    let pad = (est.max - est.min) * 0.06;
    if (pad === 0) pad = Math.max(Math.abs(est.min) * 0.05, 1);
    const dLo = est.min - pad, dHi = est.max + pad;
    const sx = (x) => m.l + (x - dLo) / (dHi - dLo) * pw;
    const tk = ticksNice(dLo, dHi, movil ? 4 : 7);

    const yBox = m.t + 56, bh = 46, yMid = yBox + bh / 2, yEje = yBox + bh + 22;
    const H = yEje + 78;

    let s = svgAbrir(W, H, "Diagrama de caja y bigotes", `${v.nombre} · n = ${n}`,
      "Diagrama de caja con mínimo, primer cuartil, mediana, tercer cuartil, máximo y media.");

    // Cuadrícula vertical y marcas del eje X
    tk.valores.forEach((t) => {
      const x = sx(t);
      s += `<line class="g-rej" x1="${p1(x)}" x2="${p1(x)}" y1="${yBox - 6}" y2="${yEje}"/>` +
           `<line class="g-eje" x1="${p1(x)}" x2="${p1(x)}" y1="${yEje}" y2="${yEje + 5}"/>` +
           `<text class="g-tick" x="${p1(x)}" y="${yEje + 19}" text-anchor="middle">${fmt(t, tk.dec)}</text>`;
    });
    s += `<line class="g-eje" x1="${m.l}" x2="${W - m.r}" y1="${yEje}" y2="${yEje}"/>`;

    // Bigotes (mínimo → Q1 y Q3 → máximo) con remates
    const xMin = sx(est.min), xQ1 = sx(est.q1), xMe = sx(est.me), xQ3 = sx(est.q3), xMax = sx(est.max), xMd = sx(est.media);
    s += `<line class="g-bigote" x1="${p1(xMin)}" x2="${p1(xQ1)}" y1="${yMid}" y2="${yMid}"/>` +
         `<line class="g-bigote" x1="${p1(xQ3)}" x2="${p1(xMax)}" y1="${yMid}" y2="${yMid}"/>` +
         `<line class="g-bigote" x1="${p1(xMin)}" x2="${p1(xMin)}" y1="${yMid - 11}" y2="${yMid + 11}"/>` +
         `<line class="g-bigote" x1="${p1(xMax)}" x2="${p1(xMax)}" y1="${yMid - 11}" y2="${yMid + 11}"/>`;

    // Caja (Q1 a Q3), mediana y media
    s += `<rect class="g-caja" x="${p1(xQ1)}" y="${yBox}" width="${p1(Math.max(xQ3 - xQ1, 0))}" height="${bh}"/>` +
         `<line class="g-med" x1="${p1(xMe)}" x2="${p1(xMe)}" y1="${yBox}" y2="${yBox + bh}"/>` +
         `<polygon class="g-media" points="${p1(xMd)},${yMid - 9} ${p1(xMd + 9)},${yMid} ${p1(xMd)},${yMid + 9} ${p1(xMd - 9)},${yMid}"/>`;    // Etiquetas de los cinco valores principales
    const etiquetas = [
      { x: xMin, y: yBox - 10, t: "Mín." },
      { x: xQ1, y: yBox + bh + 14, t: "Q1" },
      { x: xMe, y: yBox - 10, t: "Mediana" },
      { x: xQ3, y: yBox + bh + 14, t: "Q3" },
      { x: xMax, y: yBox - 10, t: "Máx." }
    ];
    etiquetas.forEach((e) => {
      s += `<text class="g-etq" x="${p1(e.x)}" y="${e.y}" text-anchor="middle">${e.t}</text>`;
    });

    // Leyenda de la media
    s += `<polygon class="g-media" points="${p1(m.l + 8)},${yEje + 43} ${p1(m.l + 16)},${yEje + 51} ${p1(m.l + 8)},${yEje + 59} ${p1(m.l)},${yEje + 51}"/>` +
         `<text class="g-leyenda" x="${m.l + 22}" y="${yEje + 55}">Media</text>` +
         `<text class="g-eje-t" x="${p1(m.l + pw / 2)}" y="${H - 5}" text-anchor="middle">${esc(v.nombre)}</text>`;

    return s + "</svg>";
  }

  /* ---------- 19E. GRÁFICO DE BARRAS HORIZONTALES ---------- */

  /** Barras horizontales SVG para una variable cualitativa. */
  function svgBarrasH(items, v, n) {
    const W = anchoGrafico(), movil = esMovil();
    const m = { t: 58, r: movil ? 48 : 70, b: 48, l: movil ? 112 : 190 };
    const altoFila = movil ? 36 : 40;
    const H = m.t + items.length * altoFila + m.b;
    const pw = W - m.l - m.r;
    const max = Math.max(1, ...items.map((i) => i.fi));
    const tk = ticksNice(0, max, 5);
    const yBase = m.t + items.length * altoFila;

    let s = svgAbrir(W, H, "Frecuencia por categoría", `${v.nombre} · n = ${n}`,
      `Gráfico de barras horizontales con frecuencias absolutas y porcentajes para ${v.nombre}.`);

    // Eje X y cuadrícula
    tk.valores.forEach((t) => {
      const x = m.l + t / max * pw;
      s += `<line class="g-rej" x1="${p1(x)}" x2="${p1(x)}" y1="${m.t - 4}" y2="${yBase}"/>` +
           `<text class="g-tick" x="${p1(x)}" y="${yBase + 18}" text-anchor="middle">${fmt(t, tk.dec)}</text>`;
    });
    s += `<line class="g-eje" x1="${m.l}" x2="${W - m.r}" y1="${yBase}" y2="${yBase}"/>`;

    // Barras y etiquetas
    items.forEach((it, i) => {
      const y = m.t + i * altoFila + 5;
      const ancho = it.fi / max * pw;
      const centro = y + 12;
      s += `<text class="g-cat" x="${m.l - 8}" y="${centro + 4}" text-anchor="end">${esc(it.etq)}</text>` +
           `<rect class="g-barra" x="${m.l}" y="${y}" width="${p1(ancho)}" height="24" rx="3">` +
           `<title>${esc(it.etq)}: ${it.fi} registros (${fmt(it.pct, 1)} %)</title></rect>` +
           `<text class="g-valor" x="${p1(m.l + ancho + 6)}" y="${centro + 4}">${it.fi} · ${fmt(it.pct, 1)} %</text>`;
    });

    s += `<text class="g-eje-t" x="${p1(m.l + pw / 2)}" y="${H - 6}" text-anchor="middle">Frecuencia absoluta (fi)</text>`;
    return s + "</svg>";
  }

  /* ---------- 19F. LECTURA AUTOMÁTICA DE CUANTITATIVAS ---------- */

  /**
   * Interpreta la forma de la distribución comparando media y mediana.
   * También clasifica la dispersión mediante el coeficiente de variación.
   */
  function htmlLecturaCuant(est, v) {
    const dif = est.media - est.mediana;
    const tolerancia = Math.max(Math.abs(est.media), Math.abs(est.mediana), 1) * 0.01;
    let forma, claseForma, detalleForma;

    if (Math.abs(dif) <= tolerancia) {
      forma = "Distribución aproximadamente simétrica";
      claseForma = "ins-verde";
      detalleForma = "La media y la mediana son muy cercanas. No se observa un sesgo marcado.";
    } else if (dif > 0) {
      forma = "Asimetría positiva (sesgo a la derecha)";
      claseForma = "ins-ambar";
      detalleForma = "La media es mayor que la mediana. Algunos valores altos pueden estar desplazando el promedio hacia la derecha.";
    } else {
      forma = "Asimetría negativa (sesgo a la izquierda)";
      claseForma = "ins-ambar";
      detalleForma = "La media es menor que la mediana. Algunos valores bajos pueden estar desplazando el promedio hacia la izquierda.";
    }

    let cvClase, cvTexto, cvDetalle;
    if (est.cv < 15) {
      cvClase = "ins-verde";
      cvTexto = "Datos homogéneos";
      cvDetalle = "El coeficiente de variación es menor del 15 %; los datos presentan poca dispersión relativa.";
    } else if (est.cv < 30) {
      cvClase = "ins-ambar";
      cvTexto = "Dispersión moderada";
      cvDetalle = "El coeficiente de variación está entre el 15 % y menos del 30 %; existe una variabilidad intermedia.";
    } else {
      cvClase = "ins-rojo";
      cvTexto = "Datos muy dispersos";
      cvDetalle = "El coeficiente de variación es del 30 % o superior; los datos presentan alta dispersión relativa.";
    }

    const f = formateadores(v);
    return `
      <h3 class="an-sub">Lectura automática</h3>
      <ul class="lectura">
        <li>
          <b>${forma}</b>
          <span class="insignia ${claseForma}">${dif > tolerancia ? "Sesgo positivo" : dif < -tolerancia ? "Sesgo negativo" : "Simetría"}</span>
          <small>${detalleForma} Media: ${f.u(est.media)}; mediana: ${f.u(est.mediana)}.</small>
        </li>
        <li>
          <b>${cvTexto}</b>
          <span class="insignia ${cvClase}">CV = ${fmt(est.cv, 2)} %</span>
          <small>${cvDetalle}</small>
        </li>
      </ul>`;
  }

  /* ---------- 19G. LECTURA AUTOMÁTICA DE CUALITATIVAS ---------- */

  /** Identifica la categoría con mayor frecuencia y comunica su porcentaje. */
  function htmlLecturaCual(items, v, n) {
    if (!items.length || n === 0) return "";
    const max = Math.max(...items.map((i) => i.fi));
    const moda = items.filter((i) => i.fi === max);
    const nombres = moda.map((i) => esc(i.etq)).join(", ");
    const pct = max / n * 100;
    const texto = moda.length > 1 ? "Las categorías más frecuentes son" : "La categoría más frecuente es";
    return `
      <h3 class="an-sub">Lectura automática</h3>
      <ul class="lectura">
        <li>
          <b>${texto}: ${nombres}.</b>
          <span class="insignia ins-verde">${max} registro(s) · ${fmt(pct, 1)} %</span>
          <small>De los ${n} registros analizados para ${esc(v.nombre)}, esta categoría${moda.length > 1 ? " comparte la mayor frecuencia" : " presenta la mayor frecuencia"}.</small>
        </li>
      </ul>`;
  }

  /* ---------- 20. ANÁLISIS CUANTITATIVO ---------- */

  /** Construye el análisis completo de una variable cuantitativa. */
  function htmlCuantitativa(datos, v) {
    const n = datos.length;
    if (!n) return '<p class="vacio">No hay datos numéricos para analizar con los filtros seleccionados.</p>';

    const x = datos.map((r) => Number(r[$("an-variable").value])).filter(Number.isFinite).sort((a, b) => a - b);
    if (!x.length) return '<p class="vacio">No hay datos numéricos válidos para esta variable.</p>';

    const suma = x.reduce((a, b) => a + b, 0);
    const media = suma / x.length;
    const mediana = x.length % 2
      ? x[Math.floor(x.length / 2)]
      : (x[x.length / 2 - 1] + x[x.length / 2]) / 2;

    // Cuartiles por método de mitades (Tukey)
    const mitadInf = x.slice(0, Math.floor(x.length / 2));
    const mitadSup = x.slice(Math.ceil(x.length / 2));
    const medianaLista = (a) => a.length % 2
      ? a[Math.floor(a.length / 2)]
      : a.length ? (a[a.length / 2 - 1] + a[a.length / 2]) / 2 : x[0];
    const q1 = medianaLista(mitadInf);
    const q3 = medianaLista(mitadSup);

    const min = x[0], max = x[x.length - 1], rango = max - min;
    const varianza = x.reduce((acc, z) => acc + Math.pow(z - media, 2), 0) / x.length;
    const desviacion = Math.sqrt(varianza);
    const cv = media !== 0 ? desviacion / Math.abs(media) * 100 : 0;
    const d = Math.max(...x.map(decimales));
    const g = agruparDatos(x, d);

    const est = { media, mediana, q1, q3, min, max, rango, varianza, desviacion, cv };
    const f = formateadores(v);

    let h = `
      <div class="an-contexto">
        <b>${esc(v.nombre)}</b> · ${esc(v.tipo)} · ${n} observación(es) válidas.
      </div>
      <div class="kpis">
        <div class="kpi"><span>Media</span><b>${f.u(media)}</b></div>
        <div class="kpi"><span>Mediana</span><b>${f.u(mediana)}</b></div>
        <div class="kpi"><span>Desviación estándar</span><b>${f.u(desviacion)}</b></div>
        <div class="kpi"><span>Coeficiente de variación</span><b>${fmt(cv, 2)} %</b></div>
      </div>

      <h3 class="an-sub">Medidas de posición y dispersión</h3>
      <div class="tabla-wrap">
        <table>
          <thead><tr><th>Medida</th><th>Resultado</th><th>Interpretación</th></tr></thead>
          <tbody>
            <tr><td>Mínimo</td><td class="res num">${f.u(min)}</td><td>Valor más pequeño.</td></tr>
            <tr><td>Primer cuartil (Q1)</td><td class="res num">${f.u(q1)}</td><td>El 25 % de los datos está en este valor o por debajo.</td></tr>
            <tr><td>Mediana (Q2)</td><td class="res num">${f.u(mediana)}</td><td>El 50 % de los datos está en este valor o por debajo.</td></tr>
            <tr><td>Tercer cuartil (Q3)</td><td class="res num">${f.u(q3)}</td><td>El 75 % de los datos está en este valor o por debajo.</td></tr>
            <tr><td>Máximo</td><td class="res num">${f.u(max)}</td><td>Valor más grande.</td></tr>
            <tr><td>Media</td><td class="res num">${f.u(media)}</td><td>Promedio aritmético.</td></tr>
            <tr><td>Rango</td><td class="res num">${f.u(rango)}</td><td>Diferencia entre máximo y mínimo.</td></tr>
            <tr><td>Varianza poblacional</td><td class="res num">${f.u2(varianza)}</td><td>Dispersión cuadrática respecto a la media.</td></tr>
            <tr><td>Desviación estándar poblacional</td><td class="res num">${f.u(desviacion)}</td><td>Dispersión típica alrededor de la media.</td></tr>
            <tr><td>Coeficiente de variación (CV)</td><td class="res num">${fmt(cv, 2)} %</td><td>Desviación estándar relativa a la media.</td></tr>
          </tbody>
        </table>
      </div>

      <h3 class="an-sub">Distribución de frecuencias agrupadas</h3>
      <p class="an-nota">Número de clases por Sturges: k = ${g.k} (resultado sin redondear: ${fmt(g.kRaw, 2)}). Amplitud: ${fmt(g.A, d)}.</p>
      <div class="tabla-wrap">
        <table>
          <thead>
            <tr><th>Clase</th><th>Intervalo</th><th>Marca (xi)</th><th>fi</th><th>Fi</th><th>hi (%)</th><th>Hi (%)</th></tr>
          </thead>
          <tbody>
            ${g.clases.map((c, i) => `
              <tr>
                <td>${i + 1}</td>
                <td>[${fmt(c.li, d)}; ${fmt(c.ls, d)}${i === g.k - 1 ? "]" : ")"}</td>
                <td class="num">${fmt(c.xi, d)}</td>
                <td class="num">${c.fi}</td>
                <td class="num">${c.Fi}</td>
                <td class="num">${fmt(c.hi, 2)} %</td>
                <td class="num">${fmt(c.Hi, 2)} %</td>
              </tr>`).join("")}
            <tr class="total"><td colspan="3">Total</td><td class="num">${n}</td><td class="num">${n}</td><td class="num">100,00 %</td><td class="num">100,00 %</td></tr>
          </tbody>
        </table>
      </div>

      <h3 class="an-sub">Histograma y polígono de frecuencias</h3>
      <div class="grafico-wrap">${svgHistograma(g, d, v, n)}</div>

      <h3 class="an-sub">Diagrama de caja y bigotes</h3>
      <div class="grafico-wrap">${svgCaja(est, v, n)}</div>

      ${htmlLecturaCuant(est, v)}
    `;
    return h;
  }

  /* ---------- 21. ANÁLISIS CUALITATIVO ---------- */

  /** Construye la tabla de frecuencias, barras y lectura de una variable cualitativa. */
  function htmlCualitativa(datos, v, clave) {
    const n = datos.length;
    if (!n) return '<p class="vacio">No hay datos para analizar con los filtros seleccionados.</p>';

    // Conteo de categorías observadas; se conserva el orden de las categorías definidas
    const conteo = new Map();
    v.categorias.forEach((c) => conteo.set(String(c), 0));
    datos.forEach((r) => {
      const val = String(r[clave]);
      conteo.set(val, (conteo.get(val) || 0) + 1);
    });

    const items = v.categorias.map((c) => ({
      etq: String(c),
      fi: conteo.get(String(c)) || 0,
      pct: (conteo.get(String(c)) || 0) / n * 100
    }));

    let h = `
      <div class="an-contexto">
        <b>${esc(v.nombre)}</b> · ${esc(v.tipo)} · ${n} observación(es) válidas.
      </div>
      <div class="kpis">
        <div class="kpi"><span>Total de observaciones</span><b>${n}</b></div>
        <div class="kpi"><span>Categorías</span><b>${v.categorias.length}</b></div>
        <div class="kpi"><span>Mayor frecuencia</span><b>${Math.max(...items.map((i) => i.fi))}</b></div>
      </div>

      <h3 class="an-sub">Tabla de frecuencias</h3>
      <div class="tabla-wrap">
        <table>
          <thead><tr><th>Categoría</th><th>Frecuencia absoluta (fi)</th><th>Porcentaje (%)</th></tr></thead>
          <tbody>
            ${items.map((i) => `
              <tr>
                <td>${esc(i.etq)}</td>
                <td class="num">${i.fi}</td>
                <td class="num">${fmt(i.pct, 2)} %</td>
              </tr>`).join("")}
            <tr class="total"><td>Total</td><td class="num">${n}</td><td class="num">100,00 %</td></tr>
          </tbody>
        </table>
      </div>

      <h3 class="an-sub">Gráfico de barras horizontales</h3>
      <div class="grafico-wrap">${svgBarrasH(items, v, n)}</div>

      ${htmlLecturaCual(items, v, n)}
    `;
    return h;
  }

  /* ---------- 22. RENDERIZAR ANÁLISIS ---------- */

  /** Actualiza la sección de análisis según la variable y el filtro seleccionados. */
  function actualizarAnalisis() {
    const clave = $("an-variable").value;
    const v = VARIABLES_ANALISIS[clave];
    if (!v) return;

    const datos = obtenerRegistrosFiltrados();
    const salida = $("an-resultado");

    if (!registros.length) {
      salida.innerHTML = '<p class="vacio">Aún no hay registros. Agrega datos en la pestaña «Registrar» para ver el análisis estadístico.</p>';
      return;
    }

    if (!datos.length) {
      salida.innerHTML = '<p class="vacio">No hay registros que coincidan con el filtro seleccionado.</p>';
      return;
    }

    salida.innerHTML = v.cuant
      ? htmlCuantitativa(datos, v)
      : htmlCualitativa(datos, v, clave);
  }

  // Cambiar variable: reconstruye filtros y resultados
  $("an-variable").addEventListener("change", () => {
    poblarFiltroVariable();
    poblarFiltroValores();
    actualizarAnalisis();
  });

  // Cambiar variable de filtro: reconstruye sus categorías
  $("an-filtro-var").addEventListener("change", () => {
    poblarFiltroValores();
    actualizarAnalisis();
  });

  // Cambiar valor de filtro
  $("an-filtro-val").addEventListener("change", actualizarAnalisis);

  // Quitar filtro
  $("an-quitar-filtro").addEventListener("click", () => {
    $("an-filtro-var").value = "";
    poblarFiltroValores();
    actualizarAnalisis();
  });

  // Al redimensionar la ventana se redibujan los SVG con el ancho correspondiente
  let resizeAnalisis;
  window.addEventListener("resize", () => {
    clearTimeout(resizeAnalisis);
    resizeAnalisis = setTimeout(() => {
      if ($("tab-analisis").classList.contains("activo")) actualizarAnalisis();
    }, 180);
  });

  /* ---------- 23. INICIALIZACIÓN ---------- */

  function iniciar() {
    cargarRegistros();
    reiniciarFormulario();
    renderizar();
    poblarFiltroVariable();
    poblarFiltroValores();
    actualizarAnalisis();
  }

  iniciar();

})();
</script>
</body>
</html>
