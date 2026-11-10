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
    .result-card {*

