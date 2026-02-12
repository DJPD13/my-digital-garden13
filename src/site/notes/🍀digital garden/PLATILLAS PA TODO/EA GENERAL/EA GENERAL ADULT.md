---
{"dg-publish":true,"permalink":"/digital-garden/platillas-pa-todo/ea-general/ea-general-adult/","dgPassFrontmatter":true}
---

<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Narrativa con Checkboxes</title>
  <style>
    body { font-family: Arial, sans-serif; line-height: 1.35; padding: 16px; }
    h1,h2,h3,h4,h5,h6 { margin: 16px 0 8px; }
    .item { display: block; margin: 6px 0; }
    .out { margin-top: 18px; }
    textarea { width: 100%; min-height: 140px; }
    button { margin-top: 10px; padding: 8px 12px; cursor: pointer; }
  </style>
</head>
<body>

  <h1>.</h1>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> PACIENTE MASCULINO DE # AÑOS </label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> PACIENTE MASCULINO DE # AÑOS </label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> PACIENTE FEMENINA DE # AÑOS </label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> PACIENTE FEMENINA DE # AÑOS</label>

  <h2>CON ANTECEDENTES DE</h2>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> HIPERTENSIÓN ARTERIAL,</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> DIABETES MELLITUS TIPO 2 NO INSULINO REQUIRIENTE,</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> ENFERMEDAD RENAL CRONICA,</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> ENFERMEDAD PULMONAR OBSTRUCTIVA CRONICA MMRC: ##,</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> FALLA CARDIACA NYHA,</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> HIPOTIROIDISMO,</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> FIBRILACIÓN AURICULAR,</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> TABAQUISMO PESADO CON IPA DE</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> EXPOSICIÓN A BIOMASA</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> ALERGIA A ##,</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> HOSPITALIZACIÓN EN LOS ULTIMOS 3 MESES POR ##</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> VIH </label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> CANCER DE </label>

  <h3>,</h3>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> ACUDE AL SERVICIO DE URGENCIAS REFIRIENDO CUADRO CLINICO DE # DÍAS DE EVOLUCIÓN </label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> ACUDE AL SERVICIO DE URGENCIAS REFIRIENDO CUADRO CLINICO DE # HORAS DE EVOLUCIÓN</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> ACUDE AL SERVICIO DE URGENCIAS REFIRIENDO CUADRO CLINICO DE # DÍAS DE EVOLUCIÓN</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> ACUDE AL SERVICIO DE URGENCIAS REFIRIENDO CUADRO CLINICO DE # HORAS DE EVOLUCIÓN</label>

  <h4>CONSISTENTE EN</h4>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> DOLOR TORACICO OPRESIVO DE INICIO ##  Y INTENSIDAD ## EL CUAL SE REFIERE A ##, SE EXACERBA CON ##, Y MEJORA CON ##</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> DOLOR TORACICO PUNZANTE DE INICIO ##  Y INTENSIDAD ## EL CUAL SE REFIERE A ##, SE EXACERBA CON ##, Y MEJORA CON ##</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> DISNEA DE ## ESFUERZOS</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> DOLOR ABDOMINAL DIFUSO TIPO COLICO DE INICIO ##  Y INTENSIDAD ## , SE EXACERBA CON ##, Y MEJORA CON ##</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> DOLOR ABDOMINAL  TIPO COLICO LOCALIZADO EN ## DE INICIO ##  Y INTENSIDAD ## EL CUAL SE REFIERE A ## </label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> CONVULSIONES TONICO GLONICAS GENERALIZADAS PRESENCIADAS DE APROXIMADAMENTE ## DE DURACIÓN CON RECUPERACIÓN ESPONTANEA</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> PICOS FEBRILES NO CUANTIFICADOS</label>

  <h4>SE ASOCIA A</h4>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> DIAFORESIS</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> TOS SECA</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> TOS PORDUCTIVA</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> EPISODIOS EMETICOS</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> EDEMA DE MIEMBROS INFERIORES</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> MIALGIAS</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> ARTRALGIAS</label>

  <h4>NIEGA</h4>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> PERDIDA DE PESO</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> FIEBRE SUBJETIVA</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> SUDORACIÓN NOCTURNA</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> ADINAMIA</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> CEFALEA</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> DOLOR ABDOMINAL LOCALIZADO EN HIPOGASTRIO</label>
  <label class="item"><input type="checkbox" onchange="updateNarrativa()"> DISTENSION ABDOMINAL</label>

  <div class="out">
    <button type="button" onclick="updateNarrativa()">Actualizar narrativa</button>
    <textarea id="narrativa" readonly></textarea>
  </div>

  <script>
    function updateNarrativa() {
      const checks = document.querySelectorAll("input[type=checkbox]");
      let narrativa = "";

      narrativa += ". ";
      if (checks[0].checked) narrativa += "PACIENTE MASCULINO DE # AÑOS  ";
      if (checks[1].checked) narrativa += "PACIENTE MASCULINO DE # AÑOS  ";
      if (checks[2].checked) narrativa += "PACIENTE FEMENINA DE # AÑOS  ";
      if (checks[3].checked) narrativa += "PACIENTE FEMENINA DE # AÑOS ";

      narrativa += "CON ANTECEDENTES DE ";
      if (checks[4].checked) narrativa += "HIPERTENSIÓN ARTERIAL, ";
      if (checks[5].checked) narrativa += "DIABETES MELLITUS TIPO 2 NO INSULINO REQUIRIENTE, ";
      if (checks[6].checked) narrativa += "ENFERMEDAD RENAL CRONICA, ";
      if (checks[7].checked) narrativa += "ENFERMEDAD PULMONAR OBSTRUCTIVA CRONICA MMRC: ##, ";
      if (checks[8].checked) narrativa += "FALLA CARDIACA NYHA, ";
      if (checks[9].checked) narrativa += "HIPOTIROIDISMO, ";
      if (checks[10].checked) narrativa += "FIBRILACIÓN AURICULAR, ";
      if (checks[11].checked) narrativa += "TABAQUISMO PESADO CON IPA DE ";
      if (checks[12].checked) narrativa += "EXPOSICIÓN A BIOMASA ";
      if (checks[13].checked) narrativa += "ALERGIA A ##, ";
      if (checks[14].checked) narrativa += "HOSPITALIZACIÓN EN LOS ULTIMOS 3 MESES POR ## ";
      if (checks[15].checked) narrativa += "VIH  ";
      if (checks[16].checked) narrativa += "CANCER DE  ";

      narrativa += ", ";
      if (checks[17].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS REFIRIENDO CUADRO CLINICO DE # DÍAS DE EVOLUCIÓN  ";
      if (checks[18].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS REFIRIENDO CUADRO CLINICO DE # HORAS DE EVOLUCIÓN ";
      if (checks[19].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS REFIRIENDO CUADRO CLINICO DE # DÍAS DE EVOLUCIÓN ";
      if (checks[20].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS REFIRIENDO CUADRO CLINICO DE # HORAS DE EVOLUCIÓN ";

      narrativa += "CONSISTENTE EN ";
      if (checks[21].checked) narrativa += "DOLOR TORACICO OPRESIVO DE INICIO ##  Y INTENSIDAD ## EL CUAL SE REFIERE A ##, SE EXACERBA CON ##, Y MEJORA CON ## ";
      if (checks[22].checked) narrativa += "DOLOR TORACICO PUNZANTE DE INICIO ##  Y INTENSIDAD ## EL CUAL SE REFIERE A ##, SE EXACERBA CON ##, Y MEJORA CON ## ";
      if (checks[23].checked) narrativa += "DISNEA DE ## ESFUERZOS ";
      if (checks[24].checked) narrativa += "DOLOR ABDOMINAL DIFUSO TIPO COLICO DE INICIO ##  Y INTENSIDAD ## , SE EXACERBA CON ##, Y MEJORA CON ## ";
      if (checks[25].checked) narrativa += "DOLOR ABDOMINAL  TIPO COLICO LOCALIZADO EN ## DE INICIO ##  Y INTENSIDAD ## EL CUAL SE REFIERE A ##  ";
      if (checks[26].checked) narrativa += "CONVULSIONES TONICO GLONICAS GENERALIZADAS PRESENCIADAS DE APROXIMADAMENTE ## DE DURACIÓN CON RECUPERACIÓN ESPONTANEA ";
      if (checks[27].checked) narrativa += "PICOS FEBRILES NO CUANTIFICADOS ";

      narrativa += "SE ASOCIA A ";
      if (checks[28].checked) narrativa += "DIAFORESIS ";
      if (checks[29].checked) narrativa += "TOS SECA ";
      if (checks[30].checked) narrativa += "TOS PORDUCTIVA ";
      if (checks[31].checked) narrativa += "EPISODIOS EMETICOS ";
      if (checks[32].checked) narrativa += "EDEMA DE MIEMBROS INFERIORES ";
      if (checks[33].checked) narrativa += "MIALGIAS ";
      if (checks[34].checked) narrativa += "ARTRALGIAS ";

      narrativa += "NIEGA ";
      if (checks[35].checked) narrativa += "PERDIDA DE PESO ";
      if (checks[36].checked) narrativa += "FIEBRE SUBJETIVA ";
      if (checks[37].checked) narrativa += "SUDORACIÓN NOCTURNA ";
      if (checks[38].checked) narrativa += "ADINAMIA ";
      if (checks[39].checked) narrativa += "CEFALEA ";
      if (checks[40].checked) narrativa += "DOLOR ABDOMINAL LOCALIZADO EN HIPOGASTRIO ";
      if (checks[41].checked) narrativa += "DISTENSION ABDOMINAL ";

      document.getElementById("narrativa").value = narrativa;
    }

    updateNarrativa();
  </script>

</body>
</html>
