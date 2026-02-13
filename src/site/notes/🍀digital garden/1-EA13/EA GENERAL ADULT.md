---
{"dg-publish":true,"permalink":"/digital-garden/1-ea-13/ea-general-adult/","dgPassFrontmatter":true}
---

<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Narrativa con checkboxes</title>
  <style>
    body { font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif; line-height: 1.35; padding: 16px; }
    label { display: block; margin: 6px 0; }
    .out { margin-top: 16px; padding: 12px; border: 1px solid #ccc; border-radius: 8px; white-space: pre-wrap; }
    .btns { margin: 12px 0; display: flex; gap: 8px; flex-wrap: wrap; }
    button { padding: 8px 10px; cursor: pointer; }
  </style>
</head>
<body>

  <h1> .</h1>
  <label><input type="checkbox" onchange="updateNarrativa()"> PACIENTE MASCULINO DE # AÑOS </label>
  <label><input type="checkbox" onchange="updateNarrativa()"> PACIENTE FEMENINA DE # AÑOS </label>

  <h2>CON ANTECEDENTE DE</h2>
  <label><input type="checkbox" onchange="updateNarrativa()"> HIPERTENSIÓN ARTERIAL,</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> DIABETES MELLITUS TIPO 2 NO INSULINO REQUIRIENTE, ADHERENTE, SIN COMPLICACIONES MACROVASCULARES</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> DISLIPIDEMIA</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> ENFERMEDAD RENAL CRONICA,</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> ENFERMEDAD PULMONAR OBSTRUCTIVA CRONICA MMRC: ##,</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> FALLA CARDIACA NYHA: ,</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> HIPOTIROIDISMO,</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> FIBRILACIÓN AURICULAR,</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> TABAQUISMO PESADO CON IPA: ACTIVO/ABANDONO HACE # </label>
  <label><input type="checkbox" onchange="updateNarrativa()"> EXPOSICIÓN A BIOMASA</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> ALERGIA A ##,</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> HOSPITALIZACIÓN EN LOS ULTIMOS 3 MESES POR ##</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> VIH </label>
  <label><input type="checkbox" onchange="updateNarrativa()"> CANCER DE </label>

  <h3> ,</h3>
  <label><input type="checkbox" onchange="updateNarrativa()"> ACUDE SIN ACOMPAÑANTE AL SERVICIO DE URGENCIAS REFIRIENDO CUADRO CLINICO DE # DÍAS DE EVOLUCIÓN </label>
  <label><input type="checkbox" onchange="updateNarrativa()"> ACUDE AL SERVICIO DE URGENCIAS CONACOMPAÑANTE () REFIRIENDO CUADRO CLINICO DE # HORAS DE EVOLUCIÓN</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> ACUDE AL SERVICIO DE URGENCIAS REFIRIENDO CUADRO CLINICO DE # DÍAS DE EVOLUCIÓN</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> ACUDE AL SERVICIO DE URGENCIAS REFIRIENDO CUADRO CLINICO DE # HORAS DE EVOLUCIÓN</label>

  <h4></h4>
  <label><input type="checkbox" onchange="updateNarrativa()"> REFIRIENDO CUADRO CLINICO DE # DÍAS DE EVOLUCIÓN </label>
  <label><input type="checkbox" onchange="updateNarrativa()"> REFIRIENDO CUADRO CLINICO DE # HORAS DE EVOLUCIÓN</label>

  <h4>CONSISTENTE EN (CARDIOVASCULAR)</h4>
  <label><input type="checkbox" onchange="updateNarrativa()"> DOLOR TORACICO OPRESIVO DE INICIO ##  Y INTENSIDAD ## EL CUAL SE REFIERE A ##, SE EXACERBA CON ##, Y MEJORA CON ##</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> DOLOR TORACICO PUNZANTE DE INICIO ##  Y INTENSIDAD ## EL CUAL SE REFIERE A ##, SE EXACERBA CON ##, Y MEJORA CON ##</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> DISNEA DE ## ESFUERZOS</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> SINCOPE</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> PALPITACIONES</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> DOLOR ABDOMINAL DIFUSO TIPO COLICO DE INICIO ##  Y INTENSIDAD ## , SE EXACERBA CON ##, Y MEJORA CON ##</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> DOLOR ABDOMINAL  TIPO COLICO LOCALIZADO EN ## DE INICIO ##  Y INTENSIDAD ## EL CUAL SE REFIERE A ## </label>
  <label><input type="checkbox" onchange="updateNarrativa()"> CONVULSIONES TONICO GLONICAS GENERALIZADAS PRESENCIADAS DE APROXIMADAMENTE ## DE DURACIÓN CON RECUPERACIÓN ESPONTANEA</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> PICOS FEBRILES NO CUANTIFICADOS</label>

  <h4>,SE ASOCIA A</h4>
  <label><input type="checkbox" onchange="updateNarrativa()"> DISNEA</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> DIFICULTAD RESPIRATORIA</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> DIAFORESIS</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> TOS SECA</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> TOS PRODUTIVA</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> EPISODIOS EMETICOS</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> EDEMA DE MIEMBROS INFERIORES</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> MIALGIAS</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> ARTRALGIAS</label>

  <h5>NIEGA</h5>
  <label><input type="checkbox" onchange="updateNarrativa()"> PERDIDA DE PESO</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> FIEBRE SUBJETIVA</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> SUDORACIÓN NOCTURNA</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> ADINAMIA</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> ASTENIA</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> CEFALEA</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> DISNEA</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> DIFICULTAD RESPIRATORIA</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> DIAFORESIS</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> TOS SIN EXPECTORACIÓN</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> TOS CON EXPECTORACIÓN DE DE ESPUTO</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> EPISODIOS EMETICOS</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> EDEMA DE MIEMBROS INFERIORES</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> PICOS FEBRILES NO CUANTIFICADOS</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> MIALGIAS</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> ARTRALGIAS</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> DOLOR ABDOMINAL</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> DISTENSION ABDOMINAL</label>

  <h6>SE CONSIDERA</h6>
  <label><input type="checkbox" onchange="updateNarrativa()"> PACIENTE SIN CRITERIOS DE MANEJO POR EL SERVICO DE URGENCIAS POR LO QUE SE DAN RECOMENDACIONES PARA CUIDADOS EN CASA Y SIGNOS DE ALARMA PARA CONSULTAR A URGENCIAS</label>
  <label><input type="checkbox" onchange="updateNarrativa()"> PACIENTE QUE REQUIERE MANEJO INTRAHOSPITALARIO EN EL SERVICIO DE URGENCIA DEBIDO A # POR LO CUAL SE INGRESA</label>

  <div class="btns">
    <button type="button" onclick="document.querySelectorAll('input[type=checkbox]').forEach(cb=>cb.checked=true); updateNarrativa();">Marcar todo</button>
    <button type="button" onclick="document.querySelectorAll('input[type=checkbox]').forEach(cb=>cb.checked=false); updateNarrativa();">Desmarcar todo</button>
  </div>

  <div class="out" id="out"></div>

  <script>
    function updateNarrativa() {
      const checks = document.querySelectorAll("input[type=checkbox]");
      let narrativa = "";

      narrativa += " . ";
      if (checks[0].checked) narrativa += "PACIENTE MASCULINO DE # AÑOS  ";
      if (checks[1].checked) narrativa += "PACIENTE FEMENINA DE # AÑOS  ";

      narrativa += "CON ANTECEDENTE DE ";
      if (checks[2].checked) narrativa += "HIPERTENSIÓN ARTERIAL, ";
      if (checks[3].checked) narrativa += "DIABETES MELLITUS TIPO 2 NO INSULINO REQUIRIENTE, ADHERENTE, SIN COMPLICACIONES MACROVASCULARES ";
      if (checks[4].checked) narrativa += "DISLIPIDEMIA ";
      if (checks[5].checked) narrativa += "ENFERMEDAD RENAL CRONICA, ";
      if (checks[6].checked) narrativa += "ENFERMEDAD PULMONAR OBSTRUCTIVA CRONICA MMRC: ##, ";
      if (checks[7].checked) narrativa += "FALLA CARDIACA NYHA: , ";
      if (checks[8].checked) narrativa += "HIPOTIROIDISMO, ";
      if (checks[9].checked) narrativa += "FIBRILACIÓN AURICULAR, ";
      if (checks[10].checked) narrativa += "TABAQUISMO PESADO CON IPA: ACTIVO/ABANDONO HACE #  ";
      if (checks[11].checked) narrativa += "EXPOSICIÓN A BIOMASA ";
      if (checks[12].checked) narrativa += "ALERGIA A ##, ";
      if (checks[13].checked) narrativa += "HOSPITALIZACIÓN EN LOS ULTIMOS 3 MESES POR ## ";
      if (checks[14].checked) narrativa += "VIH  ";
      if (checks[15].checked) narrativa += "CANCER DE  ";

      narrativa += " , ";
      if (checks[16].checked) narrativa += "ACUDE SIN ACOMPAÑANTE AL SERVICIO DE URGENCIAS REFIRIENDO CUADRO CLINICO DE # DÍAS DE EVOLUCIÓN  ";
      if (checks[17].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS CONACOMPAÑANTE () REFIRIENDO CUADRO CLINICO DE # HORAS DE EVOLUCIÓN ";
      if (checks[18].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS REFIRIENDO CUADRO CLINICO DE # DÍAS DE EVOLUCIÓN ";
      if (checks[19].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS REFIRIENDO CUADRO CLINICO DE # HORAS DE EVOLUCIÓN ";

      narrativa += " ";
      if (checks[20].checked) narrativa += "REFIRIENDO CUADRO CLINICO DE # DÍAS DE EVOLUCIÓN  ";
      if (checks[21].checked) narrativa += "REFIRIENDO CUADRO CLINICO DE # HORAS DE EVOLUCIÓN ";

      narrativa += "CONSISTENTE EN (CARDIOVASCULAR) ";
      if (checks[22].checked) narrativa += "DOLOR TORACICO OPRESIVO DE INICIO ##  Y INTENSIDAD ## EL CUAL SE REFIERE A ##, SE EXACERBA CON ##, Y MEJORA CON ## ";
      if (checks[23].checked) narrativa += "DOLOR TORACICO PUNZANTE DE INICIO ##  Y INTENSIDAD ## EL CUAL SE REFIERE A ##, SE EXACERBA CON ##, Y MEJORA CON ## ";
      if (checks[24].checked) narrativa += "DISNEA DE ## ESFUERZOS ";
      if (checks[25].checked) narrativa += "SINCOPE ";
      if (checks[26].checked) narrativa += "PALPITACIONES ";
      if (checks[27].checked) narrativa += "DOLOR ABDOMINAL DIFUSO TIPO COLICO DE INICIO ##  Y INTENSIDAD ## , SE EXACERBA CON ##, Y MEJORA CON ## ";
      if (checks[28].checked) narrativa += "DOLOR ABDOMINAL  TIPO COLICO LOCALIZADO EN ## DE INICIO ##  Y INTENSIDAD ## EL CUAL SE REFIERE A ##  ";
      if (checks[29].checked) narrativa += "CONVULSIONES TONICO GLONICAS GENERALIZADAS PRESENCIADAS DE APROXIMADAMENTE ## DE DURACIÓN CON RECUPERACIÓN ESPONTANEA ";
      if (checks[30].checked) narrativa += "PICOS FEBRILES NO CUANTIFICADOS ";

      narrativa += ",SE ASOCIA A ";
      if (checks[31].checked) narrativa += "DISNEA ";
      if (checks[32].checked) narrativa += "DIFICULTAD RESPIRATORIA ";
      if (checks[33].checked) narrativa += "DIAFORESIS ";
      if (checks[34].checked) narrativa += "TOS SECA ";
      if (checks[35].checked) narrativa += "TOS PRODUTIVA ";
      if (checks[36].checked) narrativa += "EPISODIOS EMETICOS ";
      if (checks[37].checked) narrativa += "EDEMA DE MIEMBROS INFERIORES ";
      if (checks[38].checked) narrativa += "MIALGIAS ";
      if (checks[39].checked) narrativa += "ARTRALGIAS ";

      narrativa += "NIEGA ";
      if (checks[40].checked) narrativa += "PERDIDA DE PESO ";
      if (checks[41].checked) narrativa += "FIEBRE SUBJETIVA ";
      if (checks[42].checked) narrativa += "SUDORACIÓN NOCTURNA ";
      if (checks[43].checked) narrativa += "ADINAMIA ";
      if (checks[44].checked) narrativa += "ASTENIA ";
      if (checks[45].checked) narrativa += "CEFALEA ";
      if (checks[46].checked) narrativa += "DISNEA ";
      if (checks[47].checked) narrativa += "DIFICULTAD RESPIRATORIA ";
      if (checks[48].checked) narrativa += "DIAFORESIS ";
      if (checks[49].checked) narrativa += "TOS SIN EXPECTORACIÓN ";
      if (checks[50].checked) narrativa += "TOS CON EXPECTORACIÓN DE DE ESPUTO ";
      if (checks[51].checked) narrativa += "EPISODIOS EMETICOS ";
      if (checks[52].checked) narrativa += "EDEMA DE MIEMBROS INFERIORES ";
      if (checks[53].checked) narrativa += "PICOS FEBRILES NO CUANTIFICADOS ";
      if (checks[54].checked) narrativa += "MIALGIAS ";
      if (checks[55].checked) narrativa += "ARTRALGIAS ";
      if (checks[56].checked) narrativa += "DOLOR ABDOMINAL ";
      if (checks[57].checked) narrativa += "DISTENSION ABDOMINAL ";

      narrativa += "SE CONSIDERA ";
      if (checks[58].checked) narrativa += "PACIENTE SIN CRITERIOS DE MANEJO POR EL SERVICO DE URGENCIAS POR LO QUE SE DAN RECOMENDACIONES PARA CUIDADOS EN CASA Y SIGNOS DE ALARMA PARA CONSULTAR A URGENCIAS ";
      if (checks[59].checked) narrativa += "PACIENTE QUE REQUIERE MANEJO INTRAHOSPITALARIO EN EL SERVICIO DE URGENCIA DEBIDO A # POR LO CUAL SE INGRESA ";

      document.getElementById("out").textContent = narrativa;
    }

    updateNarrativa();
  </script>

</body>
</html>