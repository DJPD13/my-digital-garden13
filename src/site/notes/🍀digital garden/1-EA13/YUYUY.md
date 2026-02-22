---
{"dg-publish":true,"permalink":"/digital-garden/1-ea-13/yuyuy/","dgPassFrontmatter":true}
---


<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Checklist Narrativa</title>
  <style>
    body { font-family: Arial, sans-serif; line-height: 1.4; padding: 16px; }
    h1,h2,h3,h4,h5,h6 { margin: 18px 0 8px; }
    .grupo { margin-bottom: 14px; }
    label { display: flex; align-items: center; gap: 8px; margin: 6px 0; }
    input[type="text"] { width: 220px; max-width: 60vw; }
    button { margin-top: 14px; padding: 10px 14px; }
    #resultado { margin-top: 14px; white-space: pre-wrap; }
  </style>
</head>
<body>

  <h1> .</h1>
  <div class="grupo">
    <label>
      <input type="checkbox" id="h1_op1" onchange="handleLink(this)">
      PACIENTE MASCULINO DE <input type="text" id="h1_op1_txt" oninput="/* noop */">ESCRIBIR AÑOS
    </label>
    <label>
      <input type="checkbox" id="h1_op2" onchange="handleLink(this)">
      PACIENTE FEMENINA DE <input type="text" id="h1_op2_txt" oninput="/* noop */">ESCRIBIR AÑOS
    </label>
  </div>

  <h2>CON ANTECEDENTE DE</h2>
  <div class="grupo">
    <label>
      <input type="checkbox" id="h2_op1" onchange="handleLink(this)">
      HIPERTENSIÓN ARTERIAL,
    </label>
    <label>
      <input type="checkbox" id="h2_op2" onchange="handleLink(this)">
      DIABETES MELLITUS TIPO 2 NO INSULINO REQUIRIENTE, ADHERENTE, SIN COMPLICACIONES MACROVASCULARES
    </label>
    <label>
      <input type="checkbox" id="h2_op3" onchange="handleLink(this)">
      DISLIPIDEMIA
    </label>
    <label>
      <input type="checkbox" id="h2_op4" onchange="handleLink(this)">
      ENFERMEDAD RENAL CRONICA,
    </label>
    <label>
      <input type="checkbox" id="h2_op5" onchange="handleLink(this)">
      ENFERMEDAD PULMONAR OBSTRUCTIVA CRONICA MMRC: <input type="text" id="h2_op5_txt" oninput="/* noop */">,
    </label>
    <label>
      <input type="checkbox" id="h2_op6" onchange="handleLink(this)">
      FALLA CARDIACA NYHA: <input type="text" id="h2_op6_txt" oninput="/* noop */">,
    </label>
    <label>
      <input type="checkbox" id="h2_op7" onchange="handleLink(this)">
      HIPOTIROIDISMO,
    </label>
    <label>
      <input type="checkbox" id="h2_op8" onchange="handleLink(this)">
      FIBRILACIÓN AURICULAR,
    </label>
    <label>
      <input type="checkbox" id="h2_op9" onchange="handleLink(this)">
      TABAQUISMO PESADO CON IPA: ACTIVO/ABANDONO HACE <input type="text" id="h2_op9_txt" oninput="/* noop */">
    </label>
    <label>
      <input type="checkbox" id="h2_op10" onchange="handleLink(this)">
      EXPOSICIÓN A BIOMASA
    </label>
    <label>
      <input type="checkbox" id="h2_op11" onchange="handleLink(this)">
      ALERGIA A <input type="text" id="h2_op11_txt" oninput="/* noop */">,
    </label>
    <label>
      <input type="checkbox" id="h2_op12" onchange="handleLink(this)">
      HOSPITALIZACIÓN EN LOS ULTIMOS 3 MESES POR <input type="text" id="h2_op12_txt" oninput="/* noop */">
    </label>
    <label>
      <input type="checkbox" id="h2_op13" data-link="h4_op2" onchange="handleLink(this)">
      VIH
    </label>
    <label>
      <input type="checkbox" id="h2_op14" onchange="handleLink(this)">
      CANCER DE 
    </label>
  </div>

  <h3> ,</h3>
  <div class="grupo">
    <label>
      <input type="checkbox" id="h3_op1" onchange="handleLink(this)">
      ACUDE SIN ACOMPAÑANTE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE
    </label>
    <label>
      <input type="checkbox" id="h3_op2" onchange="handleLink(this)">
      ACUDE AL SERVICIO DE URGENCIAS CON ACOMPAÑANTE (<input type="text" id="h3_op2_txt" oninput="/* noop */">) 
    </label>
  </div>

  <h4> ,</h4>
  <div class="grupo">
    <label>
      <input type="checkbox" id="h4_op1" onchange="handleLink(this)">
      REFIRIENDO CUADRO CLINICO DE <input type="text" id="h4_op1_txt" oninput="/* noop */"> HORAS DE EVOLUCIÓN CONSISTENTE EN
    </label>
    <label>
      <input type="checkbox" id="h4_op2" onchange="handleLink(this)">
      REFIRIENDO CUADRO CLINICO DE <input type="text" id="h4_op2_txt" oninput="/* noop */"> DÍAS DE EVOLUCIÓN CONSISTENTE EN
    </label>
    <label>
      <input type="checkbox" id="h4_op3" onchange="handleLink(this)">
      REFIRIENDO CUADRO CLINICO DE <input type="text" id="h4_op3_txt" oninput="/* noop */"> MESES DE EVOLUCIÓN CONSISTENTE
    </label>
  </div>

  <button onclick="updateNarrativa()">Generar Narrativa</button>
  <p id="resultado"></p>

  <script>
    function handleLink(sourceCb) {
      const targetId = sourceCb.getAttribute("data-link");
      if (!targetId) return;
      const target = document.getElementById(targetId);
      if (!target) return;
      target.checked = sourceCb.checked;
    }

    function updateNarrativa() {
      const checks = document.querySelectorAll("input[type=checkbox]");
      let narrativa = "";

      // HEADER 1 title
      narrativa += " . ";

      // h1_op1: PACIENTE MASCULINO DE **ESCRIBIR AÑOS
      if (checks[0].checked) {
        narrativa += "PACIENTE MASCULINO DE ";
        const v = document.getElementById("h1_op1_txt").value.trim();
        if (v !== "") narrativa += v + " ";
        narrativa += "ESCRIBIR AÑOS ";
      }

      // h1_op2: PACIENTE FEMENINA DE **ESCRIBIR AÑOS
      if (checks[1].checked) {
        narrativa += "PACIENTE FEMENINA DE ";
        const v = document.getElementById("h1_op2_txt").value.trim();
        if (v !== "") narrativa += v + " ";
        narrativa += "ESCRIBIR AÑOS ";
      }

      // HEADER 2 title
      narrativa += "CON ANTECEDENTE DE ";

      if (checks[2].checked) narrativa += "HIPERTENSIÓN ARTERIAL, ";
      if (checks[3].checked) narrativa += "DIABETES MELLITUS TIPO 2 NO INSULINO REQUIRIENTE, ADHERENTE, SIN COMPLICACIONES MACROVASCULARES ";
      if (checks[4].checked) narrativa += "DISLIPIDEMIA ";
      if (checks[5].checked) narrativa += "ENFERMEDAD RENAL CRONICA, ";

      // h2_op5: ENFERMEDAD PULMONAR OBSTRUCTIVA CRONICA MMRC: **,
      if (checks[6].checked) {
        narrativa += "ENFERMEDAD PULMONAR OBSTRUCTIVA CRONICA MMRC: ";
        const v = document.getElementById("h2_op5_txt").value.trim();
        if (v !== "") narrativa += v + " ";
        narrativa += ", ";
      }

      // h2_op6: FALLA CARDIACA NYHA: **,
      if (checks[7].checked) {
        narrativa += "FALLA CARDIACA NYHA: ";
        const v = document.getElementById("h2_op6_txt").value.trim();
        if (v !== "") narrativa += v + " ";
        narrativa += ", ";
      }

      if (checks[8].checked) narrativa += "HIPOTIROIDISMO, ";
      if (checks[9].checked) narrativa += "FIBRILACIÓN AURICULAR, ";

      // h2_op9: TABAQUISMO PESADO CON IPA: ACTIVO/ABANDONO HACE **
      if (checks[10].checked) {
        narrativa += "TABAQUISMO PESADO CON IPA: ACTIVO/ABANDONO HACE ";
        const v = document.getElementById("h2_op9_txt").value.trim();
        if (v !== "") narrativa += v + " ";
      }

      if (checks[11].checked) narrativa += "EXPOSICIÓN A BIOMASA ";

      // h2_op11: ALERGIA A **,
      if (checks[12].checked) {
        narrativa += "ALERGIA A ";
        const v = document.getElementById("h2_op11_txt").value.trim();
        if (v !== "") narrativa += v + " ";
        narrativa += ", ";
      }

      // h2_op12: HOSPITALIZACIÓN EN LOS ULTIMOS 3 MESES POR **
      if (checks[13].checked) {
        narrativa += "HOSPITALIZACIÓN EN LOS ULTIMOS 3 MESES POR ";
        const v = document.getElementById("h2_op12_txt").value.trim();
        if (v !== "") narrativa += v + " ";
      }

      // h2_op13: VIH (CONECTAR CON OPCION 2 DE HEADER 4) -> label shows "VIH"
      if (checks[14].checked) narrativa += "VIH ";

      // h2_op14: CANCER DE 
      if (checks[15].checked) narrativa += "CANCER DE  ";

      // HEADER 3 title
      narrativa += " , ";

      if (checks[16].checked) narrativa += "ACUDE SIN ACOMPAÑANTE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE ";

      // h3_op2: ACUDE AL SERVICIO DE URGENCIAS CON ACOMPAÑANTE (**)  -> parentheses are NOT command, so keep parentheses visible
      if (checks[17].checked) {
        narrativa += "ACUDE AL SERVICIO DE URGENCIAS CON ACOMPAÑANTE (";
        const v = document.getElementById("h3_op2_txt").value.trim();
        if (v !== "") narrativa += v + " ";
        narrativa += ")  ";
      }

      // HEADER 4 title
      narrativa += " , ";

      // h4_op1
      if (checks[18].checked) {
        narrativa += "REFIRIENDO CUADRO CLINICO DE ";
        const v = document.getElementById("h4_op1_txt").value.trim();
        if (v !== "") narrativa += v + " ";
        narrativa += "HORAS DE EVOLUCIÓN CONSISTENTE EN ";
      }

      // h4_op2
      if (checks[19].checked) {
        narrativa += "REFIRIENDO CUADRO CLINICO DE ";
        const v = document.getElementById("h4_op2_txt").value.trim();
        if (v !== "") narrativa += v + " ";
        narrativa += "DÍAS DE EVOLUCIÓN CONSISTENTE EN ";
      }

      // h4_op3
      if (checks[20].checked) {
        narrativa += "REFIRIENDO CUADRO CLINICO DE ";
        const v = document.getElementById("h4_op3_txt").value.trim();
        if (v !== "") narrativa += v + " ";
        narrativa += "MESES DE EVOLUCIÓN CONSISTENTE ";
      }

      document.getElementById("resultado").textContent = narrativa.trim();
    }
  </script>

</body>
</html>