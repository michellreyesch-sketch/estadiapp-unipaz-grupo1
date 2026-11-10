# estadiapp-unipaz-grupo1
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
.btn-primario { background: var(--verde); color: #fff; }
.btn-primario:hover { filter: brightness(1.08); }
.btn-sec { background: #e6ebf2; color: var(--azul); }
.btn-sec:hover { filter: brightness(.96); }
.btn-peligro { background: var(--error); color: #fff; }
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
       PESTAÑA 2: ANÁLISIS (preparada)
       ======================================================== -->
  <section id="tab-analisis" class="panel">
    <div class="card">
      <h2>Análisis estadístico descriptivo</h2>
      <p class="sub">Sección preparada para su programación.</p>
      <div class="pendiente" id="analisis-contenido">
        <p><strong>Próximamente:</strong> aquí se mostrarán los resultados descriptivos.</p>
        <div class="chips">
          <span class="chip">Tablas de frecuencias</span>
          <span class="chip">Media, mediana y moda</span>
          <span class="chip">Varianza y desviación estándar</span>
          <span class="chip">Cuartiles y valores atípicos</span>
          <span class="chip">Gráficos de barras e histogramas</span>
          <span class="chip">Comparación entre cafeterías</span>
        </div>
        <div class="aviso-n">Registros disponibles para analizar: <b class="n-registros">0</b></div>
      </div>
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

  /* ---------- 10. INICIO ---------- */
  cargarRegistros();
  reiniciarFormulario();
  renderizar();

})();
</script>
</body>
</html>
