---
{"dg-publish":true,"permalink":"/digital-garden/platillas-pa-todo/enfermedades-actuales/ea-dengue-2/","dgPassFrontmatter":true}
---

<h3>1 parte</h3>
<label><input type="checkbox" onclick="updateNarrativa()"> ACUDE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE, REFIERE CUADRO CLINICO DE X DÍAS DE EVOLUCIÓN CONSISTENTE EN</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> ACUDE AL SERVICIO DE URGENCIAS ACOMPAÑADO DE XXXX, REFIERE CUADRO CLINICO DE X DÍAS DE EVOLUCIÓN CONSISTENTE EN</label><br>
<label><input type="checkbox" onclick="updateNarrativa()">ES TRAIDO AL SERVICIO DE URGENCIAS POR MADRE QUIEN REFIERE QUE HA PRESENTADO CUADRO CLINICO DE X DÍAS DE EVOLUCIÓN CONSISTENTE EN</label><br>

<h3>2 parte</h3>
<label><input type="checkbox" onclick="updateNarrativa()"> FIEBRE SUBJETIVA</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> FIEBRE CUANTIFICADA EN XXXX</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> PICOS FEBRILES</label><br>

<h3>3 parte</h3>
<label><input type="checkbox" onclick="updateNarrativa()"> Contacto con casos confirmados</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> Zona endémica</label><br>

<h3>Narrativa generada</h3>
<p id="narrativa"></p>

<script>
function updateNarrativa() {
  let narrativa = "";

  // Sección síntomas
  narrativa += "PACIENTE DE ## AÑOS ACUDE AL SERVICIO DE URGENCIAS";
  const checks = document.querySelectorAll("input[type=checkbox]");
  if (checks[0].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE, REFIERE CUADRO CLINICO DE X DÍAS DE EVOLUCIÓN CONSISTENTE EN ";
  if (checks[1].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS ACOMPAÑADO DE XXXX, REFIERE CUADRO CLINICO DE X DÍAS DE EVOLUCIÓN CONSISTENTE EN";
  if (checks[2].checked) narrativa += "ES TRAIDO AL SERVICIO DE URGENCIAS POR MADRE QUIEN REFIERE QUE HA PRESENTADO CUADRO CLINICO DE X DÍAS DE EVOLUCIÓN CONSISTENTE EN ";

  // Sección laboratorio
  narrativa += "\nResultados de laboratorio: ";
  if (checks[3].checked) narrativa += "FIEBRE SUBJETIVA";
  if (checks[4].checked) narrativa += "FIEBRE CUATIFICADA EN";
  if (checks[5].checked) narrativa += "PICOS FEBRILES ";

  // Sección epidemiología
  narrativa += "\nAntecedentes epidemiológicos: ";
  if (checks[6].checked) narrativa += "Contacto con casos confirmados. ";
  if (checks[7].checked) narrativa += "Reside en zona endémica. ";

  document.getElementById("narrativa").innerText = narrativa;
}
</script>


