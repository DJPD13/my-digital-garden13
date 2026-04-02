---
{"dg-publish":true,"permalink":"/digital-garden/dengueeee/1-enfermedad-actual-dengue/","dgPassFrontmatter":true}
---

<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<style>
label {
  display: flex;
  gap: 8px;
  margin-bottom: 4px;
}
.grupo {
  margin-bottom: 15px;
}
.opcion input {
  margin: 0 4px;
}
</style>
</head>
<body>

<div class="grupo" data-slashes="0" data-niega="false">
<h1>AÑOS Y ACOMPAÑANTE</h1>
<label><input type="checkbox"><span class="opcion">PACIENTE DE <input type="text"> AÑOS ACUDE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE,</span></label>
<label><input type="checkbox"><span class="opcion">PACIENTE DE <input type="text"> AÑOS ACUDE AL SERVICIO DE URGENCIAS ACOMPAÑADO DE SU MADRE</span></label>
<label><input type="checkbox"><span class="opcion">PACIENTE DE <input type="text"> AÑOS ACUDE AL SERVICIO DE URGENCIAS EN BRAZOS DE SU MADRE</span></label>
</div>

<div class="grupo" data-slashes="0" data-niega="false">
<h2>DÍAS</h2>
<label><input type="checkbox"><span class="opcion">REFIERE CUADRO CLINICO DE <input type="text"> DÍAS DE EVOLUCIÓN CONSISTENTE EN</span></label>
</div>

<div class="grupo" data-slashes="0" data-niega="false">
<h3>FIEBRE</h3>
<label><input type="checkbox"><span class="opcion">PICOS FEBRILES NO CUANTIFICADOS ASOCIADO A</span></label>
<label><input type="checkbox"><span class="opcion">PICOS FEBRILES CUANTIFICADOS (ULTIMA MEDIDA: <input type="text"> GRADOS) ASOCIADO A</span></label>
</div>

<div class="grupo" data-slashes="0" data-niega="false">
<h4>AL MENOS 2 SINTOMAS</h4>
<label><input type="checkbox"><span class="opcion">DOLOR RETROCULAR,</span></label>
<label><input type="checkbox"><span class="opcion">CEFALEA,</span></label>
<label><input type="checkbox"><span class="opcion">NAUSEAS,</span></label>
<label><input type="checkbox"><span class="opcion">VOMITO,</span></label>
<label><input type="checkbox"><span class="opcion">MIALGIAS,</span></label>
<label><input type="checkbox"><span class="opcion">ARTRALGIAS,</span></label>
<label><input type="checkbox"><span class="opcion">EXANTEMA,</span></label>
<label><input type="checkbox"><span class="opcion">PETEQUIAS EN <input type="text">,</span></label>
</div>

<div class="grupo" data-slashes="0" data-niega="false">
<h4>SIGNOS DE ALARMA</h4>
<label><input type="checkbox"><span class="opcion">DOLOR ABDOMINAL INTENSO Y CONTINUO</span></label>
<label><input type="checkbox"><span class="opcion">EMESIS PERSITENTE</span></label>
<label><input type="checkbox"><span class="opcion">DIARREA</span></label>
<label><input type="checkbox"><span class="opcion">LETARGO</span></label>
<label><input type="checkbox"><span class="opcion">IRRITABILIDAD</span></label>
<label><input type="checkbox"><span class="opcion">HIPOTENSIÓN POSTURAL</span></label>
<label><input type="checkbox"><span class="opcion">LIPOTIMIA</span></label>
</div>

<div class="grupo" data-slashes="0" data-niega="true">
<h4>NIEGA</h4>
<label><input type="checkbox"><span class="opcion">DOLOR RETROCULAR,</span></label>
<label><input type="checkbox"><span class="opcion">CEFALEA,</span></label>
<label><input type="checkbox"><span class="opcion">NAUSEAS,</span></label>
<label><input type="checkbox"><span class="opcion">VOMITO,</span></label>
<label><input type="checkbox"><span class="opcion">MIALGIAS,</span></label>
<label><input type="checkbox"><span class="opcion">ARTRALGIAS,</span></label>
<label><input type="checkbox"><span class="opcion">EXANTEMA,</span></label>
<label><input type="checkbox"><span class="opcion">PETEQUIAS</span></label>
<label><input type="checkbox"><span class="opcion">DOLOR ABDOMINAL INTENSO Y CONTINUO</span></label>
<label><input type="checkbox"><span class="opcion">EMESIS PERSITENTE</span></label>
<label><input type="checkbox"><span class="opcion">DIARREA</span></label>
<label><input type="checkbox"><span class="opcion">LETARGO</span></label>
<label><input type="checkbox"><span class="opcion">IRRITABILIDAD</span></label>
<label><input type="checkbox"><span class="opcion">HIPOTENSIÓN POSTURAL</span></label>
<label><input type="checkbox"><span class="opcion">LIPOTIMIA</span></label>
</div>

<div class="grupo" data-slashes="0" data-niega="false">
<h4>CONCLUSIÓN</h4>
<label><input type="checkbox"><span class="opcion">SE CONSIDER PACIENTE CURSANDO CON CASO PROBABLE DE DENGUE EN SU DÍA <input type="text"> DE LA ENFERMEDAD</span></label>
</div>

<div class="grupo" data-slashes="0" data-niega="false">
<h4>CLASIFICACIÓN</h4>
<label><input type="checkbox"><span class="opcion">CLASIFICADO EN EL GRUPO A POR LO QUE PUEDE MANEJARSE AMBULATORIAMENTE DESPUÉS DE DESCARTAR SIGNOS DE ALARMA CON PARACLINICOS</span></label>
<label><input type="checkbox"><span class="opcion">CLASIFICADO EN EL GRUPO B1 POR LO QUE REQUIERE MANEJO INTRAHOSPITALARIO</span></label>
<label><input type="checkbox"><span class="opcion">CLASIFICADO EN EL GRUPO B2 POR LO QUE REQUIERE MANEJO INTRAHOSPITALARIO</span></label>
<label><input type="checkbox"><span class="opcion">CLASIFICADO EN EL GRUPO C POR LO QUE REQUIERE MANEJO INTRAHOSPITALARIO Y REMISIÓN A SEGUNDO NIVEL DE COMPLEJIDAD</span></label>
</div>

<button onclick="updateNarrativa()">Generar Narrativa</button>
<p id="resultado"></p>

<script>
function updateNarrativa() {
const checks = document.querySelectorAll("input[type=checkbox]");
let narrativa = "";

document.querySelectorAll(".grupo").forEach(grupo => {

  let textoGrupo = "";
  let incluirHeader = grupo.dataset.niega === "true";
  let header = grupo.querySelector("h1,h2,h3,h4");

  grupo.querySelectorAll("input[type=checkbox]").forEach(ch => {
    if (ch.checked) {
      let span = ch.nextElementSibling;

      span.childNodes.forEach(node => {
        if (node.nodeType === 3) textoGrupo += node.textContent;
        if (node.tagName === "INPUT" && node.value) textoGrupo += node.value;
      });

      textoGrupo += " ";
    }
  });

  if (textoGrupo.trim()) {
    if (incluirHeader && header) {
      narrativa += header.textContent.trim() + ": ";
    }

    narrativa += textoGrupo.trim();
    narrativa += "\n\n".repeat(parseInt(grupo.dataset.slashes || 0));
  }

});

document.getElementById("resultado").textContent = narrativa.trim();
}
</script>

</body>
</html>


