---
{"dg-publish":true,"permalink":"/digital-garden/1-ea-13/prueba-cool/","dgPassFrontmatter":true}
---

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Narrativa Dinámica</title>
  <style>
    body { font-family: Arial, sans-serif; }
    .opcion { margin: 6px 0; }
    .opcion input[type="text"] { margin-left: 8px; }
    #resultado { margin-top: 16px; padding: 10px; border: 1px solid #ccc; }
  </style>
</head>
<body>

  <h1>Parte 1</h1>

  <div class="opcion">
    <label>
      <input type="checkbox" id="sinAcompanante" data-text="ACUDE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE, REFIERE ">
      ACUDE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE, REFIERE
    </label>
    <input type="text" placeholder="Motivo / detalle (opcional)">
  </div>

  <div class="opcion">
    <label>
      <input type="checkbox" id="acompanado" data-text="ACUDE AL SERVICIO DE URGENCIAS ACOMPAÑADO DE ">
      ACUDE AL SERVICIO DE URGENCIAS ACOMPAÑADO DE
    </label>
    <input type="text" placeholder="Nombre del acompañante">
  </div>

  <div class="opcion">
    <label>
      <input type="checkbox" id="traidoMadre" data-text="ES TRAIDO AL SERVICIO DE URGENCIAS POR MADRE QUIEN REFIERE QUE HA PRESENTADO ">
      ES TRAIDO AL SERVICIO DE URGENCIAS POR MADRE QUIEN REFIERE QUE HA PRESENTADO
    </label>
    <input type="text" placeholder="Descripción (opcional)">
  </div>

  <h2>Síntoma cardinal</h2>

  <div class="opcion">
    <label>
      <input type="checkbox" id="disneaReposo" data-text="cuadro clinico de ">
      cuadro clinico de
    </label>
    <input type="text" placeholder="# días de evolución">
    <span> consistente en disnea en reposo</span>
  </div>

  <div class="opcion">
    <label>
      <input type="checkbox" id="disneaMin" data-text="cuadro clinico de ">
      cuadro clinico de
    </label>
    <input type="text" placeholder="# días de evolución">
    <span> consistente en disnea de minimos esfuerzos</span>
  </div>

  <div class="opcion">
    <label>
      <input type="checkbox" id="disneaMed" data-text="cuadro clinico de ">
      cuadro clinico de
    </label>
    <input type="text" placeholder="# días de evolución">
    <span> consistente en disnea de medianos esfuerzos</span>
  </div>

  <h3>Acompañado</h3>

  <div class="opcion">
    <label>
      <input type="checkbox" id="dolorResp" data-text="dolor con la respiración ">
      dolor con la respiración
    </label>
    <input type="text" placeholder="Detalles (opcional)">
  </div>

  <div class="opcion">
    <label>
      <input type="checkbox" id="tosSeca" data-text="tos seca ">
      tos seca
    </label>
    <input type="text" placeholder="Detalles (opcional)">
  </div>

  <div class="opcion">
    <label>
      <input type="checkbox" id="tosMucopur" data-text="tos con esputo mucopurulento ">
      tos con esputo mucopurulento
    </label>
    <input type="text" placeholder="Detalles (opcional)">
  </div>

  <div class="opcion">
    <label>
      <input type="checkbox" id="tosVerdoso" data-text="tos con esputo verdoso ">
      tos con esputo verdoso
    </label>
    <input type="text" placeholder="Detalles (opcional)">
  </div>

  <div class="opcion">
    <label>
      <input type="checkbox" id="tirajeSub" data-text="tiraje subcostal ">
      tiraje subcostal
    </label>
    <input type="text" placeholder="Detalles (opcional)">
  </div>

  <div class="opcion">
    <label>
      <input type="checkbox" id="tirajeInter" data-text="tiraje intercostal ">
      tiraje intercostal
    </label>
    <input type="text" placeholder="Detalles (opcional)">
  </div>

  <div class="opcion">
    <label>
      <input type="checkbox" id="tirajeSupra" data-text="tiraje supraclavicular ">
      tiraje supraclavicular
    </label>
    <input type="text" placeholder="Detalles (opcional)">
  </div>

  <button onclick="updateNarrativa()">Generar Narrativa</button>

  <p id="resultado"></p>

  <script>
    // ✅ CONEXIÓN: si se marca "acompanado" → se marca "dolorResp"
    // y si se desmarca → se desmarca también (comportamiento en espejo)
    document.getElementById("acompanado").addEventListener("change", function () {
      const dolor = document.getElementById("dolorResp");
      dolor.checked = this.checked;
    });

    function updateNarrativa() {
      // Recorremos cada bloque de opción (checkbox + input de texto)
      const opciones = document.querySelectorAll(".opcion");
      let narrativa = "";

      opciones.forEach(op => {
        const checkbox = op.querySelector("input[type='checkbox']");
        const inputTxt = op.querySelector("input[type='text']");
        const extra = inputTxt ? inputTxt.value.trim() : "";

        if (checkbox && checkbox.checked) {
          // Texto fijo (data-text)
          narrativa += checkbox.dataset.text || "";

          // Texto libre (si existe)
          if (extra !== "") {
            narrativa += extra + " ";
          } else {
            // Si no puso texto, al menos dejamos un espacio al final del fragmento
            narrativa += "";
          }

          // Si hay un <span> con texto complementario (ej: "consistente en disnea...")
          const span = op.querySelector("span");
          if (span) {
            narrativa += span.textContent.trim() + " ";
          }
        }
      });

      document.getElementById("resultado").textContent = narrativa.trim();
    }
  </script>

</body>
</html>