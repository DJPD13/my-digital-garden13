---
{"dg-publish":true,"permalink":"/pediatria/dosis-pediatrica/","dgPassFrontmatter":true}
---

<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Dosis pediátrica (calculadora por peso)</title>
  <style>
    :root {
      --bg:#0b1020; --card:#111a33; --text:#e8eeff; --muted:#a9b5df;
      --accent:#6ea8ff; --line:rgba(255,255,255,.10); --warn:#ffd56e;
    }
    * { box-sizing:border-box; }
    body {
      margin:0; font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial,sans-serif;
      background:linear-gradient(180deg, #070a14, var(--bg)); color:var(--text);
    }
    header {
      padding:22px 18px 14px; position:sticky; top:0; z-index:20;
      background:rgba(7,10,20,.85); backdrop-filter: blur(10px);
      border-bottom:1px solid var(--line);
    }
    .wrap { max-width:1100px; margin:0 auto; }
    h1 { font-size:18px; margin:0 0 10px; letter-spacing:.2px; }
    .controls {
      display:flex; flex-wrap:wrap; gap:10px; align-items:end;
    }
    label { display:block; font-size:12px; color:var(--muted); margin-bottom:6px; }
    input[type="number"], input[type="text"] {
      width:240px; max-width:100%;
      padding:10px 12px; border-radius:12px;
      border:1px solid var(--line); background:rgba(255,255,255,.04);
      color:var(--text); outline:none;
    }
    input[type="number"]:focus, input[type="text"]:focus {
      border-color:rgba(110,168,255,.6);
      box-shadow:0 0 0 3px rgba(110,168,255,.15);
    }
    .chip {
      display:inline-flex; gap:8px; align-items:center;
      padding:10px 12px; border-radius:12px;
      border:1px solid var(--line); background:rgba(255,255,255,.03);
      color:var(--muted); font-size:12px;
    }
    .chip b { color:var(--text); font-weight:600; }
    main { padding:14px 18px 40px; }
    .card {
      background:rgba(17,26,51,.75);
      border:1px solid var(--line); border-radius:18px;
      overflow:hidden; margin:14px 0;
      box-shadow: 0 10px 28px rgba(0,0,0,.20);
    }
    .card h2 {
      margin:0; padding:12px 14px;
      font-size:13px; letter-spacing:.6px; text-transform:uppercase;
      background:rgba(255,255,255,.03);
      border-bottom:1px solid var(--line);
    }
    .table-wrap { overflow-x:auto; }
    table {
      width:100%; border-collapse:collapse; min-width: 920px;
    }
    th, td {
      border-bottom:1px solid var(--line);
      padding:10px 12px; vertical-align:top;
      font-size:13px;
      white-space: normal;
      overflow-wrap:anywhere;
      word-break: break-word;
      line-height: 1.25;
    }
    th {
      text-align:left; font-size:12px; color:var(--muted);
      background:#0c142b;
      border-bottom:1px solid var(--line);
    }
    tr:hover td { background:rgba(255,255,255,.02); }
    .mono { font-variant-numeric: tabular-nums; font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace; }
    .muted { color:var(--muted); }
    .pill {
      display:inline-block; padding:4px 8px; border-radius:999px;
      border:1px solid var(--line); background:rgba(255,255,255,.03);
      font-size:12px; color:var(--muted);
    }
    .warn { color:var(--warn); }
    .footer-note {
      margin-top:10px; color:var(--muted); font-size:12px; line-height:1.35;
    }
    .right { text-align:right; }
    @media (max-width: 820px) {
      th { top:150px; }
      input[type="number"], input[type="text"] { width:100%; }
    }
  </style>
</head>
<body>
  <header>
    <div class="wrap">
      <h1>Calculadora de dosis pediátrica por peso</h1>
      <div class="controls">
        <div>
          <label for="peso">Peso del paciente (kg)</label>
          <input id="peso" type="number" min="0" step="0.1" value="10" />
        </div>
        <div>
          <label for="buscar">Buscar medicamento</label>
          <input id="buscar" type="text" placeholder="Ej: amoxicilina, salbutamol..." />
        </div>
        <div class="chip"><span class="muted">Total meds:</span> <b id="count">0</b></div>
        <div class="chip"><span class="muted">Nota:</span> <b class="warn">Verifica siempre en guías y contexto clínico.</b></div>
      </div>
      <div class="footer-note">
        Calcula <span class="pill">TOTAL (mg)</span> y <span class="pill">DOSIS FINAL</span> con las fórmulas del Excel.
        Si en el Excel la “dosis final” decía “IV” u otro texto, aquí se muestra tal cual.
      </div>
    </div>
  </header>

  <main>
    <div class="wrap" id="app"></div>
  </main>

<script>
const DATA = [{"row": 7, "categoria": "ANALGESICOS", "med": "ACETAMINOFEN", "dosis_mgkg": 15.0, "freq": "C/4 - 6 H", "present": "Jar. 150/5  - Fco (90mL).", "total_formula": "=(C7*D7)", "final_formula": "=(E7*5)/150"}, {"row": 8, "categoria": "ANALGESICOS", "med": "DICLOFENACO", "dosis_mgkg": 1.0, "freq": "C/12 H ", "present": "Amp. 75mg/3mL. Grag 50mg                      Sus. 90/5 (Fco 120mL)", "total_formula": "=(C8*D8)", "final_formula": "=(E8/2)"}, {"row": 9, "categoria": "ANALGESICOS", "med": "DIPIRONA", "dosis_mgkg": 20.0, "freq": "C/8 H", "present": "Amp. 2g/5mL. Tab 500mg                      Jar. 250/5 (Fco 60mL)", "total_formula": "=(C9*D9)", "final_formula": "IV"}, {"row": 10, "categoria": "ANALGESICOS", "med": "HIOSCINA", "dosis_mgkg": 10.0, "freq": "C/8 H", "present": "Amp. 20mg/mL. Grag 10mg", "total_formula": "=(C10*D10)", "final_formula": "IV"}, {"row": 11, "categoria": "ANALGESICOS", "med": "IBUPROFENO", "dosis_mgkg": 6.0, "freq": "C/8 H", "present": "Grag. 200 -400 mg                               Sus. 100/5 (Fco 120mL)", "total_formula": "=(C11*D11)", "final_formula": "=(E11*5)/100"}, {"row": 12, "categoria": "ANALGESICOS", "med": "MORFINA", "dosis_mgkg": 0.1, "freq": "Bolo IV", "present": "Amp. 10mg/mL. (1mL)", "total_formula": "=(C12*D12)", "final_formula": "IV"}, {"row": 13, "categoria": "ANALGESICOS", "med": "NAPROXENO", "dosis_mgkg": 20.0, "freq": "C/8 -12 H ", "present": "Susp. 125/5 - Fco (60mL).              Tab 100 - 275 - 550mg.                  ", "total_formula": "=(C13*D13)", "final_formula": "=(E13*5)/125/3"}, {"row": 14, "categoria": "ANALGESICOS", "med": "TRAMADOL", "dosis_mgkg": 1.0, "freq": "C/ 6 - 8 H", "present": "Amp.50-100mg/mL. Gt 40=100mg", "total_formula": "=(C14*D14)", "final_formula": "=E14"}, {"row": 17, "categoria": "ANTIBIOTICOS", "med": "ACIDO NALIDIXICO", "dosis_mgkg": 55.0, "freq": "C/8 H ", "present": "Susp. 250/5  - Fco (120mL)", "total_formula": "=(C17*D17)", "final_formula": "=(E17*5/250)/3"}, {"row": 18, "categoria": "ANTIBIOTICOS", "med": "AMIKACINA", "dosis_mgkg": 15.0, "freq": "C/ 8 - 12 H ", "present": "Amp. 100 -250 - 500/2mL", "total_formula": "=(C18*D18)", "final_formula": "IV"}, {"row": 19, "categoria": "ANTIBIOTICOS", "med": "AMOXICILINA", "dosis_mgkg": 60.0, "freq": "C/8 H X 10 d", "present": "Susp. 250/5  - Fco (100mL)", "total_formula": "=(C19*D19)", "final_formula": "=(E19*5)/250/3"}, {"row": 20, "categoria": "ANTIBIOTICOS", "med": "AMPICILINA", "dosis_mgkg": 100.0, "freq": "C/8 H", "present": "Amp. 500 y 1gr.  Jar. 125-250-500/5 (Fco 90mL)", "total_formula": "=(C20*D20)", "final_formula": "=(E20*5/250)/3"}, {"row": 21, "categoria": "ANTIBIOTICOS", "med": "AMPICILINA/SULBACTAM", "dosis_mgkg": 50.0, "freq": "C/6-12", "present": "Sus. 250/5 (Fco 120mL). Tab.375-750mg. Amp. 0.75 -1.5 -3g", "total_formula": "=(C21*D21)", "final_formula": "=(E21*5/250)/2"}, {"row": 22, "categoria": "ANTIBIOTICOS", "med": "AZITROMICINA", "dosis_mgkg": 10.0, "freq": "C/ DIA X 3 d", "present": "Susp. 200/5 - Fco (15 y 30mL).        Tab 500mg.                  ", "total_formula": "=(C22*D22)", "final_formula": "=(E22*5/200)"}, {"row": 23, "categoria": "ANTIBIOTICOS", "med": "CEFALOTINA", "dosis_mgkg": 150.0, "freq": "C/4-6 H", "present": "Fco.ampolla 1 gr (10mL)", "total_formula": "=(C23*D23)", "final_formula": "IV"}, {"row": 24, "categoria": "ANTIBIOTICOS", "med": "CEFALEXINA", "dosis_mgkg": 50.0, "freq": "C/6 H", "present": "Susp. 250/5 - Fco (100mL).        Tab 500mg  - 1gr                  ", "total_formula": "=(C24*D24)", "final_formula": "=(E24*5)/250/4"}, {"row": 25, "categoria": "ANTIBIOTICOS", "med": "CEFAZOLINA", "dosis_mgkg": 50.0, "freq": "C/8 H", "present": "Amp. 500mg -1gr.", "total_formula": "=(C25*D25)", "final_formula": "IV"}, {"row": 26, "categoria": "ANTIBIOTICOS", "med": "CEFTRIAXONA", "dosis_mgkg": 50.0, "freq": "C/12 - 24 H", "present": "Amp. 250 - 500mg - 1gr", "total_formula": "=(C26*D26)", "final_formula": "IV"}, {"row": 27, "categoria": "ANTIBIOTICOS", "med": "CIPROFLOXACINA", "dosis_mgkg": 20.0, "freq": "C/12 H ", "present": "Susp. 250/5 - Fco (100mL).        Tab 500mg. Gotas 5-10ml                ", "total_formula": "=(C27*D27)", "final_formula": "=(E27*5)/250/2"}, {"row": 28, "categoria": "ANTIBIOTICOS", "med": "CLARITROMICINA", "dosis_mgkg": 15.0, "freq": "C/12 H x 5-10d", "present": "Susp. 250/5 - Fco (50mL).        Tab 250 - 500mg.                ", "total_formula": "=(C28*D28)", "final_formula": "=(E28*5)/250/2"}, {"row": 29, "categoria": "ANTIBIOTICOS", "med": "CLINDAMICINA", "dosis_mgkg": 40.0, "freq": "C/6 H", "present": "Caps 300mg - Amp. 600/4mL", "total_formula": "=(C29*D29)", "final_formula": "IV"}, {"row": 30, "categoria": "ANTIBIOTICOS", "med": "DICLOXACILINA", "dosis_mgkg": 60.0, "freq": "C/6 H", "present": "Susp. 125mg - Fco (100mL).        Caps. 250 - 500mg.                ", "total_formula": "=(C30*D30)", "final_formula": "=(E30/125)/4"}, {"row": 31, "categoria": "ANTIBIOTICOS", "med": "DOXICICLINA", "dosis_mgkg": 5.0, "freq": "C/12 H ", "present": "Caps. 100mg.                ", "total_formula": "=(C31*D31)", "final_formula": "VO"}, {"row": 32, "categoria": "ANTIBIOTICOS", "med": "ERITROMICINA", "dosis_mgkg": 50.0, "freq": "C/6 H X 10d", "present": "Susp. 250/5 - Fco (60mL).              Tab 500mg.                ", "total_formula": "=(C32*D32)", "final_formula": "=(E32*5)/250/4"}, {"row": 33, "categoria": "ANTIBIOTICOS", "med": "GENTAMICINA", "dosis_mgkg": 6.0, "freq": "C/8 H", "present": "Amp. 40mg/ml - 80mg/ml.", "total_formula": "=(C33*D33)", "final_formula": "IV"}, {"row": 34, "categoria": "ANTIBIOTICOS", "med": "METRONIDAZOL", "dosis_mgkg": 15.0, "freq": "C/6 H", "present": "Sln Iny. 100mg/500mL", "total_formula": "=(C34*D34)", "final_formula": "IV"}, {"row": 35, "categoria": "ANTIBIOTICOS", "med": "OXACILINA", "dosis_mgkg": 100.0, "freq": "C/6 H", "present": "Amp. 1g -  2g.", "total_formula": "=(C35*D35)", "final_formula": "IV"}, {"row": 36, "categoria": "ANTIBIOTICOS", "med": "PENICILINA BENZATINICA", "dosis_mgkg": 50000.0, "freq": "DOSIS UNICA", "present": "Fco.amp 1´200.000 - 2´400.000 U", "total_formula": "=(C36*D36)", "final_formula": "IM"}, {"row": 37, "categoria": "ANTIBIOTICOS", "med": "PENICILINA G CRISTALINA", "dosis_mgkg": 50000.0, "freq": "C/6 H", "present": "Fco.ampolla 1´000.000", "total_formula": "=(C37*D37)", "final_formula": "IV"}, {"row": 38, "categoria": "ANTIBIOTICOS", "med": "PENICILINA V ORAL", "dosis_mgkg": 50.0, "freq": "C/6 - 8 H", "present": "Susp. 250/5 - Fco(100mL).              Tab 250-500mg.                ", "total_formula": "=(C38*D38)", "final_formula": "=(E38*5)/250/4"}, {"row": 39, "categoria": "ANTIBIOTICOS", "med": "TRIMETO/SULFAMTXL", "dosis_mgkg": 8.0, "freq": "C/12 H x 5-10d", "present": "Sup.40/200mg/5mL -Fco(100mL).  Tab 80/400mg  Tab160/800mg.                ", "total_formula": "=(C39*D39)", "final_formula": "VO"}, {"row": 42, "categoria": "ANTIVIRALES", "med": "* ACICLOVIR", "dosis_mgkg": 30.0, "freq": "C/6 H x 7-10 d", "present": "Susp. 200/5 - Fco (90mL).        Tab 200 - 400 - 800mg.                    Amp 20mg/mL (10mL)", "total_formula": "=(C42*D42)", "final_formula": "=(E42*5)/200"}, {"row": 45, "categoria": "ANTIPARASITARIOS", "med": "ALBENDAZOL", "dosis_mgkg": 15.0, "freq": "DOSIS UNICA", "present": "Susp. 400/10 - Fco (10mL).        Tab 200 - 400 mg", "total_formula": "=(C45*D45)", "final_formula": "=(E45*10)/400"}, {"row": 46, "categoria": "ANTIPARASITARIOS", "med": "IBERMECTINA", "dosis_mgkg": 1.0, "freq": "DOSIS UNICA", "present": "30got=6mg Fco(5mL). Cap 3mg", "total_formula": "=(C46*D46)", "final_formula": "=(C46*D46)"}, {"row": 47, "categoria": "ANTIPARASITARIOS", "med": "MEBENDAZOL", "dosis_mgkg": 100.0, "freq": "C/12 H X3d", "present": "Tab. 100mg - Sus100/5 (30mL)", "total_formula": "…", "final_formula": ""}, {"row": 48, "categoria": "ANTIPARASITARIOS", "med": "METRONIDAZOL", "dosis_mgkg": 15.0, "freq": "C/8 H x7d", "present": "Susp. 250/5 - Fco (100mL).        Tab 250 - 500mg. Sln Iny 100/500", "total_formula": "=(C48*D48)", "final_formula": "=(E48*5)/250/3"}, {"row": 49, "categoria": "ANTIPARASITARIOS", "med": "PAMOATO DE PIRANTEL", "dosis_mgkg": 10.0, "freq": "DOSIS UNICA", "present": "Susp.250/5-Fco(15mL). Tab250mg", "total_formula": "=(C49*D49)", "final_formula": "=(E49*5)/250"}, {"row": 50, "categoria": "ANTIPARASITARIOS", "med": "SECNIDAZOL", "dosis_mgkg": 30.0, "freq": "DOSIS UNICA", "present": "Susp.500mg-Fco(30mL).                              Tab250-500mg", "total_formula": "=(C50*D50)", "final_formula": "VO"}, {"row": 51, "categoria": "ANTIPARASITARIOS", "med": "TINIDAZOL", "dosis_mgkg": 60.0, "freq": "DOSIS UNICA", "present": "Susp.200/mL-Fco(15mL).Tab500 ", "total_formula": "=(C51*D51)", "final_formula": "=(E51*1)/200"}, {"row": 54, "categoria": "ANTIMICOTICO", "med": "KETOCONAZOL", "dosis_mgkg": 5.0, "freq": "DOSIS UNICA", "present": "Susp.20/1 Fco(60mL). Tab 200", "total_formula": "=(C54*D54)", "final_formula": "=(E54/20)"}, {"row": 55, "categoria": "ANTIMICOTICO", "med": "FLUCONAZOL", "dosis_mgkg": 2.0, "freq": "CADA DIA X 2 S", "present": "Susp. 200/5.  Cap.150-200mg. Vial 2mg/mL.", "total_formula": "=(C55*D55)", "final_formula": "=(E55*5)/200"}, {"row": 56, "categoria": "ANTIMICOTICO", "med": "ANFOTERICINA B", "dosis_mgkg": 0.4, "freq": "En 2-6 H", "present": "Amp. 50/10mL", "total_formula": "=(C56*D56)", "final_formula": "IV"}, {"row": 57, "categoria": "ANTIMICOTICO", "med": "NISTATINA", "dosis_mgkg": 1.0, "freq": "C/6 H x 15d", "present": "Susp. 100.000 U/mL (60mL)", "total_formula": "=(C57*D57)", "final_formula": "VO"}, {"row": 60, "categoria": "ANTIHISTAMINICO", "med": "CETIRIZINA", "dosis_mgkg": 0.5, "freq": "CADA DIA", "present": "Jar.5/5 - Fco (60mL.)Tab. 10mg", "total_formula": "=(C60*D60)", "final_formula": "=(E60*5)/5"}, {"row": 62, "categoria": "ANTIHISTAMINICO", "med": "HIDROXICINA", "dosis_mgkg": 2.0, "freq": "C/ 8 - 12 H", "present": "Jar. 2,5/ml - Fco (120 mL).        Tab 25 mg  Amp. 100/2mL", "total_formula": "=(C62*D62)", "final_formula": "=(E62/2.5)/3"}, {"row": 63, "categoria": "ANTIHISTAMINICO", "med": "KETOTIFENO", "dosis_mgkg": 0.05, "freq": "C/ 12 H", "present": "Jar. 1/5ml - Fco(100 mL).       Tab 1mg   Got. 20=1mg (15mL)", "total_formula": "=(C63*D63)", "final_formula": "=(E63*5)/1/2"}, {"row": 64, "categoria": "ANTIHISTAMINICO", "med": "LORATADINA", "dosis_mgkg": 0.2, "freq": "CADA DIA", "present": "Jar.5/5 - Fco(100mL) Tab 10mg", "total_formula": "=(C64*D64)", "final_formula": "=(E64*5)/5"}, {"row": 67, "categoria": "ANTICONVULSUVANTES", "med": "ACIDO VALPROICO", "dosis_mgkg": 15.0, "freq": "C/12 H", "present": "Jar. 250/5 - Fco (120mL).           Sln Iny 100/ml (vial 5ml).", "total_formula": "=(C67*D67)", "final_formula": "=(E67*5)/250/2"}, {"row": 68, "categoria": "ANTICONVULSUVANTES", "med": "CARBAMAZEPINA", "dosis_mgkg": 10.0, "freq": "C/8 H ", "present": "Susp. 100/5 - Fco (120mL).        Tab 200 - 400 mg", "total_formula": "=(C68*D68)", "final_formula": "=(E68*5)/100"}, {"row": 69, "categoria": "ANTICONVULSUVANTES", "med": "CLONAZEPAM", "dosis_mgkg": 0.03, "freq": "C/8 H ", "present": "Amp.1mg/1ml. Tab. 0,5 -2mg", "total_formula": "=(C69*D69)", "final_formula": "IV"}, {"row": 70, "categoria": "ANTICONVULSUVANTES", "med": "DIAZEPAM", "dosis_mgkg": 0.3, "freq": "DOSIS UNICA", "present": "Amp.5mg/ml (2mL) Tab.10mg", "total_formula": "=(C70*D70)", "final_formula": "IV"}, {"row": 71, "categoria": "ANTICONVULSUVANTES", "med": "FENITOINA", "dosis_mgkg": 10.0, "freq": "Bolo IV.", "present": "Jar. 125/5 - Fco (240mL).           Amp. 50/ml (5ml).", "total_formula": "=(C71*D71)", "final_formula": "IV"}, {"row": 72, "categoria": "ANTICONVULSUVANTES", "med": "FENOBARBITAL", "dosis_mgkg": 3.5, "freq": "C/12 H ", "present": "Amp. 40mg -200/1ml.           Tab. 10 -50mg. Elixir 4mg/mL", "total_formula": "=(C72*D72)", "final_formula": "IV"}, {"row": 73, "categoria": "ANTICONVULSUVANTES", "med": "MIDAZOLAM", "dosis_mgkg": 0.05, "freq": "Bolo IV.", "present": "Amp.5mg/5ml.  - Tab. 7.5mg", "total_formula": "=(C73*D73)", "final_formula": "IV"}, {"row": 76, "categoria": "CORTICOIDES", "med": "BETAMETASONA", "dosis_mgkg": 0.125, "freq": "C/ 6 -12 H", "present": "Amp 4mg/mL - Tab. 0,5 y 2 mg", "total_formula": "=(C76*D76)", "final_formula": "IV"}, {"row": 77, "categoria": "CORTICOIDES", "med": "DEXAMETASONA", "dosis_mgkg": 0.3, "freq": "C/ 6 H", "present": "Amp 4mg/mL - (2mL)", "total_formula": "=(C77*D77)", "final_formula": "IV"}, {"row": 78, "categoria": "CORTICOIDES", "med": "METILPREDNISOLONA", "dosis_mgkg": 10.0, "freq": "Bolo IV.", "present": "Amp 40mg/mL - Tab. 4 y 16 mg", "total_formula": "=(C78*D78)", "final_formula": "IV"}, {"row": 81, "categoria": "ANTIEMETICO", "med": "ALIZAPRIDA", "dosis_mgkg": 5.0, "freq": "C/ 8 - 12 H", "present": "Tab. 50 mg - Amp 50/2mL.  Gotas 20=12mg (0,5mg/gt)", "total_formula": "=(C81*D81)", "final_formula": "IV"}, {"row": 82, "categoria": "ANTIEMETICO", "med": "DOLASETRON", "dosis_mgkg": 1.8, "freq": "DOSIS", "present": "Tab. 100 mg - Sol 10mg/mL", "total_formula": "=(C82*D82)", "final_formula": "IV"}, {"row": 83, "categoria": "ANTIEMETICO", "med": "METOCLOPRAMIDA", "dosis_mgkg": 0.4, "freq": "C/8 H", "present": "Tab. 10 mg - Amp 10/2mL. Gotas (0,2mg/gt) Jar 1mg/ml", "total_formula": "=(C83*D83)", "final_formula": "=(E83/3)"}, {"row": 84, "categoria": "ANTIEMETICO", "med": "*RANITIDINA", "dosis_mgkg": 4.0, "freq": "C/12 ", "present": "Tab. 150-300mg - Amp 50/2mL. Jar 75mg/5ml", "total_formula": "=(C84*D84)", "final_formula": "=(E84*5/75)/2"}, {"row": 87, "categoria": "BRONCODILATADORES", "med": "MONTELUKAST", "dosis_mgkg": 4.0, "freq": "NOCHE", "present": "Tab. 4 -5 - 10mg", "total_formula": "…", "final_formula": "VO"}, {"row": 88, "categoria": "BRONCODILATADORES", "med": "PREDNISOLONA", "dosis_mgkg": 1.0, "freq": "C/ 12 H x3-5d", "present": "Tab5mg - Sol. 1mg/mL (Fco100mL)", "total_formula": "=(C88*D88)", "final_formula": "=(E88*1/1)/2"}, {"row": 89, "categoria": "BRONCODILATADORES", "med": "SALBUTAMOL", "dosis_mgkg": 0.15, "freq": "C/ 6 H", "present": "Jar. 2/5  - Fco (170mL)", "total_formula": "=(C89*D89)", "final_formula": "=(E89*5)/2"}, {"row": 90, "categoria": "BRONCODILATADORES", "med": "TERBUTALINA", "dosis_mgkg": 0.1, "freq": "C/ 6 H", "present": "sol para nebulizar 10mg/Ml.      Jar. 0.3mg/ml (120). Amp 0.5.", "total_formula": "=(C90*D90)", "final_formula": "=(E90*1/0.3)"}, {"row": 93, "categoria": "ACLS - BLS", "med": "ADENOSINA", "dosis_mgkg": 0.1, "freq": "Bolo IV.", "present": "Ampolla. 6mg/2mL", "total_formula": "=(C93*D93)", "final_formula": "IV"}, {"row": 94, "categoria": "ACLS - BLS", "med": "ADRENALINA", "dosis_mgkg": 0.01, "freq": "C/3-5 Min", "present": "Ampolla. 1mg/1mL", "total_formula": "=(C94*D94)", "final_formula": "IV"}, {"row": 95, "categoria": "ACLS - BLS", "med": "ATROPINA", "dosis_mgkg": 0.01, "freq": "DOSIS", "present": "Ampolla. 1mg/1mL", "total_formula": "=(C95*D95)", "final_formula": "IV"}, {"row": 96, "categoria": "ACLS - BLS", "med": "AMIODARONA", "dosis_mgkg": 10.0, "freq": "C/ 12 H X 10 d", "present": "Tabletas. 200mg", "total_formula": "=C96*D96", "final_formula": "VO"}, {"row": 97, "categoria": "ACLS - BLS", "med": "DOBUTAMINA", "dosis_mgkg": 2.5, "freq": "Bolo IV.", "present": "Ampolla. 12,5mg/1mL", "total_formula": "=C97*D97", "final_formula": "IV"}, {"row": 98, "categoria": "ACLS - BLS", "med": "DOPAMINA", "dosis_mgkg": 10.0, "freq": "Bolo IV.", "present": "Ampolla. 40mg/mL", "total_formula": "=C98*D98", "final_formula": "IV"}, {"row": 99, "categoria": "ACLS - BLS", "med": "NOREPINEFRINA", "dosis_mgkg": 0.05, "freq": "Bolo IV.", "present": "Ampolla. 1mg/1mL", "total_formula": "=C99*D99", "final_formula": "IV"}, {"row": 102, "categoria": "INTOXICACIONES", "med": "ALCOHOL ETÍLICO", "dosis_mgkg": 1.0, "freq": "C/ 2 - 4 H", "present": "Alcohol etílico 96º", "total_formula": "=(C102*D102)", "final_formula": "IV"}, {"row": 103, "categoria": "INTOXICACIONES", "med": "ATROPINA", "dosis_mgkg": 0.05, "freq": "C/10 - 20 Min.", "present": "Ampolla. 1mg/1mL", "total_formula": "=(C103*D103)", "final_formula": "IV"}, {"row": 104, "categoria": "INTOXICACIONES", "med": "CARBON ACTIVADO", "dosis_mgkg": 1.0, "freq": "C/ 2 - 4 H", "present": "Polvo. Bolsa 1 Libra", "total_formula": "=(C104*D104)", "final_formula": "VO"}, {"row": 105, "categoria": "INTOXICACIONES", "med": "FLUMAZENIL", "dosis_mgkg": 0.01, "freq": "Bolo IV.", "present": "Ampolla. 0,5mg/5mL", "total_formula": "=(C105*D105)", "final_formula": "IV"}, {"row": 106, "categoria": "INTOXICACIONES", "med": "NALOXONA", "dosis_mgkg": 0.01, "freq": "C/10 - 15 Min.", "present": "Ampolla. 0,4mg/mL", "total_formula": "=(C106*D106)", "final_formula": "IV"}, {"row": 107, "categoria": "INTOXICACIONES", "med": "NEOSTIGMINA", "dosis_mgkg": 0.01, "freq": "C/ 3 - 4 H", "present": "Ampolla. 0,5mg/mL", "total_formula": "=(C107*D107)", "final_formula": "IV"}, {"row": 110, "categoria": "SNC", "med": "AMITRIPTILINA", "dosis_mgkg": 1.0, "freq": "C/ 8 H ", "present": "Tabletas. 10 y 25mg", "total_formula": "=(C110*D110)", "final_formula": "VO"}, {"row": 113, "categoria": "DIARREA", "med": "BISMUTO, SUBSALICILATO", "dosis_mgkg": 100.0, "freq": "C/ 4 H", "present": "Susp. 255/15 - Fco (12mL).        Tab 262 mg", "total_formula": "=(C113*D113)", "final_formula": "=(E113*15/255)/6"}, {"row": 114, "categoria": "DIARREA", "med": "DIFENOXILATO", "dosis_mgkg": 0.2, "freq": "C/ 6 - 8 H", "present": "Tabletas. 2,5mg", "total_formula": "=(C114*D114)", "final_formula": "VO"}, {"row": 115, "categoria": "DIARREA", "med": "LOPERAMIDA", "dosis_mgkg": 0.2, "freq": "C/ 8 - 12H", "present": "Susp.1/5 - Fco(60mL). Tab 2mg", "total_formula": "=(C115*D115)", "final_formula": "=(E115*5)/1/3"}, {"row": 118, "categoria": "ELECTROLITOS", "med": "HIPOK: POTASIO", "dosis_mgkg": 3.0, "freq": "Bolo", "present": "Amp. 2mEq=0,14g/mL. (10mL)", "total_formula": "=(C118*D118)", "final_formula": "IV"}, {"row": 119, "categoria": "ELECTROLITOS", "med": "HIPERK: FUROSEMIDA", "dosis_mgkg": 1.0, "freq": "C/ 2 - 8 H", "present": "Ampolla. 20mg/2mL", "total_formula": "IV", "final_formula": "IV"}];

function fmt(n) {
  if (n === null || n === undefined || Number.isNaN(n)) return "";
  const s = (Math.round(n * 1000) / 1000).toFixed(3);
  return s.replace(/\.0+$/,"").replace(/(\.\d*[1-9])0+$/,"$1");
}

function compileFormula(formula, row, vars) {
  if (!formula || typeof formula !== "string") return null;
  const f = formula.trim();
  if (!f.startsWith("=")) return null;

  let expr = f.slice(1);

  // Reemplazos seguros para referencias de la misma fila.
  // Usamos (?!\d) para evitar confundir C7 con C70, etc.
  expr = expr.replace(new RegExp("C" + row + "(?!\\d)", "g"), "W");
  expr = expr.replace(new RegExp("D" + row + "(?!\\d)", "g"), "DOSE");
  expr = expr.replace(new RegExp("E" + row + "(?!\\d)", "g"), "TOTAL");

  // Permitir SOLO números, operadores, paréntesis, espacios y nombres de variables.
  if (!/^[0-9+\-*/().\sA-Z]+$/.test(expr)) return null;

  try {
    // eslint-disable-next-line no-new-func
    const fn = new Function("W","DOSE","TOTAL", "return (" + expr + ");");
    const out = fn(vars.W, vars.DOSE, vars.TOTAL);
    return (typeof out === "number" && Number.isFinite(out)) ? out : null;
  } catch(e) {
    return null;
  }
}

function groupByCategory(items) {
  const map = new Map();
  for (const it of items) {
    const k = it.categoria || "OTROS";
    if (!map.has(k)) map.set(k, []);
    map.get(k).push(it);
  }
  return map;
}

function render() {
  const pesoRaw = document.getElementById("peso").value;
  const peso = parseFloat(String(pesoRaw).replace(",", ".")); // soporte decimal con coma
  const q = (document.getElementById("buscar").value || "").trim().toLowerCase();

  const filtered = DATA.filter(it => {
    if (!q) return true;
    return (it.med || "").toLowerCase().includes(q) ||
           (it.categoria || "").toLowerCase().includes(q) ||
           (it.present || "").toLowerCase().includes(q);
  });

  document.getElementById("count").textContent = filtered.length;

  const grouped = groupByCategory(filtered);
  const app = document.getElementById("app");
  app.innerHTML = "";

  for (const [cat, arr] of grouped.entries()) {
    const card = document.createElement("div");
    card.className = "card";

    const h2 = document.createElement("h2");
    h2.textContent = cat;
    card.appendChild(h2);

    const wrap = document.createElement("div");
    wrap.className = "table-wrap";

    const table = document.createElement("table");
    table.innerHTML = `
      <thead>
        <tr>
          <th style="width:18%">Medicamento</th>
          <th style="width:12%">Dosis (mg/kg)</th>
          <th style="width:12%">Total (mg)</th>
          <th style="width:34%">Presentación</th>
          <th style="width:12%">Frecuencia</th>
          <th class="right" style="width:12%">Dosis final</th>
        </tr>
      </thead>
      <tbody></tbody>
    `;
    const tbody = table.querySelector("tbody");

    for (const it of arr) {
      const dose = (typeof it.dosis_mgkg === "number") ? it.dosis_mgkg : NaN;

      // TOTAL (mg)
      let total = compileFormula(it.total_formula, it.row, {
        W: peso,
        DOSE: dose,
        TOTAL: NaN
      });
      if (total === null) {
        total = (Number.isFinite(peso) && Number.isFinite(dose)) ? (peso * dose) : null;
      }

      // DOSIS FINAL
      let finalText = "";
      let finalVal = compileFormula(it.final_formula, it.row, {
        W: peso,
        DOSE: dose,
        TOTAL: total
      });

      if (finalVal !== null) {
        finalText = fmt(finalVal);
      } else {
        if (it.final_formula && !it.final_formula.trim().startsWith("=")) {
          // Si la "dosis final" es texto (ej: IV/VO/IM), mostramos la dosis calculada + vía
          if (total !== null && total !== undefined && !Number.isNaN(total)) {
            finalText = fmt(total) + " " + it.final_formula.trim();
          } else {
            finalText = it.final_formula.trim();
          }
        } else {
          finalText = "";
        }
      }

      const tr = document.createElement("tr");
      tr.innerHTML = `
        <td><b>${it.med}</b></td>
        <td class="mono">${fmt(dose)}</td>
        <td class="mono">${fmt(total)}</td>
        <td class="muted">${it.present || ""}</td>
        <td>${it.freq || ""}</td>
        <td class="mono right">${finalText}</td>
      `;
      tbody.appendChild(tr);
    }

    wrap.appendChild(table);
    card.appendChild(wrap);
    app.appendChild(card);
  }
}

document.getElementById("peso").addEventListener("input", render);
document.getElementById("buscar").addEventListener("input", render);
render();
</script>
</body>
</html>