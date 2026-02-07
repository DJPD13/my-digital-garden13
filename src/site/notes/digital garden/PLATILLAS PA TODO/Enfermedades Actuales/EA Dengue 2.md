---
{"dg-publish":true,"permalink":"/digital-garden/platillas-pa-todo/enfermedades-actuales/ea-dengue-2/","dgPassFrontmatter":true}
---

<h3>1 parte</h3>
<label><input type="checkbox" onclick="updateNarrativa()"> ACUDE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE, REFIERE </label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> ACUDE AL SERVICIO DE URGENCIAS ACOMPAÑADO DE XXXX, REFIERE </label><br>
<label><input type="checkbox" onclick="updateNarrativa()">ES TRAIDO AL SERVICIO DE URGENCIAS POR MADRE QUIEN REFIERE QUE HA PRESENTADO CUADRO </label><br>

<h2>Necesario</h2>
<label><input type="checkbox" onclick="updateNarrativa()"> FIEBRE SUBJETIVA</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> FIEBRE CUANTIFICADA EN</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> PICOS FEBRILES</label><br>
<h3>Al menos 2 de estos</h3>
<label><input type="checkbox" onclick="updateNarrativa()"> CEFALEA</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> NÁUSEAS</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> VÓMITO</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> MIALGIAS</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> ARTRALGIAS</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> EXANTEMA (registrar también en examen físico)</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> PETEQUIAS EN (registrar también en examen físico)</label><br>

<h4>Signos de alarma</h4>
<label><input type="checkbox" onclick="updateNarrativa()"> DOLOR ABDOMINAL INTENSO Y CONTINUO</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> VÓMITOS PERSISTENTES</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> DIARREA</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> LETARGO</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> IRRITABILIDAD (PRINCIPALMENTE EN NIÑOS)</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> HIPOTENSIÓN POSTURAL</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> LIPOTIMIA</label><br>

<h3>Narrativa generada</h3>
<p id="narrativa"></p>

<script>
function updateNarrativa() {
  let narrativa = "";

  // Sección síntomas
  narrativa += "PACIENTE DE ## AÑOS";
  const checks = document.querySelectorAll("input[type=checkbox]");
  if (checks[0].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE, REFIERE CUADRO CLINICO DE X DIAS DE EVOLUCION CONSISTENTE EN ";
  if (checks[1].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS ACOMPAÑADO DE XXXX, REFIERE CUADRO CLINICO DE X DIAS DE EVOLUCION CONSISTENTE EN ";
  if (checks[2].checked) narrativa += "ES TRAIDO AL SERVICIO DE URGENCIAS POR MADRE QUIEN REFIERE QUE HA PRESENTADO CUADRO CLINICO DE X DIAS DE EVOLUCION CONSISTENTE EN ";

  // Síntomas iniciales
  narrativa += "CUADRO CLINICO DE X DIAS DE EVOLUCION CONSISTENTE EN ";
  if (checks[3].checked) narrativa += "FIEBRE SUBJETIVA ";
  if (checks[4].checked) narrativa += "FIEBRE CUANTIFICADA EN GRADOS ";
  if (checks[5].checked) narrativa += "PICOS FEBRILES NO CUANTIFICADOS ";
  
  narrativa += "ACOMPAÑADO DE ";
  if (checks[6].checked) narrativa += "CEFALEA ";
  if (checks[7].checked) narrativa += "NAUSEAS ";
  if (checks[8].checked) narrativa += "VOMITO ";
  if (checks[9].checked) narrativa += "MIALGIAS ";
  if (checks[10].checked) narrativa += "ARTRALGIAS ";
  if (checks[11].checked) narrativa += "EXANTEMA (REGISTRAR TAMBIEN EN EXAMEN FISICO) ";
  if (checks[12].checked) narrativa += "PETEQUIAS EN (REGISTRAR TAMBIEN EN EXAMEN FISICO) ";

  // Síntomas de alarma
  if (checks[13].checked) narrativa += "DOLOR ABDOMINAL INTENSO Y CONTINUO ";
  if (checks[14].checked) narrativa += "VOMITOS PERSISTENTES ";
  if (checks[15].checked) narrativa += "DIARREA ";
  if (checks[16].checked) narrativa += "LETARGO ";
  if (checks[17].checked) narrativa += "IRRITABILIDAD (PRINCIPALMENTE EN NIÑOS) ";
  if (checks[18].checked) narrativa += "HIPOTENSION POSTURAL ";
  if (checks[19].checked) narrativa += "LIPOTIMIA ";

  document.getElementById("narrativa").innerText = narrativa;
}
</script>


