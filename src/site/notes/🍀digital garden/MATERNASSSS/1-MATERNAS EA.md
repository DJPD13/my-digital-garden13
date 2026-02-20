---
{"dg-publish":true,"permalink":"/digital-garden/maternassss/1-maternas-ea/","dgPassFrontmatter":true}
---

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Narrativa Dinámica</title>
  <style>
    body { font-family: Arial, sans-serif; line-height: 1.35; }
    .grupo { margin: 14px 0 18px; }
    label { display: block; margin: 6px 0; }
    input[type="text"] { margin: 0 6px; min-width: 70px; }
    #resultado { margin-top: 16px; padding: 12px; border: 1px solid #ccc; }

    /* Normalización de encabezados (HTML solo permite h1..h6) */
    h1,h2,h3,h4,h5,h6 { margin: 12px 0 8px; font-weight: 800; }
    .h7,.h8,.h9,.h10,.h11,.h12,.h13,.h14,.h15,.h16,.h17,.h18,.h19,.h20,
    .h21,.h22,.h23,.h24,.h25,.h26,.h27,.h28,.h29,.h30,.h31,.h32,.h33,.h34,
    .h35,.h36,.h37,.h38,.h39,.h40,.h41,.h42,.h43,.h44,.h45{
      font-size: 1em;
      margin: 12px 0 8px;
      font-weight: 800;
      display: block;
    }
  </style>
</head>
<body>

  <!-- header 1:MC: " ** " / -->
  <div class="grupo" data-slashes="1">
    <h1>MC: " <input type="text"> " </h1>
  </div>

  <!-- header 2:FORMULA OBSTÉTRICA: G**P** / -->
  <div class="grupo" data-slashes="1">
    <h2>FORMULA OBSTÉTRICA: G<input type="text">P<input type="text"> </h2>
  </div>

  <!-- header 3:FECHA ÚLTIMO PARTO:  **-**-** / -->
  <div class="grupo" data-slashes="1">
    <h3>FECHA ÚLTIMO PARTO:  <input type="text">-<input type="text">-<input type="text"> </h3>
  </div>

  <!-- header 4:FECHA DE ULTIMA MENSTRUACIÓN: **-**-** / -->
  <div class="grupo" data-slashes="1">
    <h4>FECHA DE ULTIMA MENSTRUACIÓN: <input type="text">-<input type="text">-<input type="text"> </h4>
  </div>

  <!-- header 5:HEMOCLASIFICACIÓN: / -->
  <div class="grupo" data-slashes="1">
    <h5>HEMOCLASIFICACIÓN: </h5>
    <label><input type="checkbox" id="h5_op1"> O+</label>
    <label><input type="checkbox" id="h5_op2"> O-</label>
    <label><input type="checkbox" id="h5_op3"> A+</label>
    <label><input type="checkbox" id="h5_op4"> A-</label>
    <label><input type="checkbox" id="h5_op5"> B+</label>
    <label><input type="checkbox" id="h5_op6"> B-</label>
    <label><input type="checkbox" id="h5_op7"> AB+</label>
    <label><input type="checkbox" id="h5_op8"> AB-</label>
  </div>

  <!-- header 6:CONSULTA PRECONCEPCIONAL:/ -->
  <div class="grupo" data-slashes="1">
    <h6>CONSULTA PRECONCEPCIONAL:</h6>
    <label><input type="checkbox" id="h6_op1"> NO</label>
    <label><input type="checkbox" id="h6_op2"> SI</label>
  </div>

  <!-- header 7:PLANIFICACIÓN PRECONCEPCIONAL: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h7">PLANIFICACIÓN PRECONCEPCIONAL: </h6>
    <label><input type="checkbox" id="h7_op1"> POMEROY</label>
    <label><input type="checkbox" id="h7_op2"> INYECCIÓN MENSUAL</label>
    <label><input type="checkbox" id="h7_op3"> INYECCIÓN TRIMESTRAL</label>
    <label><input type="checkbox" id="h7_op4"> ANTICONCEPTIVOS ORALES</label>
    <label><input type="checkbox" id="h7_op5"> IMPLANTE SUBDERMICO</label>
    <label><input type="checkbox" id="h7_op6"> NO PLANIFICABA ANTERIORMENTE</label>
  </div>

  <!-- header 8:CONTROLES PRENATALES: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h8">CONTROLES PRENATALES: </h6>
    <label><input type="checkbox" id="h8_op1"><input type="text"> (APORTA HISTORIA CLINICA)</label>
    <label><input type="checkbox" id="h8_op2"><input type="text"> (NO APORTA HISTORIA CLINICA)</label>
    <label><input type="checkbox" id="h8_op3"> NO RECUERDA (NO APORTA HISTORIA CLINICA)</label>
  </div>

  <!-- header 9:EMBARAZO: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h9">EMBARAZO: </h6>
    <label><input type="checkbox" id="h9_op1"> PLANEADO Y ACEPTADO</label>
    <label><input type="checkbox" id="h9_op2"> NO PLANEADO Y ACEPTADO</label>
  </div>

  <!-- header 10:PLAN DE PLANIFICACIÓN POSTPARTO: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h10">PLAN DE PLANIFICACIÓN POSTPARTO: </h6>
    <label><input type="checkbox" id="h10_op1"> POMEROY</label>
    <label><input type="checkbox" id="h10_op2"> INYECCIÓN MENSUAL</label>
    <label><input type="checkbox" id="h10_op3"> INYECCIÓN TRIMESTRAL</label>
    <label><input type="checkbox" id="h10_op4"> ANTICONCEPTIVOS ORALES</label>
    <label><input type="checkbox" id="h10_op5"> IMPLANTE SUBDERMICO</label>
    <label><input type="checkbox" id="h10_op6"> NO DESEA</label>
  </div>

  <!-- header 11: PROCEDENCIA: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h11"> PROCEDENCIA: </h6>
    <label><input type="checkbox" id="h11_op1"> VILLANUEVA CASANARE</label>
  </div>

  <!-- header 12: DIRECCIÓN: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h12"> DIRECCIÓN: </h6>
    <label><input type="checkbox" id="h12_op1"> CARRERA <input type="text"> # <input type="text">-<input type="text"></label>
    <label><input type="checkbox" id="h12_op2"> CALLE <input type="text"> #<input type="text">-<input type="text"></label>
    <label><input type="checkbox" id="h12_op3"> DIAGONAL <input type="text">#<input type="text">-<input type="text"></label>
  </div>

  <!-- header 13: TELÉFONO: ** / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h13"> TELÉFONO: <input type="text"> </h6>
  </div>

  <!-- header 14: ESTADO CIVIL:  / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h14"> ESTADO CIVIL:  </h6>
    <label><input type="checkbox" id="h14_op1"> UNION LIBRE</label>
    <label><input type="checkbox" id="h14_op2"> CASADA</label>
    <label><input type="checkbox" id="h14_op3"> SOLTERA</label>
  </div>

  <!-- header 15: OCUPACIÓN: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h15"> OCUPACIÓN: </h6>
    <label><input type="checkbox" id="h15_op1"> AMA DE CASA</label>
    <label><input type="checkbox" id="h15_op2"> OFICIOS VARIOS</label>
    <label><input type="checkbox" id="h15_op3"> <input type="text"></label>
  </div>

  <!-- header 16: ESCOLARIDAD: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h16"> ESCOLARIDAD: </h6>
    <label><input type="checkbox" id="h16_op1"> BACHILLER</label>
    <label><input type="checkbox" id="h16_op2"> PREGRADO</label>
    <label><input type="checkbox" id="h16_op3"> TECNOLOGO</label>
  </div>

  <!-- header 17: VIVE CON: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h17"> VIVE CON: </h6>
    <label><input type="checkbox" id="h17_op1"> SOLA</label>
    <label><input type="checkbox" id="h17_op2"> MADRE</label>
    <label><input type="checkbox" id="h17_op3"> PADRE</label>
    <label><input type="checkbox" id="h17_op4"> ABUELA</label>
    <label><input type="checkbox" id="h17_op5"> <input type="text"></label>
  </div>

  <!-- header 18: EDAD DEL PADRE: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h18"> EDAD DEL PADRE: </h6>
    <label><input type="checkbox" id="h18_op1"> NO BRINDA INFORMACION</label>
    <label><input type="checkbox" id="h18_op2"> <input type="text"></label>
  </div>

  <!-- header 19: ESCOLARIDAD DEL PADRE:  / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h19"> ESCOLARIDAD DEL PADRE:  </h6>
    <label><input type="checkbox" id="h19_op1"> NO BRINDA INFORMACION</label>
    <label><input type="checkbox" id="h19_op2"> BACHILLER</label>
    <label><input type="checkbox" id="h19_op3"> PREGRADO</label>
    <label><input type="checkbox" id="h19_op4"> TECNOLOGO</label>
  </div>

  <!-- header 20: PRIMIPATERNIDAD: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h20"> PRIMIPATERNIDAD: </h6>
    <label><input type="checkbox" id="h20_op1"> SI</label>
    <label><input type="checkbox" id="h20_op2"> NO</label>
  </div>

  <!-- header 21: HEMOCLASIFICACION PATERNA: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h21"> HEMOCLASIFICACION PATERNA: </h6>
    <label><input type="checkbox" id="h21_op1"> NO BRINDA INFORMACION</label>
    <label><input type="checkbox" id="h21_op2"> O+</label>
    <label><input type="checkbox" id="h21_op3"> O-</label>
    <label><input type="checkbox" id="h21_op4"> A+</label>
    <label><input type="checkbox" id="h21_op5"> A-</label>
    <label><input type="checkbox" id="h21_op6"> B+</label>
    <label><input type="checkbox" id="h21_op7"> B-</label>
    <label><input type="checkbox" id="h21_op8"> AB+</label>
    <label><input type="checkbox" id="h21_op9"> AB-</label>
  </div>

  <!-- header 22: REVISIÓN POR SISTEMAS: NIEGA / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h22"> REVISIÓN POR SISTEMAS: NIEGA </h6>
    <label><input type="checkbox" id="h22_op1"> DOLOR ABDOMINAL PROGRESIVO</label>
    <label><input type="checkbox" id="h22_op2"> DOLOR ABDOMINAL PERSISTENTE</label>
    <label><input type="checkbox" id="h22_op3"> DOLOR ABDOMINAL LOCALIZADO EN CUADRANTE SUPERIOR DERECHO</label>
    <label><input type="checkbox" id="h22_op4"> METRORRAGIA </label>
    <label><input type="checkbox" id="h22_op5"> SÍNTOMATOLOGIA URINARIA</label>
    <label><input type="checkbox" id="h22_op6"> NIEGA  LEUCORREA</label>
  </div>

  <!-- header 22: ANTECEDENTES GINECOLÓGICOS: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h22"> ANTECEDENTES GINECOLÓGICOS: </h6>
  </div>

  <!-- header 23: G**P**C**V** / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h23"> G<input type="text">P<input type="text">C<input type="text">V<input type="text"> </h6>
  </div>

  <!-- header 24: CONTROLES PRENATALES: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h24"> CONTROLES PRENATALES: </h6>
  </div>

  <!-- header 25: CICLOS: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h25"> CICLOS: </h6>
    <label><input type="checkbox" id="h25_op1"> REGULARES</label>
    <label><input type="checkbox" id="h25_op2"> IRREGULARES</label>
  </div>

  <!-- header 26: FUM: ** / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h26"> FUM: <input type="text"> </h6>
  </div>

  <!-- header 27: MENARQUIA: ** AÑOS / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h27"> MENARQUIA: <input type="text"> AÑOS </h6>
  </div>

  <!-- header 28: SEXARQUIA: ** AÑOS / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h28"> SEXARQUIA: <input type="text"> AÑOS </h6>
  </div>

  <!-- header 29: PAREJAS SEXUALES: ** / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h29"> PAREJAS SEXUALES: <input type="text"> </h6>
  </div>

  <!-- header 30: ETS: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h30"> ETS: </h6>
    <label><input type="checkbox" id="h30_op1"> NO</label>
    <label><input type="checkbox" id="h30_op2"> VIH</label>
    <label><input type="checkbox" id="h30_op3"> SIFILIS</label>
    <label><input type="checkbox" id="h30_op4"> GONORREA</label>
  </div>

  <!-- header 31: CITOLOGÍA: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h31"> CITOLOGÍA: </h6>
    <label><input type="checkbox" id="h31_op1"> SI HACE <input type="text"> AÑOS</label>
    <label><input type="checkbox" id="h31_op2"> NO</label>
  </div>

  <!-- header 32: VACUNACIÓN: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h32"> VACUNACIÓN: </h6>
    <label><input type="checkbox" id="h32_op1"> COMPLETA</label>
    <label><input type="checkbox" id="h32_op2"> INCOMPLETA</label>
    <label><input type="checkbox" id="h32_op3"> NO ESTA SEGURA DE CUALES VACUNAS SE LE HAN APLICADO</label>
  </div>

  <!-- header 33: MICRONUTRIENTES: // -->
  <div class="grupo" data-slashes="2">
    <h6 class="h33"> MICRONUTRIENTES: </h6>
    <label><input type="checkbox" id="h33_op1"> CALCIO</label>
    <label><input type="checkbox" id="h33_op2"> ÁCIDO FÓLICO</label>
    <label><input type="checkbox" id="h33_op3"> HIERRO</label>
    <label><input type="checkbox" id="h33_op4"> GESTAVIT</label>
  </div>

  <!-- header 34: TAMIZAJE DEPRESIÓN POSTPARTO/ -->
  <div class="grupo" data-slashes="1">
    <h6 class="h34"> TAMIZAJE DEPRESIÓN POSTPARTO</h6>
    <label><input type="checkbox" id="h34_op1"> SI</label>
    <label><input type="checkbox" id="h34_op2"> NO</label>
  </div>

  <!-- header 35 ... / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h35"> DURANTE EL MES PASADO, ¿CON FRECUENCIA SE HA SENTIDO TRISTE, DEPRIMIDA O SIN ESPERANZA?</h6>
    <label><input type="checkbox" id="h35_op1"> SI</label>
    <label><input type="checkbox" id="h35_op2"> NO</label>
  </div>

  <!-- header 36 ... / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h36"> DURANTE EL MES PASADO, ¿HA PERMANECIDO PREOCUPADA POR TENER POCO INTERÉS O PLACER PARA HACER LAS COSAS COTIDIANAS?</h6>
    <label><input type="checkbox" id="h36_op1"> SI</label>
    <label><input type="checkbox" id="h36_op2"> NO</label>
  </div>

  <!-- header 37 ... / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h37"> TAMIZAJE DE VIOLENCIA</h6>
    <label><input type="checkbox" id="h37_op1"> SI</label>
    <label><input type="checkbox" id="h37_op2"> NO</label>
  </div>

  <!-- header 38 ... / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h38"> ¿DURANTE EL ÚLTIMO AÑO, HA SIDO HUMILLADA, MENOSPRECIADA, INSULTADA O AMENAZADA POR SU PAREJA?</h6>
    <label><input type="checkbox" id="h38_op1"> SI</label>
    <label><input type="checkbox" id="h38_op2"> NO</label>
  </div>

  <!-- header 39 ... / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h39"> ¿DURANTE EL ÚLTIMO AÑO, FUE GOLPEADA, BOFETEADA, PATEADA, O LASTIMADA FÍSICAMENTE DE OTRA MANERA?</h6>
    <label><input type="checkbox" id="h39_op1"> SI</label>
    <label><input type="checkbox" id="h39_op2"> NO</label>
  </div>

  <!-- header 40 ... / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h40"> ¿DESDE QUE ESTÁ EN GESTACIÓN, HA SIDO GOLPEADA, BOFETEADA, PATEADA, O LASTIMADA FÍSICAMENTE DE ALGUNA MANERA?</h6>
    <label><input type="checkbox" id="h40_op1"> SI</label>
    <label><input type="checkbox" id="h40_op2"> NO</label>
  </div>

  <!-- header 41 ... / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h41"> ¿DURANTE EL ÚLTIMO AÑO, FUE FORZADA A TENER RELACIONES SEXUALES?</h6>
    <label><input type="checkbox" id="h41_op1"> SI</label>
    <label><input type="checkbox" id="h41_op2"> NO</label>
  </div>

  <!-- header 42: VALORACIÓN POR PSICOLOGÍA: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h42"> VALORACIÓN POR PSICOLOGÍA: </h6>
    <label><input type="checkbox" id="h42_op1"> SI</label>
    <label><input type="checkbox" id="h42_op2"> NO</label>
  </div>

  <!-- header 43: VALORACIÓN POR ODONTOLOGÍA: / -->
  <div class="grupo" data-slashes="1">
    <h6 class="h43"> VALORACIÓN POR ODONTOLOGÍA: </h6>
    <label><input type="checkbox" id="h43_op1"> SI</label>
    <label><input type="checkbox" id="h43_op2"> NO</label>
  </div>

  <!-- header 44: VALORACIÓN POR NUTRICIÓN: // -->
  <div class="grupo" data-slashes="2">
    <h6 class="h44"> VALORACIÓN POR NUTRICIÓN: </h6>
    <label><input type="checkbox" id="h44_op1"> SI</label>
    <label><input type="checkbox" id="h44_op2"> NO</label>
  </div>

  <!-- header 44:  PARACLINICOS (sin slash) -->
  <div class="grupo" data-slashes="0">
    <h6 class="h44">  PARACLINICOS</h6>
    <label><input type="checkbox" id="h44_op3"> UROCULTIVO: <input type="text"></label>
    <label><input type="checkbox" id="h44_op4"> GLUCOSA 1 HORA POSTCARGA: <input type="text"> GLUCOSA 2 HORAS POST CARGA:<input type="text"></label>
    <label><input type="checkbox" id="h44_op5"> HEMOGRAMA: HEMOGLOBINA: <input type="text"> G/DL HEMATOCRITO: <input type="text"> % VCM: <input type="text"> FL HCM: <input type="text"> PG LEUCOCITOS: <input type="text"> NEUTROFILOS: <input type="text">%LINFOCITOS: <input type="text">%MONOCITOS: <input type="text">% EOSINOFILOS: <input type="text">% PLAQUETAS: <input type="text"></label>
    <label><input type="checkbox" id="h44_op6"> VIH: <input type="text"></label>
    <label><input type="checkbox" id="h44_op7"> AGSHB: <input type="text"></label>
    <label><input type="checkbox" id="h44_op8"> TREPONEMA: <input type="text"></label>
    <label><input type="checkbox" id="h44_op9"> TOXOPLASMA IGG: <input type="text"></label>
    <label><input type="checkbox" id="h44_op10"> TOXOPLASMA IGM: <input type="text"></label>
    <label><input type="checkbox" id="h44_op11"> UROANALISIS <input type="text"></label>
    <label><input type="checkbox" id="h44_op12"> RUBEOLA IGG: <input type="text"></label>
    <label><input type="checkbox" id="h44_op13"> RUBEOLA IGM: <input type="text"></label>
    <label><input type="checkbox" id="h44_op14"> TSH: <input type="text"> mU/L</label>
  </div>

  <!-- header 45: ECOGRAFIAS (sin slash) -->
  <div class="grupo" data-slashes="0">
    <h6 class="h45"> ECOGRAFIAS</h6>
    <label><input type="checkbox" id="h45_op1"> NO APORTA CARPETA DE CONTROLES PRENATALES SIN EMBARGO MANIFIESTA ECOGRAFIAS SIN EVENTUALIDADES</label>
    <label><input type="checkbox" id="h45_op2"> <input type="text">-<input type="text">-<input type="text"> ECO TN : EMBARAZO DE <input type="text"> SEMANAS , TN NORMAL , HOY : 25.1 SEMANAS</label>
    <label><input type="checkbox" id="h45_op3"> <input type="text">-<input type="text">-<input type="text"> ECOGRAFIA DETALLE ANATOMICO EMBARAZO DE <input type="text"> SEMANAS BEIENES FETAL PERFIL DE CRECIMEINTO FETAL NORMAL, NO SE DETECTARON MALFORMACIONES MAYORES, PESO FETAL <input type="text"> GR PERCENTIL <input type="text"></label>
  </div>

  <button onclick="updateNarrativa()">Generar Narrativa</button>
  <p id="resultado"></p>

  <script>
    // Conexiones (si en el futuro agregas data-link)
    document.querySelectorAll("input[type='checkbox'][data-link]").forEach(cb => {
      cb.addEventListener("change", function () {
        const target = document.getElementById(this.dataset.link);
        if (target) target.checked = this.checked;
      });
    });

    function readTextWithInputs(root, { ignoreCheckboxes } = { ignoreCheckboxes: true }) {
      let out = "";
      const walker = document.createTreeWalker(root, NodeFilter.SHOW_ELEMENT | NodeFilter.SHOW_TEXT, null);

      function appendText(t) { out += t; }

      let node = walker.currentNode;
      // TreeWalker inicia en root; procesamos root y luego avanzamos
      while (node) {
        if (node.nodeType === Node.TEXT_NODE) {
          appendText(node.textContent);
        } else if (node.nodeType === Node.ELEMENT_NODE) {
          const el = node;
          const tag = el.tagName.toLowerCase();

          if (tag === "input") {
            const type = (el.getAttribute("type") || "").toLowerCase();
            if (type === "text") appendText(el.value || "");
            if (type === "checkbox" && ignoreCheckboxes) { /* ignorar */ }
          }
        }
        node = walker.nextNode();
      }

      // Limpieza mínima: elimina saltos/indent del HTML, conserva espacios naturales
      return out.replace(/\s+/g, " ").trim();
    }

    function updateNarrativa() {
      const checks = document.querySelectorAll("input[type=checkbox]"); // (debe existir EXACTAMENTE)

      let narrativa = "";

      document.querySelectorAll(".grupo").forEach(grupo => {
        const slashCount = parseInt(grupo.getAttribute("data-slashes") || "0", 10);

        const headerEl = grupo.querySelector("h1,h2,h3,h4,h5,h6");
        const headerText = headerEl ? readTextWithInputs(headerEl, { ignoreCheckboxes: true }) : "";

        // ¿Aporta por inputs del header?
        const headerHasText = headerEl
          ? Array.from(headerEl.querySelectorAll('input[type="text"]')).some(inp => (inp.value || "").trim() !== "")
          : false;

        // Opciones marcadas (en orden)
        let opcionesText = "";
        const labels = Array.from(grupo.querySelectorAll("label"));
        let anyChecked = false;

        labels.forEach(label => {
          const cb = label.querySelector('input[type="checkbox"]');
          if (cb && cb.checked) {
            anyChecked = true;
            // Clonar para excluir el checkbox del texto, pero conservar inputs text y resto del label
            const clone = label.cloneNode(true);
            const cb2 = clone.querySelector('input[type="checkbox"]');
            if (cb2) cb2.remove();
            const t = readTextWithInputs(clone, { ignoreCheckboxes: true });
            if (t) opcionesText += t + " ";
          }
        });

        const aporta = anyChecked || headerHasText;

        if (aporta) {
          if (headerText) narrativa += headerText + " ";
          if (opcionesText.trim() !== "") narrativa += opcionesText.trim() + " ";

          for (let k = 0; k < slashCount; k++) narrativa += "\n\n";
        }
      });

      document.getElementById("resultado").innerHTML =
        narrativa.trim().replace(/\n/g, "<br>");
    }
  </script>

</body>
</html>
