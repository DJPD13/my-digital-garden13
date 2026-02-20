---
{"dg-publish":true,"permalink":"/digital-garden/1-ea-13/prueba-cool/","dgPassFrontmatter":true}
---

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Narrativa Dinámica</title>
  <style>
    input[type="text"] {
      margin-left: 8px;
    }
  </style>
</head>
<body>

<h1>Parte 1</h1>

<label>
  <input type="checkbox" data-text="ACUDE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE, REFIERE ">
  ACUDE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE, REFIERE
</label>
<input type="text" placeholder="Motivo"><br><br>

<label>
  <input type="checkbox" data-text="ACUDE AL SERVICIO DE URGENCIAS ACOMPAÑADO DE ">
  ACUDE AL SERVICIO DE URGENCIAS ACOMPAÑADO DE
</label>
<input type="text" placeholder="Nombre del acompañante"><br><br>

<label>
  <input type="checkbox" data-text="ES TRAÍDO AL SERVICIO DE URGENCIAS POR MADRE QUIEN REFIERE QUE HA PRESENTADO ">
  ES TRAÍDO AL SERVICIO DE URGENCIAS POR MADRE QUIEN REFIERE QUE HA PRESENTADO
</label>
<input type="text" placeholder="Descripción"><br><br>

<h2>Síntoma cardinal</h2>

<label>
  <input type="checkbox" data-text="Cuadro clínico de ">
  Cuadro clínico de
</label>
<input type="text" placeholder="# días de evolución"> consistente en disnea en reposo<br><br>

<h3>Acompañado de</h3>

<label>
  <input type="checkbox" data-text="dolor con la respiración ">
  Dolor con la respiración
</label>
<input type="text" placeholder="Intensidad / localización"><br><br>

<button onclick="updateNarrativa()">Generar Narrativa</button>

<p id="resultado"></p>

<script>
function updateNarrativa() {
  const opciones = document.querySelectorAll("label");
  let narrativa = "";

  opciones.forEach(opcion => {
    const checkbox = opcion.querySelector("input[type='checkbox']");
    const textoLibre = opcion.nextElementSibling;

    if (checkbox && checkbox.checked) {
      narrativa += checkbox.dataset.text;
      if (textoLibre && textoLibre.value.trim() !== "") {
        narrativa += textoLibre.value.trim() + " ";
      }
    }
  });

  document.getElementById("resultado").textContent = narrativa.trim();
}
</script>

</body>
</html>