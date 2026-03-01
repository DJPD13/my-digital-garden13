---
{"dg-publish":true,"permalink":"/digital-garden/3-examenes-fisicos/exfi-adulto-check/","dgPassFrontmatter":true}
---

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Examen Físico – Generador de Narrativa</title>
  <style>
    body {
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      line-height: 1.35;
      margin: 16px;
      max-width: 1000px;
      background: #fcfcfc;
    }
    h1, h2, h3, h4 {
      margin: 24px 0 16px;
      padding-bottom: 3px;
      font-weight: 600;
    }
    .group {
      margin: 0 0 26px 0;
      padding-left: 12px;
      border-left: 3px solid #5f8ab0;
    }
    label {
      display: block;
      margin: 6px 0;
      cursor: pointer;
    }
    .child {
      margin-left: 24px;
      padding-left: 12px;
      border-left: 2px dashed #b0c8dd;
    }
    .hidden {
      display: none;
    }
    input[type="text"] {
      margin: 0 8px 0 4px;
      min-width: 210px;
      padding: 3px 6px;
      border: 1px solid #aaa;
      border-radius: 5px;
    }
    select {
      margin: 0 8px 0 4px;
      padding: 3px 6px;
      border-radius: 5px;
    }
    button {
      background: #1e4468;
      color: white;
      border: none;
      font-size: 1.2rem;
      padding: 8px 30px;
      border-radius: 40px;
      margin: 25px 0 12px;
      cursor: pointer;
      font-weight: 600;
    }
    button:hover {
      background: #0f2b44;
    }
    #resultado {
      white-space: pre-wrap;
      border: 2px solid #b4c9e2;
      background: #f3f7fd;
      padding: 16px;
      border-radius: 16px;
      margin-top: 18px;
      font-family: 'Courier New', monospace;
    }
  </style>
</head>
<body>

  <!-- TENDENCIAS -->
  <h1>TENDENCIAS:</h1>
  <div class="group" data-header="1">
    <label>
      <input type="checkbox" id="h1" onchange="toggleChildren(this, 'h1_children'); updateNarrativa()"> 
      TENDENCIAS
    </label>
    <div id="h1_children" class="child hidden">
      <label><input type="checkbox" id="h1_op1" onchange="updateNarrativa()" /> REGULARES CONDICIONES GENERALES</label>
      <label><input type="checkbox" id="h1_op2" onchange="updateNarrativa()" /> SOMNOLIENTO</label>
      <label><input type="checkbox" id="h1_op3" onchange="updateNarrativa()" /> FEBRIL</label>
      <label><input type="checkbox" id="h1_op4" onchange="updateNarrativa()" /> CON SIGNOS DE DESHIDRATACIÓN</label>
      <label><input type="checkbox" id="h1_op5" onchange="updateNarrativa()" /> SATURANDO EN METAS CON CANULA NASAL A <input type="text" id="h1_op5_text" onchange="updateNarrativa()" /> L/MIN</label>
    </div>
  </div>

  <!-- PIEL -->
  <h2>PIEL:</h2>
  <div class="group" data-header="2">
    <label>
      <input type="checkbox" id="h2" onchange="toggleChildren(this, 'h2_children'); updateNarrativa()"> 
      PIEL
    </label>
    <div id="h2_children" class="child hidden">
      <label><input type="checkbox" id="h2_op1" onchange="updateNarrativa()" /> EXANTEMA MACULAR EN TRONCO Y EXTREMIDADES</label>
      <label><input type="checkbox" id="h2_op2" onchange="updateNarrativa()" /> MACULAS ERITEMATOSAS EN <input type="text" id="h2_op2_text" onchange="updateNarrativa()" /></label>
      <label><input type="checkbox" id="h2_op3" onchange="updateNarrativa()" /> PAPULAS EN <input type="text" id="h2_op3_text" onchange="updateNarrativa()" /></label>
      <label><input type="checkbox" id="h2_op4" onchange="updateNarrativa()" /> PÁPULAS DE GOTTRON (EN DORSO DE LA MANO)</label>
      <label><input type="checkbox" id="h2_op5" onchange="updateNarrativa()" /> PLACAS ERITEMATOSAS</label>
      <label><input type="checkbox" id="h2_op6" onchange="updateNarrativa()" /> EXCORIACIONES CON COSTRA POR POSIBLE RASCADO</label>
      <label><input type="checkbox" id="h2_op7" onchange="updateNarrativa()" /> SE EVIDENCIA LACERACIÓN(ES) EN <input type="text" id="h2_op7_text" onchange="updateNarrativa()" /></label>
      <label><input type="checkbox" id="h2_op8" onchange="updateNarrativa()" /> SE EVIDENCIA</label>
      <label><input type="checkbox" id="h2_op9" onchange="updateNarrativa()" /> heridas</label>
    </div>
  </div>

  <!-- CABEZA -->
  <h3>CABEZA:</h3>
  <div class="group" data-header="3">
    <label>
      <input type="checkbox" id="h3" onchange="toggleChildren(this, 'h3_children'); updateNarrativa()"> 
      CABEZA
    </label>
    <div id="h3_children" class="child hidden">
      <label><input type="checkbox" id="h3_op1" onchange="updateNarrativa()" /> CONDUCTOS AUDITIVOS CON TAPON DE CERUMEN IMPACTADO POR LO QUE NO SE VISUALIZA MEMEBRANA TIMPANICA</label>
      <label><input type="checkbox" id="h3_op2" onchange="updateNarrativa()" /> CONDUCTO AUDITIVO <input type="text" id="h3_op2_text" onchange="updateNarrativa()" /> CON ERITEMA SIN SALIDA DE PUS</label>
    </div>
  </div>

  <!-- CAVIDAD ORAL -->
  <h4>CAVIDAD ORAL:</h4>
  <div class="group" data-header="4">
    <label>
      <input type="checkbox" id="h4" onchange="toggleChildren(this, 'h4_children'); updateNarrativa()"> 
      CAVIDAD ORAL
    </label>
    <div id="h4_children" class="child hidden">
      <label><input type="checkbox" id="h4_op1" onchange="updateNarrativa()" /> úlceras</label>
      <label><input type="checkbox" id="h4_op2" onchange="updateNarrativa()" /> llagas</label>
      <label><input type="checkbox" id="h4_op3" onchange="updateNarrativa()" /> sin lesiones</label>
    </div>
  </div>

  <!-- CUELLO -->
  <h5>CUELLO:</h5>
  <div class="group" data-header="5">
    <label>
      <input type="checkbox" id="h5" onchange="toggleChildren(this, 'h5_children'); updateNarrativa()"> 
      CUELLO
    </label>
    <div id="h5_children" class="child hidden">
      <label><input type="checkbox" id="h5_op1" onchange="updateNarrativa()" /> MARCADA INGUGITACIÓN YUGULAR</label>
      <label><input type="checkbox" id="h5_op2" onchange="updateNarrativa()" /> limitada</label>
      <label><input type="checkbox" id="h5_op3" onchange="updateNarrativa()" /> doloroso a la movilización</label>
      <label><input type="checkbox" id="h5_op4" onchange="updateNarrativa()" /> LESIÓN EN ZONA I</label>
      <label><input type="checkbox" id="h5_op5" onchange="updateNarrativa()" /> LESIÓN EN ZONA II</label>
      <label><input type="checkbox" id="h5_op6" onchange="updateNarrativa()" /> LESIÓN EN ZONA III</label>
    </div>
  </div>

  <!-- TÓRAX -->
  <h6>TÓRAX:</h6>
  <div class="group" data-header="6">
    <label>
      <input type="checkbox" id="h6" onchange="toggleChildren(this, 'h6_children'); updateNarrativa()"> 
      TÓRAX
    </label>
    <div id="h6_children" class="child hidden">
      <label><input type="checkbox" id="h6_op1" onchange="updateNarrativa()" /> CREPITOS EN <input type="text" id="h6_op1_text" onchange="updateNarrativa()" /></label>
      <label><input type="checkbox" id="h6_op2" onchange="updateNarrativa()" /> SIBILANCIAS EN <input type="text" id="h6_op2_text" onchange="updateNarrativa()" /></label>
      <label><input type="checkbox" id="h6_op3" onchange="updateNarrativa()" /> RONCUS EN <input type="text" id="h6_op3_text" onchange="updateNarrativa()" /></label>
      <label><input type="checkbox" id="h6_op4" onchange="updateNarrativa()" /> DOLOR A LA PALPACIÓN EN <input type="text" id="h6_op4_text" onchange="updateNarrativa()" /></label>
      <label><input type="checkbox" id="h6_op5" onchange="updateNarrativa()" /> dolor en precordio</label>
      <label><input type="checkbox" id="h6_op6" onchange="updateNarrativa()" /> dolor en reposo</label>
    </div>
  </div>

  <!-- ABDOMEN -->
  <h7>ABDOMEN:</h7>
  <div class="group" data-header="7">
    <label>
      <input type="checkbox" id="h7" onchange="toggleChildren(this, 'h7_children'); updateNarrativa()"> 
      ABDOMEN
    </label>
    <div id="h7_children" class="child hidden">
      <label><input type="checkbox" id="h7_op1" onchange="updateNarrativa()" /> DOLOR A LA PALPACIÓN EN HIPOCONDRIO DERECHO</label>
      <label><input type="checkbox" id="h7_op2" onchange="updateNarrativa()" /> DOLOR A LA PALPACIÓN EN HIPOCONDRIO IZQUIERDO</label>
      <label><input type="checkbox" id="h7_op3" onchange="updateNarrativa()" /> DOLOR A LA PALPACIÓN EN EPIGASTRIO</label>
      <label><input type="checkbox" id="h7_op4" onchange="updateNarrativa()" /> DOLOR A LA PALPACIÓN EN FLANCO DERECHO</label>
      <label><input type="checkbox" id="h7_op5" onchange="updateNarrativa()" /> DOLOR A LA PALPACIÓN EN FLANCO IZQUIERDO</label>
      <label><input type="checkbox" id="h7_op6" onchange="updateNarrativa()" /> DOLOR A LA PALPACIÓN EN MESOGASTRIO</label>
      <label><input type="checkbox" id="h7_op7" onchange="updateNarrativa()" /> DOLOR A LA PALPACIÓN EN FOSA ILIACA DERECHA</label>
      <label><input type="checkbox" id="h7_op8" onchange="updateNarrativa()" /> DOLOR A LA PALPACIÓN EN FOSA ILIACA IZQUIERDA</label>
    </div>
  </div>

  <!-- OSTEOMUSCULAR -->
  <h8>OSTEOMUSCULAR:</h8>
  <div class="group" data-header="8">
    <label>
      <input type="checkbox" id="h8" onchange="toggleChildren(this, 'h8_children'); updateNarrativa()"> 
      OSTEOMUSCULAR
    </label>
    <div id="h8_children" class="child hidden">
      <label><input type="checkbox" id="h8_op1" onchange="updateNarrativa()" /> dolor a la palpación en maleolo medial y lateral</label>
      <label><input type="checkbox" id="h8_op2" onchange="updateNarrativa()" /> dolor a la palpación en maleolo medial</label>
      <label><input type="checkbox" id="h8_op3" onchange="updateNarrativa()" /> dolor a la palpación en maleolo lateral</label>
    </div>
  </div>

  <!-- NEUROLÓGICO -->
  <h9>NEUROLÓGICO:</h9>
  <div class="group" data-header="9">
    <label>
      <input type="checkbox" id="h9" onchange="toggleChildren(this, 'h9_children'); updateNarrativa()"> 
      NEUROLÓGICO
    </label>
    <div id="h9_children" class="child hidden">
      <label><input type="checkbox" id="h9_op1" onchange="updateNarrativa()" /> DESVIACIÓN DE LA COMISURA FACIAL</label>
      <label><input type="checkbox" id="h9_op2" onchange="updateNarrativa()" /> PTSOSIS PARPEBRAL</label>
      <label><input type="checkbox" id="h9_op3" onchange="updateNarrativa()" /> PARESIA DEL AEXTREMIDAD SUPERIOR <input type="text" id="h9_op3_text" onchange="updateNarrativa()" /></label>
    </div>
  </div>

  <button onclick="updateNarrativa()">Generar Narrativa</button>
  <p id="resultado"></p>

  <script>
    function toggleChildren(checkbox, childId) {
      const childContainer = document.getElementById(childId);
      if (checkbox.checked) {
        childContainer.classList.remove("hidden");
      } else {
        childContainer.classList.add("hidden");
      }
    }

    function updateNarrativa() {
      const checks = document.querySelectorAll("input[type=checkbox]");
      let narrativa = "";

      // Headers y sus valores por defecto
      const headers = [
        { id: "h1", label: "TENDENCIAS", default: "BUENAS CONDICIONES GENERALES, ALERTA, CONCIENTE, ORIENTADO EN LAS TRES ESFERAS, AFEBRIL, HIDRATADO" },
        { id: "h2", label: "PIEL", default: "SIN LESIONES APARENTES" },
        { id: "h3", label: "CABEZA", default: "SIN LESIONES EN CARA, PABELLON AURICULAR INTEGRO, CONDUCTOS AUDITIVOS SIN ERITEMA, U OTORREA, MEMBRANA TIMPANICA NO ABOMBADA Y NO ROTA, NO SE EVIDENCIAN ADENOMEGALIAS RETROAURICULARES O SUBMANDIBULARES" },
        { id: "h4", label: "CAVIDAD ORAL", default: "NORMAL" },
        { id: "h5", label: "CUELLO", default: "SIN LESIONES, SIN INGURGITACION YUGULAR, SIN SOPLO CAROTIDEO, SIN ADENOMEGALIAS, SIN PUNTOS GATILLOS, SIN LATERALIZACIÓN" },
        { id: "h6", label: "TÓRAX", default: "SIN LESIONES APARENTES, SIMETRICAMENTE EXPANSIBLE, SIN TIRAJE SUB O INTERCOSTAL, RUIDOS CARDIACO DE ADECUADA INTENSIDAD RITMICOS Y SIN SOPLOS. MURMULO VESICULAR CONSERVADO SIN RUIDOS SOBREAGREGADOS" },
        { id: "h7", label: "ABDOMEN", default: "SIN EQUIMOSIS, BLANDO, PERISTALTISMO PRESENTE, NO DOLOROSO A LA PALPACIÓN SUPERFICIAL O PROFUNDA, SIN SIGNOS DE IRRITACIÓN PERITONEAL." },
        { id: "h8", label: "OSTEOMUSCULAR", default: "EXTREMIDADES SIN DEFORMIDADES APARENTES, PULSOS DISTALES PRESENTES, SIN LIMITACIÓN PARA LOS ARCOS DE MOVIMIENTO." },
        { id: "h9", label: "NEUROLÓGICO", default: "SIN FOCALIZACIÓN SENSITIVA O MOTORA, SIN DESVIACIÓN DE LA COMISURA LABIAL, SIN PTOSIS PALPEBRAL, MOVIMINETO S OCULARES SIN PARESIAS, FUERZA 5/5 EN 4 EXTREMIDADES, REFLEJOS OSTEOTENDINOSOS ++ SIMETRICOS" }
      ];

      headers.forEach(header => {
        const el = document.getElementById(header.id);
        let text = `${header.label}: `;
        if (el.checked) {
          const checkedOptions = document.querySelectorAll(`#${header.id}_children input[type=checkbox]:checked`);
          const selectedOptions = Array.from(checkedOptions).map(opt => opt.nextSibling.nodeValue.trim());
          if (selectedOptions.length > 0) {
            text += selectedOptions.join(", ");
          } else {
            text += header.default;
          }
        } else {
          text += header.default;
        }
        narrativa += text + "\n";
      });

      document.getElementById("resultado").textContent = narrativa.trim();
    }
  </script>

</body>
</html>