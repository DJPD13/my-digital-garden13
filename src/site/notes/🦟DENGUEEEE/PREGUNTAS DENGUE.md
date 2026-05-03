---
{"dg-publish":true,"permalink":"/🦟DENGUEEEE/PREGUNTAS DENGUE/","dgPassFrontmatter":true,"updated":"2026-04-26T18:09:17.822-05:00","dg-note-properties":{}}
---

<html lang="es">
<head>
<meta charset="UTF-8">
<title>Generador Narrativa Clínica</title>

<style>
  body {
    font-family: Arial, sans-serif !important;
    background: #f9f9f9 !important;
    color: #333 !important;
    margin: 12px !important;
    font-size: 14px !important;
  }

  h1 {
    font-size: 20px !important;
    margin-bottom: 12px !important;
  }

  .grupo {
    display: grid !important;
    grid-template-columns: 1fr auto auto !important;
    gap: 8px !important;
    align-items: center !important;
    background: #fff !important;
    padding: 6px 8px !important;
    margin-bottom: 5px !important;
    border: 1px solid #ddd !important;
    border-radius: 4px !important;
  }

  .pregunta {
    font-weight: bold !important;
  }

  label {
    display: inline-flex !important;
    align-items: center !important;
    gap: 4px !important;
    white-space: nowrap !important;
  }

  input[type="text"] {
    width: 260px !important;
    min-width: 260px !important;
    max-width: 260px !important;
    padding: 5px !important;
    box-sizing: border-box !important;
  }

  button {
    margin-top: 12px !important;
    padding: 10px 18px !important;
    background: #0066cc !important;
    color: #fff !important;
    border: none !important;
    border-radius: 4px !important;
    cursor: pointer !important;
    font-family: Arial, sans-serif !important;
  }

  button:hover {
    background: #004999 !important;
  }

  #resultadoContainer {
    margin-top: 15px !important;
    display: none;
    position: relative !important;

    width: 850px !important;
    min-width: 850px !important;
    max-width: 850px !important;

    box-sizing: border-box !important;
  }

  #resultadoTexto,
  textarea#resultadoTexto {
    width: 850px !important;
    min-width: 850px !important;
    max-width: 850px !important;

    height: 340px !important;
    min-height: 340px !important;
    max-height: 340px !important;

    padding: 20px !important;
    padding-top: 65px !important;

    border: 2px solid #ccc !important;
    border-radius: 8px !important;

    font-family: Arial, sans-serif !important;
    font-size: 16px !important;
    line-height: 1.6 !important;

    resize: none !important;
    background: #fff !important;
    color: #333 !important;

    box-sizing: border-box !important;
    display: block !important;
    overflow-y: auto !important;
    margin: 0 !important;
  }

  #btnCopiar {
    position: absolute !important;
    top: 15px !important;
    right: 15px !important;

    margin: 0 !important;
    background: #28a745 !important;
    padding: 10px 20px !important;

    font-size: 14px !important;
    font-weight: bold !important;
    z-index: 10 !important;

    border-radius: 6px !important;
    box-shadow: 0 2px 8px rgba(0,0,0,0.2) !important;

    color: white !important;
    border: none !important;
    cursor: pointer !important;
  }

  #btnCopiar:hover {
    background: #218838 !important;
    box-shadow: 0 4px 12px rgba(0,0,0,0.3) !important;
  }

  .mensajeCopiado {
    position: absolute !important;
    top: 25px !important;
    right: 145px !important;

    color: #28a745 !important;
    font-weight: bold !important;
    font-size: 14px !important;

    display: none !important;
    z-index: 11 !important;

    background: white !important;
    padding: 5px 10px !important;
    border-radius: 4px !important;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1) !important;
  }
</style>
</head>

<body>

<h1>Generador de Narrativa Clínica</h1>

<div id="cuestionario"></div>

<button onclick="generarNarrativa()">Generar Narrativa</button>

<div id="resultadoContainer">
  <textarea id="resultadoTexto" rows="14" cols="100" readonly></textarea>
  <button id="btnCopiar" onclick="copiarTexto()">📋 Copiar Texto</button>
  <span id="mensajeCopiado" class="mensajeCopiado">¡Texto copiado!</span>
</div>

<script>
const preguntas = [
  "¿Ha presentado fiebre?",
  "¿Ha presentado dolor en articulaciones?",
  "¿Ha presentado dolor muscular?",
  "¿Ha presentado dolor de cabeza?",
  "¿Ha presentado brote y rasquiña?",
  "¿Ha viajado en los últimos 14 días?",
  "¿Ha presentado sangrado por orificios naturales?",
  "¿Alguien más en la familia presenta los mismos síntomas o similares?",
  "¿Presencia de petequias?",
  "¿Presencia de rash cutáneo?",
  "¿Ha tenido dengue como antecedente?",
  "¿Vive lejos de la institución de salud?",
  "¿Sufre de alguna enfermedad o está embarazada?",
  "¿Ha consumido algún medicamento durante este curso de la enfermedad?"
];

const camposTexto = [
  "¿Dónde vive?",
  "¿Dónde trabaja?",
  "¿Cuál es su ocupación?"
];

const contenedor = document.getElementById("cuestionario");

preguntas.forEach((pregunta, index) => {
  const div = document.createElement("div");
  div.className = "grupo";

  div.innerHTML = `
    <div class="pregunta">${pregunta}</div>
    <label>
      <input type="radio" name="pregunta_${index}" value="Sí">
      Sí
    </label>
    <label>
      <input type="radio" name="pregunta_${index}" value="No">
      No
    </label>
  `;

  contenedor.appendChild(div);
});

camposTexto.forEach((pregunta, index) => {
  const div = document.createElement("div");
  div.className = "grupo";
  div.style.gridTemplateColumns = "1fr auto";

  div.innerHTML = `
    <div class="pregunta">${pregunta}</div>
    <input type="text" id="texto_${index}" placeholder="Escriba aquí">
  `;

  contenedor.appendChild(div);
});

function generarNarrativa() {
  let narrativa = "";
  let hayRespuestasPreguntas = false;
  let hayRespuestasTexto = false;

  preguntas.forEach((pregunta, index) => {
    const seleccion = document.querySelector(`input[name="pregunta_${index}"]:checked`);

    if (seleccion) {
      if (hayRespuestasPreguntas) {
        narrativa += "\n\n";
      }

      narrativa += `${pregunta} ${seleccion.value}.`;
      hayRespuestasPreguntas = true;
    }
  });

  camposTexto.forEach((pregunta, index) => {
    const valor = document.getElementById(`texto_${index}`).value.trim();

    if (valor) {
      hayRespuestasTexto = true;
    }
  });

  if (hayRespuestasPreguntas && hayRespuestasTexto) {
    narrativa += "\n\n";
  }

  let primerTexto = true;

  camposTexto.forEach((pregunta, index) => {
    const valor = document.getElementById(`texto_${index}`).value.trim();

    if (valor) {
      if (!primerTexto) {
        narrativa += "\n\n";
      }

      narrativa += `${pregunta} ${valor}.`;
      primerTexto = false;
    }
  });

  const resultadoTexto = document.getElementById("resultadoTexto");
  const resultadoContainer = document.getElementById("resultadoContainer");

  resultadoTexto.value = narrativa || "No se ha seleccionado ni escrito ninguna información.";
  resultadoContainer.style.display = "block";

  document.getElementById("mensajeCopiado").style.display = "none";
}

function copiarTexto() {
  const resultadoTexto = document.getElementById("resultadoTexto");
  const mensajeCopiado = document.getElementById("mensajeCopiado");

  resultadoTexto.select();
  resultadoTexto.setSelectionRange(0, 99999);

  navigator.clipboard.writeText(resultadoTexto.value).then(() => {
    mensajeCopiado.style.display = "inline";

    setTimeout(() => {
      mensajeCopiado.style.display = "none";
    }, 2000);
  }).catch(err => {
    try {
      document.execCommand("copy");

      mensajeCopiado.style.display = "inline";

      setTimeout(() => {
        mensajeCopiado.style.display = "none";
      }, 2000);
    } catch (e) {
      alert("No se pudo copiar el texto. Por favor, selecciónalo manualmente.");
    }
  });
}
</script>

</body>
</html>















