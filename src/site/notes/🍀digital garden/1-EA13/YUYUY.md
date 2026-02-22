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
    body {
      font-family: Arial, sans-serif;
      line-height: 1.3;
      padding: 12px;
      font-size: 13px;
    }

    h1 { font-size: 16px; margin: 14px 0 6px; }
    h2 { font-size: 15px; margin: 14px 0 6px; }
    h3 { font-size: 14px; margin: 14px 0 6px; }
    h4 { font-size: 14px; margin: 14px 0 6px; }

    .grupo { margin-bottom: 10px; }

    label {
      display: flex;
      align-items: center;
      gap: 6px;
      margin: 4px 0;
      font-size: 13px;
    }

    input[type="text"] {
      width: 160px;
      font-size: 12px;
    }

    button {
      margin-top: 12px;
      padding: 6px 10px;
      font-size: 13px;
    }

    #resultado {
      margin-top: 12px;
      font-size: 13px;
      white-space: pre-wrap;
    }
  </style>
</head>

<body>

  <h1> .</h1>
  <div class="grupo">
    <label><input type="checkbox" id="h1_op1" onchange="handleLink(this)">PACIENTE MASCULINO DE <input type="text" id="h1_op1_txt">ESCRIBIR AÑOS</label>
    <label><input type="checkbox" id="h1_op2" onchange="handleLink(this)">PACIENTE FEMENINA DE <input type="text" id="h1_op2_txt">ESCRIBIR AÑOS</label>
  </div>

  <h2>CON ANTECEDENTE DE</h2>
  <div class="grupo">
    <label><input type="checkbox" id="h2_op1" onchange="handleLink(this)">HIPERTENSIÓN ARTERIAL,</label>
    <label><input type="checkbox" id="h2_op2" onchange="handleLink(this)">DIABETES MELLITUS TIPO 2 NO INSULINO REQUIRIENTE, ADHERENTE, SIN COMPLICACIONES MACROVASCULARES</label>
    <label><input type="checkbox" id="h2_op3" onchange="handleLink(this)">DISLIPIDEMIA</label>
    <label><input type="checkbox" id="h2_op4" onchange="handleLink(this)">ENFERMEDAD RENAL CRONICA,</label>
    <label><input type="checkbox" id="h2_op5" onchange="handleLink(this)">ENFERMEDAD PULMONAR OBSTRUCTIVA CRONICA MMRC: <input type="text" id="h2_op5_txt">,</label>
    <label><input type="checkbox" id="h2_op6" onchange="handleLink(this)">FALLA CARDIACA NYHA: <input type="text" id="h2_op6_txt">,</label>
    <label><input type="checkbox" id="h2_op7" onchange="handleLink(this)">HIPOTIROIDISMO,</label>
    <label><input type="checkbox" id="h2_op8" onchange="handleLink(this)">FIBRILACIÓN AURICULAR,</label>
    <label><input type="checkbox" id="h2_op9" onchange="handleLink(this)">TABAQUISMO PESADO CON IPA: ACTIVO/ABANDONO HACE <input type="text" id="h2_op9_txt"></label>
    <label><input type="checkbox" id="h2_op10" onchange="handleLink(this)">EXPOSICIÓN A BIOMASA</label>
    <label><input type="checkbox" id="h2_op11" onchange="handleLink(this)">ALERGIA A <input type="text" id="h2_op11_txt">,</label>
    <label><input type="checkbox" id="h2_op12" onchange="handleLink(this)">HOSPITALIZACIÓN EN LOS ULTIMOS 3 MESES POR <input type="text" id="h2_op12_txt"></label>
    <label><input type="checkbox" id="h2_op13" data-link="h4_op2" onchange="handleLink(this)">VIH</label>
    <label><input type="checkbox" id="h2_op14" onchange="handleLink(this)">CANCER DE </label>
  </div>

  <h3> ,</h3>
  <div class="grupo">
    <label><input type="checkbox" id="h3_op1" onchange="handleLink(this)">ACUDE SIN ACOMPAÑANTE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE</label>
    <label><input type="checkbox" id="h3_op2" onchange="handleLink(this)">ACUDE AL SERVICIO DE URGENCIAS CON ACOMPAÑANTE (<input type="text" id="h3_op2_txt">)</label>
  </div>

  <h4> ,</h4>
  <div class="grupo">
    <label><input type="checkbox" id="h4_op1" onchange="handleLink(this)">REFIRIENDO CUADRO CLINICO DE <input type="text" id="h4_op1_txt"> HORAS DE EVOLUCIÓN CONSISTENTE EN</label>
    <label><input type="checkbox" id="h4_op2" onchange="handleLink(this)">REFIRIENDO CUADRO CLINICO DE <input type="text" id="h4_op2_txt"> DÍAS DE EVOLUCIÓN CONSISTENTE EN</label>
    <label><input type="checkbox" id="h4_op3" onchange="handleLink(this)">REFIRIENDO CUADRO CLINICO DE <input type="text" id="h4_op3_txt"> MESES DE EVOLUCIÓN CONSISTENTE</label>
  </div>

  <button onclick="updateNarrativa()">Generar Narrativa</button>
  <p id="resultado"></p>

  <script>
    function handleLink(source) {
      const targetId = source.dataset.link;
      if (!targetId) return;
      const target = document.getElementById(targetId);
      if (target) target.checked = source.checked;
    }

    function updateNarrativa() {
      const checks = document.querySelectorAll("input[type=checkbox]");
      let narrativa = "";

      narrativa += " . ";

      if (checks[0].checked) {
        narrativa += "PACIENTE MASCULINO DE ";
        const v = h1_op1_txt.value.trim();
        if (v) narrativa += v + " ";
        narrativa += "ESCRIBIR AÑOS ";
      }

      if (checks[1].checked) {
        narrativa += "PACIENTE FEMENINA DE ";
        const v = h1_op2_txt.value.trim();
        if (v) narrativa += v + " ";
        narrativa += "ESCRIBIR AÑOS ";
      }

      narrativa += "CON ANTECEDENTE DE ";

      if (checks[2].checked) narrativa += "HIPERTENSIÓN ARTERIAL, ";
      if (checks[3].checked) narrativa += "DIABETES MELLITUS TIPO 2 NO INSULINO REQUIRIENTE, ADHERENTE, SIN COMPLICACIONES MACROVASCULARES ";
      if (checks[4].checked) narrativa += "DISLIPIDEMIA ";
      if (checks[5].checked) narrativa += "ENFERMEDAD RENAL CRONICA, ";

      if (checks[6].checked) {
        narrativa += "ENFERMEDAD PULMONAR OBSTRUCTIVA CRONICA MMRC: ";
        const v = h2_op5_txt.value.trim();
        if (v) narrativa += v + " ";
        narrativa += ", ";
      }

      if (checks[7].checked) {
        narrativa += "FALLA CARDIACA NYHA: ";
        const v = h2_op6_txt.value.trim();
        if (v) narrativa += v + " ";
        narrativa += ", ";
      }

      if (checks[8].checked) narrativa += "HIPOTIROIDISMO, ";
      if (checks[9].checked) narrativa += "FIBRILACIÓN AURICULAR, ";

      if (checks[10].checked) {
        narrativa += "TABAQUISMO PESADO CON IPA: ACTIVO/ABANDONO HACE ";
        const v = h2_op9_txt.value.trim();
        if (v) narrativa += v + " ";
      }

      if (checks[11].checked) narrativa += "EXPOSICIÓN A BIOMASA ";

      if (checks[12].checked) {
        narrativa += "ALERGIA A ";
        const v = h2_op11_txt.value.trim();
        if (v) narrativa += v + " ";
        narrativa += ", ";
      }

      if (checks[13].checked) {
        narrativa += "HOSPITALIZACIÓN EN LOS ULTIMOS 3 MESES POR ";
        const v = h2_op12_txt.value.trim();
        if (v) narrativa += v + " ";
      }

      if (checks[14].checked) narrativa += "VIH ";
      if (checks[15].checked) narrativa += "CANCER DE  ";

      narrativa += " , ";

      if (checks[16].checked) narrativa += "ACUDE SIN ACOMPAÑANTE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE ";

      if (checks[17].checked) {
        narrativa += "ACUDE AL SERVICIO DE URGENCIAS CON ACOMPAÑANTE (";
        const v = h3_op2_txt.value.trim();
        if (v) narrativa += v + " ";
        narrativa += ") ";
      }

      narrativa += " , ";

      if (checks[18].checked) {
        narrativa += "REFIRIENDO CUADRO CLINICO DE ";
        const v = h4_op1_txt.value.trim();
        if (v) narrativa += v + " ";
        narrativa += "HORAS DE EVOLUCIÓN CONSISTENTE EN ";
      }

      if (checks[19].checked) {
        narrativa += "REFIRIENDO CUADRO CLINICO DE ";
        const v = h4_op2_txt.value.trim();
        if (v) narrativa += v + " ";
        narrativa += "DÍAS DE EVOLUCIÓN CONSISTENTE EN ";
      }

      if (checks[20].checked) {
        narrativa += "REFIRIENDO CUADRO CLINICO DE ";
        const v = h4_op3_txt.value.trim();
        if (v) narrativa += v + " ";
        narrativa += "MESES DE EVOLUCIÓN CONSISTENTE ";
      }

      document.getElementById("resultado").textContent = narrativa.trim();
    }
  </script>

</body>
</html>