---
{"dg-publish":true,"permalink":"/digital-garden/platillas-pa-todo/enfermedades-actuales/ea-dengue-2/","dgPassFrontmatter":true}
---

<h3>1 parte</h3>
<label><input type="checkbox" onclick="updateNarrativa()"> ACUDE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE, REFIERE </label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> ACUDE AL SERVICIO DE URGENCIAS ACOMPAÑADO DE XXXX, REFIERE </label><br>
<label><input type="checkbox" onclick="updateNarrativa()">ES TRAIDO AL SERVICIO DE URGENCIAS POR MADRE QUIEN REFIERE QUE HA PRESENTADO CUADRO </label><br>

<h3>Al menos 2 de estos</h3>
<label><input type="checkbox" onclick="updateNarrativa()"> FIEBRE SUBJETIVA</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> FIEBRE CUANTIFICADA EN</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> PICOS FEBRILES</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> CEFALEA</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> NÁUSEAS</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> VÓMITO</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> MIALGIAS</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> ARTRALGIAS</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> EXANTEMA (registrar también en examen físico)</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> PETEQUIAS EN (registrar también en examen físico)</label><br>

<h3>Signos de alarma</h3>
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
  narrativa += "PACIENTE DE ## AÑOS ACUDE AL SERVICIO DE URGENCIAS";
  const checks = document.querySelectorAll("input[type=checkbox]");
  if (checks[0].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE, REFIERE CUADRO CLINICO DE X DÍAS DE EVOLUCIÓN CONSISTENTE EN ";
  if (checks[1].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS ACOMPAÑADO DE XXXX, REFIERE CUADRO CLINICO DE X DÍAS DE EVOLUCIÓN CONSISTENTE EN";
  if (checks[2].checked) narrativa += "ES TRAIDO AL SERVICIO DE URGENCIAS POR MADRE QUIEN REFIERE QUE HA PRESENTADO CUADRO CLINICO DE X DÍAS DE EVOLUCIÓN CONSISTENTE EN ";

  narrativa += "CUADRO CLINICO DE X DÍAS DE EVOLUCIÓN CONSISTENTE EN ";
  if (checks[3].checked) narrativa += "Cefalea. ";
  if (checks[4].checked) narrativa += "Náuseas. ";
  if (checks[5].checked) narrativa += "Vómito. ";
  if (checks[6].checked) narrativa += "Mialgias. ";
  if (checks[7].checked) narrativa += "Artralgias. ";
  if (checks[8].checked) narrativa += "Exantema (registrar también en examen físico). ";
  if (checks[9].checked) narrativa += "Petequias en (registrar también en examen físico). ";

  narrativa += "";
  if (checks[0].checked) narrativa += "Dolor abdominal intenso y continuo. ";
  if (checks[1].checked) narrativa += "Vómitos persistentes. ";
  if (checks[2].checked) narrativa += "Diarrea. ";
  if (checks[3].checked) narrativa += "Letargo. ";
  if (checks[4].checked) narrativa += "Irritabilidad (principalmente en niños). ";
  if (checks[5].checked) narrativa += "Hipotensión postural. ";
  if (checks[6].checked) narrativa += "Lipotimia. ";

  document.getElementById("narrativa").innerText = narrativa;
}
</script>


