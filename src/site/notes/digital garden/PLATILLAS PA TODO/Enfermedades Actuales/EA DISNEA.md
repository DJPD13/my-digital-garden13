---
{"dg-publish":true,"permalink":"/digital-garden/platillas-pa-todo/enfermedades-actuales/ea-disnea/","dgPassFrontmatter":true}
---


<h3>Síntomas</h3>
<label><input type="checkbox" onclick="updateNarrativa()"> Fiebre</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> Dolor abdominal</label><br>
<label><input type="checkbox" onclick="updateNarrativa()"> Erupción cutánea</label><br>

<h3>Narrativa generada</h3>
<p id="narrativa">Resumen clínico: ... Fin del reporte.</p>

<script>
function updateNarrativa() {
  let narrativa = "Resumen clínico: ";
  const checks = document.querySelectorAll("input[type=checkbox]");
  if (checks[0].checked) narrativa += "El paciente presenta fiebre. ";
  if (checks[1].checked) narrativa += "Se reporta dolor abdominal. ";
  if (checks[2].checked) narrativa += "Se observa erupción cutánea. ";
  narrativa += "Fin del reporte.";
  document.getElementById("narrativa").innerText = narrativa;
}
</script>

