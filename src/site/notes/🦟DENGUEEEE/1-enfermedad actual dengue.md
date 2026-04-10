---
{"dg-publish":true,"permalink":"/dengueeee/1-enfermedad-actual-dengue/","dgPassFrontmatter":true}
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


<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Generador Narrativa Clínica</title>
<style>
  body { font-family: Arial, sans-serif; background:#f9f9f9; color:#333; margin:20px; }
  h2 { margin-top:30px; border-bottom:2px solid #ccc; padding-bottom:5px; }
  .grupo { margin-bottom:20px; }
  label { display:flex; align-items:center; gap:8px; margin:5px 0; }
  .opcion { display:inline-flex; align-items:center; gap:6px; }
  button { padding:10px 20px; background:#0066cc; color:#fff; border:none; border-radius:4px; cursor:pointer; }
  button:hover { background:#004999; }
  #resultado { white-space:pre-wrap; background:#fff; border:1px solid #ccc; padding:15px; margin-top:20px; }
</style>
</head>
<body>

<h1>Generador de Narrativa Clínica</h1>

<div class="grupo" data-slashes="0">
  <h2>¿HA PRESENTADO FIEBRE?</h2>
  <label><input type="checkbox" id="l1_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l1_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿HA PRESENTADO DOLOR EN ARTICULACIONES?</h2>
  <label><input type="checkbox" id="l2_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l2_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿HA PRESENTADO DOLOR MUSCULAR?</h2>
  <label><input type="checkbox" id="l3_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l3_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿HA PRESENTADO DOLOR DE CABEZA?</h2>
  <label><input type="checkbox" id="l4_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l4_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿HA PRESENTADO BROTE Y RASQUIÑA?</h2>
  <label><input type="checkbox" id="l5_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l5_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿HA VIAJADO EN LOS ÚLTIMOS 14 DÍAS?</h2>
  <label><input type="checkbox" id="l6_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l6_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿HA PRESENTADO SANGRADO POR ORIFICIOS NATURALES?</h2>
  <label><input type="checkbox" id="l7_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l7_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿ALGUIEN MÁS EN LA FAMILIA PRESENTA LOS MISMOS SÍNTOMAS O SIMILARES?</h2>
  <label><input type="checkbox" id="l8_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l8_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿PRESENCIA DE PETEQUIAS?</h2>
  <label><input type="checkbox" id="l9_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l9_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="3">
  <h2>¿PRESENCIA DE RASH CUTÁNEO?</h2>
  <label><input type="checkbox" id="l10_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l10_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿HA TENIDO DENGUE COMO ANTECEDENTE?</h2>
  <label><input type="checkbox" id="l11_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l11_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿DÓNDE VIVE?</h2>
  <label><input type="checkbox" id="l12_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l12_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿VIVE LEJOS DE LA INSTITUCIÓN DE SALUD?</h2>
  <label><input type="checkbox" id="l13_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l13_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿DÓNDE TRABAJA?</h2>
  <label><input type="checkbox" id="l14_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l14_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿CUÁL ES SU OCUPACIÓN?</h2>
  <label><input type="checkbox" id="l15_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l15_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿SUFRE DE ALGUNA ENFERMEDAD O ESTÁ EMBARAZADA?</h2>
  <label><input type="checkbox" id="l16_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l16_op2"><span class="opcion">NO</span></label>
</div>

<div class="grupo" data-slashes="0">
  <h2>¿HA CONSUMIDO ALGÚN MEDICAMENTO DURANTE ESTE CURSO DE LA ENFERMEDAD?</h2>
  <label><input type="checkbox" id="l17_op1"><span class="opcion">SI</span></label>
  <label><input type="checkbox" id="l17_op2"><span class="opcion">NO</span></label>
</div>

<button onclick="updateNarrativa()">Generar Narrativa</button>
<p id="resultado"></p>

<script>
function updateNarrativa() {
  const checks = document.querySelectorAll("input[type=checkbox]");
  let narrativa = "";
  let currentGroup = null;
  let groupHasContent = false;

  checks.forEach(chk => {
    if (chk.checked) {
      const grupo = chk.closest(".grupo");
      const header = grupo.querySelector("h2");
      if (currentGroup !== grupo) {
        if (currentGroup && groupHasContent) {
          const slashes = parseInt(currentGroup.getAttribute("data-slashes"), 10);
          narrativa += "\n".repeat(slashes);
        }
        currentGroup = grupo;
        groupHasContent = false;
        narrativa += header.textContent.trim() + "\n";
      }
      const span = chk.parentElement.querySelector(".opcion");
      narrativa += "- " + span.textContent.trim() + "\n";
      groupHasContent = true;
    }
  });

  if (currentGroup && groupHasContent) {
    const slashes = parseInt(currentGroup.getAttribute("data-slashes"), 10);
    narrativa += "\n".repeat(slashes);
  }
  
  // Mostrar el resultado en el elemento <p>
  document.getElementById("resultado").textContent = narrativa || "No se ha seleccionado ninguna opción.";
}
</script>

</body>
</html>