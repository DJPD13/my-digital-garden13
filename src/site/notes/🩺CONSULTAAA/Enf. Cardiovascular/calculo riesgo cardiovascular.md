---
{"dg-publish":true,"permalink":"/consultaaa/enf-cardiovascular/calculo-riesgo-cardiovascular/","dgPassFrontmatter":true}
---

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>eGFR CKD-EPI 2021</title>
  <style>
    body{
      font-family:Arial;
      background:#0f172a;
      color:white;
      padding:20px;
      max-width:800px;
      margin:auto;
    }
    .card{
      background:#111827;
      padding:20px;
      border-radius:12px;
      margin-bottom:15px;
    }
    input,select{
      width:100%;
      padding:10px;
      margin-top:5px;
      margin-bottom:10px;
      border-radius:8px;
      border:1px solid #334155;
      background:#1f2937;
      color:white;
    }
    button{
      background:#22c55e;
      border:none;
      padding:12px;
      border-radius:10px;
      font-weight:bold;
      cursor:pointer;
      width:100%;
    }
    .result{
      font-size:32px;
      font-weight:bold;
      color:#22c55e;
    }
    pre{
      background:black;
      padding:10px;
      border-radius:10px;
    }
  </style>
</head>
<body>

<div class="card">
  <h2>eGFR CKD-EPI 2021 (Creatinina)</h2>

  <label>Edad</label>
  <input id="age" type="number" value="55">

  <label>Sexo</label>
  <select id="sex">
    <option value="male">Masculino</option>
    <option value="female">Femenino</option>
  </select>

  <label>Creatinina</label>
  <input id="scr" type="number" value="1.1" step="0.01">

  <label>Unidad</label>
  <select id="unit">
    <option value="mg">mg/dL</option>
    <option value="umol">µmol/L</option>
  </select>

  <button onclick="calc()">Calcular</button>
</div>

<div class="card">
  <div class="result" id="result">—</div>
  <div id="stage"></div>
</div>

<div class="card">
  <h3>Resumen</h3>
  <pre id="summary"></pre>
</div>

<script>
function convertScr(value, unit){
  if(unit === "umol") return value / 88.4;
  return value;
}

// CKD-EPI 2021 creatinina
function egfr(age, sex, scr){
  const k = sex === "female" ? 0.7 : 0.9;
  const a = sex === "female" ? -0.241 : -0.302;
  const femaleFactor = sex === "female" ? 1.012 : 1;

  const ratio = scr / k;

  return 142 *
    Math.pow(Math.min(ratio,1), a) *
    Math.pow(Math.max(ratio,1), -1.200) *
    Math.pow(0.9938, age) *
    femaleFactor;
}

function stage(gfr){
  if(gfr >= 90) return "G1";
  if(gfr >= 60) return "G2";
  if(gfr >= 45) return "G3a";
  if(gfr >= 30) return "G3b";
  if(gfr >= 15) return "G4";
  return "G5";
}

function calc(){
  const age = Number(document.getElementById("age").value);
  const sex = document.getElementById("sex").value;
  const scrInput = Number(document.getElementById("scr").value);
  const unit = document.getElementById("unit").value;

  if(age < 18){
    alert("Edad debe ser ≥18");
    return;
  }

  const scr = convertScr(scrInput, unit);
  const gfr = egfr(age, sex, scr);
  const gfrMs = gfr * 0.0167;
  const st = stage(gfr);

  document.getElementById("result").innerText =
    gfr.toFixed(1) + " mL/min/1.73m²";

  document.getElementById("stage").innerText =
    "Estadio: " + st;

  document.getElementById("summary").innerText =
`Edad: ${age}
Sexo: ${sex}
Creatinina: ${scrInput} ${unit === "mg" ? "mg/dL" : "µmol/L"}
Creatinina convertida: ${scr.toFixed(3)} mg/dL

=== RESULTADO ===
eGFR: ${gfr.toFixed(1)} mL/min/1.73m²
eGFR: ${gfrMs.toFixed(2)} mL/s/1.73m²
Estadio: ${st}`;
}
</script>

</body>
</html>



<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>PREVENT Offline - Base Model</title>
  <style>
    :root{
      --bg:#0f172a;
      --panel:#111827;
      --panel2:#1f2937;
      --line:#334155;
      --text:#e5e7eb;
      --muted:#94a3b8;
      --ok:#22c55e;
      --warn:#f59e0b;
      --err:#ef4444;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family:Arial, Helvetica, sans-serif;
      background:linear-gradient(180deg,#020617,#0f172a);
      color:var(--text);
      padding:24px;
    }
    .container{max-width:1150px;margin:0 auto}
    .card{
      background:rgba(17,24,39,.96);
      border:1px solid var(--line);
      border-radius:16px;
      padding:20px;
      margin-bottom:18px;
    }
    h1,h2{margin:0 0 12px}
    p{color:var(--muted);line-height:1.5}
    .grid{
      display:grid;
      grid-template-columns:repeat(12,1fr);
      gap:14px;
    }
    .field{grid-column:span 4}
    .field.full{grid-column:1 / -1}
    @media(max-width:900px){ .field{grid-column:span 12} }
    label{
      display:block;
      margin-bottom:6px;
      font-size:14px;
      font-weight:700;
    }
    input,select{
      width:100%;
      padding:11px 12px;
      border-radius:10px;
      border:1px solid var(--line);
      background:var(--panel2);
      color:var(--text);
      font-size:15px;
    }
    .actions{
      display:flex;
      gap:12px;
      flex-wrap:wrap;
      margin-top:14px;
    }
    button{
      border:none;
      border-radius:12px;
      padding:12px 18px;
      font-weight:700;
      cursor:pointer;
    }
    .primary{background:var(--ok);color:#052e16}
    .secondary{background:#334155;color:#f8fafc}
    .status{font-size:14px;color:var(--muted);margin-bottom:8px}
    .result{
      font-size:40px;
      font-weight:800;
      color:var(--ok);
      margin:8px 0;
    }
    .sub{font-size:14px;color:var(--muted)}
    .results-grid{
      display:grid;
      grid-template-columns:repeat(3,1fr);
      gap:14px;
      margin-top:16px;
    }
    .mini{
      background:#0b1220;
      border:1px solid var(--line);
      border-radius:12px;
      padding:14px;
    }
    .mini .k{font-size:13px;color:var(--muted)}
    .mini .v{font-size:28px;font-weight:800;margin-top:4px}
    @media(max-width:900px){ .results-grid{grid-template-columns:1fr} }
    pre{
      background:#020617;
      border:1px solid var(--line);
      border-radius:12px;
      padding:14px;
      color:#dbeafe;
      white-space:pre-wrap;
      word-break:break-word;
      overflow:auto;
    }
    .ok{color:#86efac}
    .warn{color:#fbbf24}
    .err{color:#fca5a5}
    .note{
      font-size:13px;
      color:#cbd5e1;
      background:#0b1220;
      border:1px solid var(--line);
      border-radius:12px;
      padding:12px;
      margin-top:12px;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="card">
      <h1>Calculadora PREVENT Offline</h1>
      <p>
        Versión totalmente offline en HTML + JavaScript puro.
        Calcula el <strong>PREVENT Base Model</strong> sin internet.
      </p>
      <div class="note">
        Esta versión calcula: Total CVD, ASCVD y Heart Failure a 10 y 30 años.
        No usa HbA1c, UACR ni ZIP/SDI en esta edición offline.
      </div>
    </div>

    <div class="card">
      <h2>Datos del paciente</h2>
      <div class="grid">
        <div class="field">
          <label for="age">Edad (30–79)</label>
          <input id="age" type="number" min="30" max="79" step="1" value="55">
        </div>

        <div class="field">
          <label for="sex">Sexo</label>
          <select id="sex">
            <option value="female">Femenino</option>
            <option value="male">Masculino</option>
          </select>
        </div>

        <div class="field">
          <label for="sbp">Presión sistólica (mmHg)</label>
          <input id="sbp" type="number" min="80" max="220" step="1" value="130">
        </div>

        <div class="field">
          <label for="bp_tx">Tratamiento antihipertensivo</label>
          <select id="bp_tx">
            <option value="false">No</option>
            <option value="true">Sí</option>
          </select>
        </div>

        <div class="field">
          <label for="total_c">Colesterol total</label>
          <input id="total_c" type="number" min="50" max="500" step="0.1" value="200">
        </div>

        <div class="field">
          <label for="hdl_c">HDL</label>
          <input id="hdl_c" type="number" min="10" max="150" step="0.1" value="50">
        </div>

        <div class="field">
          <label for="statin">Usa estatina</label>
          <select id="statin">
            <option value="false">No</option>
            <option value="true">Sí</option>
          </select>
        </div>

        <div class="field">
          <label for="dm">Diabetes mellitus</label>
          <select id="dm">
            <option value="false">No</option>
            <option value="true">Sí</option>
          </select>
        </div>

        <div class="field">
          <label for="smoking">Fumador actual</label>
          <select id="smoking">
            <option value="false">No</option>
            <option value="true">Sí</option>
          </select>
        </div>

        <div class="field">
          <label for="bmi">BMI (kg/m²)</label>
          <input id="bmi" type="number" min="10" max="80" step="0.1" value="25">
        </div>

        <div class="field">
          <label for="egfr">eGFR (mL/min/1.73m²)</label>
          <input id="egfr" type="number" min="1" max="200" step="0.1" value="90">
        </div>
      </div>

      <div class="actions">
        <button class="primary" id="btnCalc">Calcular riesgo</button>
        <button class="secondary" id="btnEjemplo">Cargar ejemplo</button>
      </div>
    </div>

    <div class="card">
      <h2>Resultado principal</h2>
      <div id="status" class="status">Listo para calcular.</div>
      <div id="mainResult" class="result">—</div>
      <div id="subResult" class="sub">Se mostrará el riesgo total CVD a 10 años.</div>

      <div class="results-grid">
        <div class="mini">
          <div class="k">Total CVD 10 años</div>
          <div class="v" id="r10_total">—</div>
        </div>
        <div class="mini">
          <div class="k">ASCVD 10 años</div>
          <div class="v" id="r10_ascvd">—</div>
        </div>
        <div class="mini">
          <div class="k">Heart Failure 10 años</div>
          <div class="v" id="r10_hf">—</div>
        </div>
        <div class="mini">
          <div class="k">Total CVD 30 años</div>
          <div class="v" id="r30_total">—</div>
        </div>
        <div class="mini">
          <div class="k">ASCVD 30 años</div>
          <div class="v" id="r30_ascvd">—</div>
        </div>
        <div class="mini">
          <div class="k">Heart Failure 30 años</div>
          <div class="v" id="r30_hf">—</div>
        </div>
      </div>
    </div>

    <div class="card">
      <h2>Texto con todas las variables</h2>
      <pre id="summaryText">Aquí aparecerán las variables y el resultado.</pre>
    </div>

    <div class="card">
      <h2>Salida técnica JSON</h2>
      <pre id="rawOutput">Aquí aparecerá la salida técnica.</pre>
    </div>
  </div>

  <script>
    const $ = (id) => document.getElementById(id);

    const COEFS = {
      base10: {
        total_cvd: {
          female: [0.7939329,0,0.0305239,-0.1606857,-0.2394003,0.3600781,0.8667604,0.5360739,0,0,0.6045917,0.0433769,0.3151672,-0.1477655,-0.0663612,0.1197879,-0.0819715,0.0306769,-0.0946348,-0.27057,-0.078715,0,-0.1637806,-3.307728],
          male:   [0.7688528,0,0.0736174,-0.0954431,-0.4347345,0.3362658,0.7692857,0.4386871,0,0,0.5378979,0.0164827,0.288879,-0.1337349,-0.0475924,0.150273,-0.0517874,0.0191169,-0.1049477,-0.2251948,-0.0895067,0,-0.1543702,-3.031168]
        },
        ascvd: {
          female: [0.719883,0,0.1176967,-0.151185,-0.0835358,0.3592852,0.8348585,0.4831078,0,0,0.4864619,0.0397779,0.2265309,-0.0592374,-0.0395762,0.0844423,-0.0567839,0.0325692,-0.1035985,-0.2417542,-0.0791142,0,-0.1671492,-3.819975],
          male:   [0.7099847,0,0.1658663,-0.1144285,-0.2837212,0.3239977,0.7189597,0.3956973,0,0,0.3690075,0.0203619,0.2036522,-0.0865581,-0.0322916,0.114563,-0.0300005,0.0232747,-0.0927024,-0.2018525,-0.0970527,0,-0.1217081,-3.500655]
        },
        heart_failure: {
          female: [0.8998235,0,0,0,-0.4559771,0.3576505,1.038346,0.583916,-0.0072294,0.2997706,0.7451638,0.0557087,0.3534442,0,-0.0981511,0,0,0,-0.0946663,-0.3581041,-0.1159453,-0.003878,-0.1884289,-4.310409],
          male:   [0.8972642,0,0,0,-0.6811466,0.3634461,0.923776,0.5023736,-0.0485841,0.3726929,0.6926917,0.0251827,0.2980922,0,-0.0497731,0,0,0,-0.1289201,-0.3040924,-0.1401688,0.0068126,-0.1797778,-3.946391]
        }
      },
      base30: {
        total_cvd: {
          female: [0.5503079,-0.0928369,0.0409794,-0.1663306,-0.1628654,0.3299505,0.6793894,0.3196112,0,0,0.1857101,0.0553528,0.2894,-0.075688,-0.056367,0.1071019,-0.0751438,0.0301786,-0.0998776,-0.3206166,-0.1607862,0,-0.1450788,-1.318827],
          male:   [0.4627309,-0.0984281,0.0836088,-0.1029824,-0.2140352,0.2904325,0.5331276,0.2141914,0,0,0.1155556,0.0603775,0.232714,-0.0272112,-0.0384488,0.134192,-0.0511759,0.0165865,-0.1101437,-0.2585943,-0.1566406,0,-0.1166776,-1.148204]
        },
        ascvd: {
          female: [0.4669202,-0.0893118,0.1256901,-0.1542255,-0.0018093,0.322949,0.6296707,0.268292,0,0,0.100106,0.0499663,0.1875292,0.0152476,-0.0276123,0.0736147,-0.0521962,0.0316918,-0.1046101,-0.2727793,-0.1530907,0,-0.1299149,-1.974074],
          male:   [0.3994099,-0.0937484,0.1744643,-0.120203,-0.0665117,0.2753037,0.4790257,0.1782635,0,0,-0.0218789,0.0602553,0.1421182,0.0135996,-0.0218265,0.1013148,-0.0312619,0.020673,-0.0920935,-0.2159947,-0.1548811,0,-0.0712547,-1.736444]
        },
        heart_failure: {
          female: [0.6254374,-0.0983038,0,0,-0.3919241,0.3142295,0.8330787,0.3438651,0.0594874,0.2525536,0.2981642,0.0667159,0.333921,0,-0.0893177,0,0,0,-0.0974299,-0.404855,-0.1982991,-0.0035619,-0.1564215,-2.205379],
          male:   [0.5681541,-0.1048388,0,0,-0.4761564,0.30324,0.6840338,0.2656273,0.0833107,0.26999,0.2541805,0.0638923,0.2583631,0,-0.0391938,0,0,0,-0.1269124,-0.3273572,-0.2043019,-0.0182831,-0.1342618,-1.95751]
        }
      }
    };

    function toBool(id){ return $(id).value === "true"; }
    function toNum(id){ return Number($(id).value); }

    function fmtPct(x){
      if (x === null || x === undefined || Number.isNaN(x)) return "N/D";
      return (x * 100).toFixed(1) + "%";
    }

    function clampMin(v, x){ return Math.min(v, x); }
    function clampMax(v, x){ return Math.max(v, x); }

    function getInputs(){
      return {
        age: toNum("age"),
        sex: $("sex").value,
        sbp: toNum("sbp"),
        bp_tx: toBool("bp_tx") ? 1 : 0,
        total_c: toNum("total_c"),
        hdl_c: toNum("hdl_c"),
        statin: toBool("statin") ? 1 : 0,
        dm: toBool("dm") ? 1 : 0,
        smoking: toBool("smoking") ? 1 : 0,
        bmi: toNum("bmi"),
        egfr: toNum("egfr")
      };
    }

    function validate(i){
      const req = ["age","sbp","total_c","hdl_c","bmi","egfr"];
      for (const k of req){
        if (Number.isNaN(i[k])) return "Campo inválido: " + k;
      }
      if (i.age < 30 || i.age > 79) return "Edad fuera de rango. PREVENT usa 30–79 años.";
      if (i.hdl_c <= 0) return "HDL debe ser mayor que 0.";
      if (i.total_c <= 0) return "Colesterol total debe ser mayor que 0.";
      return null;
    }

    function buildTerms(i){
      const age10 = (i.age - 55) / 10;
      const age10sq = age10 * age10;
      const nonHdl = (i.total_c - i.hdl_c) * 0.02586 - 3.5;
      const hdlNorm = (i.hdl_c * 0.02586 - 1.3) / 0.3;
      const sbpLow = (Math.min(i.sbp, 110) - 110) / 20;
      const sbpHigh = (Math.max(i.sbp, 110) - 130) / 20;
      const bmiLow = (Math.min(i.bmi, 30) - 25) / 5;
      const bmiHigh = (Math.max(i.bmi, 30) - 30) / 5;
      const egfrLow = (Math.min(i.egfr, 60) - 60) / -15;
      const egfrHigh = (Math.max(i.egfr, 60) - 90) / -15;

      return {
        age10,
        age10sq,
        nonHdl,
        hdlNorm,
        sbpLow,
        sbpHigh,
        dm: i.dm,
        smoking: i.smoking,
        bmiLow,
        bmiHigh,
        egfrLow,
        egfrHigh,
        bp_tx: i.bp_tx,
        statin: i.statin,
        bpTx_sbpHigh: i.bp_tx * sbpHigh,
        statin_nonHdl: i.statin * nonHdl,
        age_nonHdl: age10 * nonHdl,
        age_hdl: age10 * hdlNorm,
        age_sbpHigh: age10 * sbpHigh,
        age_dm: age10 * i.dm,
        age_smoking: age10 * i.smoking,
        bmiHigh_again: bmiHigh,
        age_egfrLow: age10 * egfrLow
      };
    }

    function logistic(x){
      return Math.exp(x) / (1 + Math.exp(x));
    }

    function calcEndpoint(i, coeffSet){
      const c = coeffSet[i.sex];
      const t = buildTerms(i);

      const logit =
        c[0]  * t.age10 +
        c[1]  * t.age10sq +
        c[2]  * t.nonHdl +
        c[3]  * t.hdlNorm +
        c[4]  * t.sbpLow +
        c[5]  * t.sbpHigh +
        c[6]  * t.dm +
        c[7]  * t.smoking +
        c[8]  * t.bmiLow +
        c[9]  * t.bmiHigh +
        c[10] * t.egfrLow +
        c[11] * t.egfrHigh +
        c[12] * t.bp_tx +
        c[13] * t.statin +
        c[14] * t.bpTx_sbpHigh +
        c[15] * t.statin_nonHdl +
        c[16] * t.age_nonHdl +
        c[17] * t.age_hdl +
        c[18] * t.age_sbpHigh +
        c[19] * t.age_dm +
        c[20] * t.age_smoking +
        c[21] * t.bmiHigh_again +
        c[22] * t.age_egfrLow +
        c[23];

      return logistic(logit);
    }

    function calculatePreventBase(i){
      const r10 = {
        total_cvd: calcEndpoint(i, COEFS.base10.total_cvd),
        ascvd: calcEndpoint(i, COEFS.base10.ascvd),
        heart_failure: calcEndpoint(i, COEFS.base10.heart_failure)
      };

      const r30 = {
        total_cvd: calcEndpoint(i, COEFS.base30.total_cvd),
        ascvd: calcEndpoint(i, COEFS.base30.ascvd),
        heart_failure: calcEndpoint(i, COEFS.base30.heart_failure)
      };

      return { model: "PREVENT base offline", risk_10y: r10, risk_30y: r30 };
    }

    function buildSummary(i, r){
      return [
        "=== VARIABLES INGRESADAS ===",
        "Edad: " + i.age,
        "Sexo: " + (i.sex === "female" ? "Femenino" : "Masculino"),
        "Presión sistólica: " + i.sbp + " mmHg",
        "Tratamiento antihipertensivo: " + (i.bp_tx ? "Sí" : "No"),
        "Colesterol total: " + i.total_c + " mg/dL",
        "HDL: " + i.hdl_c + " mg/dL",
        "Estatina: " + (i.statin ? "Sí" : "No"),
        "Diabetes mellitus: " + (i.dm ? "Sí" : "No"),
        "Fumador actual: " + (i.smoking ? "Sí" : "No"),
        "BMI: " + i.bmi + " kg/m²",
        "eGFR: " + i.egfr + " mL/min/1.73m²",
        "",
        "=== RESULTADOS ===",
        "Modelo: " + r.model,
        "Riesgo total CVD 10 años: " + fmtPct(r.risk_10y.total_cvd),
        "Riesgo ASCVD 10 años: " + fmtPct(r.risk_10y.ascvd),
        "Riesgo Heart Failure 10 años: " + fmtPct(r.risk_10y.heart_failure),
        "Riesgo total CVD 30 años: " + fmtPct(r.risk_30y.total_cvd),
        "Riesgo ASCVD 30 años: " + fmtPct(r.risk_30y.ascvd),
        "Riesgo Heart Failure 30 años: " + fmtPct(r.risk_30y.heart_failure)
      ].join("\n");
    }

    function setExample(){
      $("age").value = 55;
      $("sex").value = "female";
      $("sbp").value = 145;
      $("bp_tx").value = "true";
      $("total_c").value = 210;
      $("hdl_c").value = 45;
      $("statin").value = "false";
      $("dm").value = "true";
      $("smoking").value = "false";
      $("bmi").value = 31;
      $("egfr").value = 82;
    }

    function calculate(){
      const i = getInputs();
      const err = validate(i);

      if (err){
        $("status").textContent = err;
        $("status").className = "status err";
        return;
      }

      const r = calculatePreventBase(i);

      $("status").textContent = "Cálculo completado correctamente.";
      $("status").className = "status ok";

      $("mainResult").textContent = fmtPct(r.risk_10y.total_cvd);
      $("subResult").textContent =
        "ASCVD 10 años: " + fmtPct(r.risk_10y.ascvd) +
        " · Heart Failure 10 años: " + fmtPct(r.risk_10y.heart_failure);

      $("r10_total").textContent = fmtPct(r.risk_10y.total_cvd);
      $("r10_ascvd").textContent = fmtPct(r.risk_10y.ascvd);
      $("r10_hf").textContent = fmtPct(r.risk_10y.heart_failure);
      $("r30_total").textContent = fmtPct(r.risk_30y.total_cvd);
      $("r30_ascvd").textContent = fmtPct(r.risk_30y.ascvd);
      $("r30_hf").textContent = fmtPct(r.risk_30y.heart_failure);

      $("summaryText").textContent = buildSummary(i, r);
      $("rawOutput").textContent = JSON.stringify({
        inputs: i,
        results: r
      }, null, 2);
    }

    $("btnCalc").addEventListener("click", calculate);
    $("btnEjemplo").addEventListener("click", setExample);

    setExample();
  </script>
</body>
</html>

