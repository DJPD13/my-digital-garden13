---
{"dg-publish":true,"permalink":"/digital-garden/1-ea-13/maternas/","dgPassFrontmatter":true}
---

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Narrativa Dinámica</title>
  <style>
    body { font-family: Arial, sans-serif; }
    .opcion { display: block; margin: 6px 0; }
    .inline-input { margin: 0 6px; }
    #resultado { margin-top: 14px; padding: 10px; border: 1px solid #ccc; }
  </style>
</head>
<body>

  <!-- header 1: MC: " ** " / -->
  <h1>
    MC: "
    <input class="inline-input" type="text" id="inp_h1_1" />
    "
  </h1>

  <!-- header 2: FORMULA OBSTÉTRICA: G**P** / -->
  <h2>
    FORMULA OBSTÉTRICA: G
    <input class="inline-input" type="text" id="inp_h2_1" />
    P
    <input class="inline-input" type="text" id="inp_h2_2" />
  </h2>

  <!-- header 3: FECHA ÚLTIMO PARTO:  **-**-** / -->
  <h3>
    FECHA ÚLTIMO PARTO:
    <input class="inline-input" type="text" id="inp_h3_1" />-
    <input class="inline-input" type="text" id="inp_h3_2" />-
    <input class="inline-input" type="text" id="inp_h3_3" />
  </h3>

  <!-- header 4: FECHA DE ULTIMA REGLA: **-**-** / -->
  <h4>
    FECHA DE ULTIMA REGLA:
    <input class="inline-input" type="text" id="inp_h4_1" />-
    <input class="inline-input" type="text" id="inp_h4_2" />-
    <input class="inline-input" type="text" id="inp_h4_3" />
  </h4>

  <!-- header 5: HEMOCLASIFICACIÓN: / -->
  <h5>HEMOCLASIFICACIÓN:</h5>
  <label class="opcion"><input type="checkbox" id="h5_op1"> O+</label>
  <label class="opcion"><input type="checkbox" id="h5_op2"> O-</label>
  <label class="opcion"><input type="checkbox" id="h5_op3"> A+</label>
  <label class="opcion"><input type="checkbox" id="h5_op4"> A-</label>
  <label class="opcion"><input type="checkbox" id="h5_op5"> AB+</label>
  <label class="opcion"><input type="checkbox" id="h5_op6"> AB-</label>

  <!-- header 6: CONSULTA PRECONCEPCIONAL:/ -->
  <h6>CONSULTA PRECONCEPCIONAL:</h6>

  <!-- header 7: PLANIFICACIÓN PRECONCEPCIONAL: / -->
  <h7>PLANIFICACIÓN PRECONCEPCIONAL:</h7>
  <label class="opcion"><input type="checkbox" id="h7_op1"> POMEROY</label>
  <label class="opcion"><input type="checkbox" id="h7_op2"> INYECCIÓN MENSUAL</label>
  <label class="opcion"><input type="checkbox" id="h7_op3"> INYECCIÓN TRIMESTRAL</label>
  <label class="opcion"><input type="checkbox" id="h7_op4"> ANTICONCEPTIVOS ORALES</label>
  <label class="opcion"><input type="checkbox" id="h7_op5"> IMPLANTE SUBDERMICO</label>
  <label class="opcion"><input type="checkbox" id="h7_op6"> NO PLANIFICABA ANTERIORMENTE</label>

  <!-- header 8: CONTROLES PRENATALES: / -->
  <h8>CONTROLES PRENATALES:</h8>
  <label class="opcion">
    <input type="checkbox" id="h8_op1">
    <input class="inline-input" type="text" id="inp_h8_op1" />
    <span> (APORTA HISTORIA CLINICA)</span>
  </label>
  <label class="opcion">
    <input type="checkbox" id="h8_op2">
    <input class="inline-input" type="text" id="inp_h8_op2" />
    <span> (NO APORTA HISTORIA CLINICA)</span>
  </label>
  <label class="opcion"><input type="checkbox" id="h8_op3"> NO RECUERDA (NO AMPORTA HISTORIA CLINICA)</label>

  <!-- header 9: EMBARAZO: / -->
  <h9>EMBARAZO:</h9>
  <label class="opcion"><input type="checkbox" id="h9_op1"> PLANEADO Y ACEPTADO</label>
  <label class="opcion"><input type="checkbox" id="h9_op2"> NO PLANEADO Y ACEPTADO</label>

  <!-- header 10: PLAN DE PLANIFICACIÓN POSTPARTO: / -->
  <h10>PLAN DE PLANIFICACIÓN POSTPARTO:</h10>
  <label class="opcion"><input type="checkbox" id="h10_op1"> POMEROY</label>
  <label class="opcion"><input type="checkbox" id="h10_op2"> INYECCIÓN MENSUAL</label>
  <label class="opcion"><input type="checkbox" id="h10_op3"> INYECCIÓN TRIMESTRAL</label>
  <label class="opcion"><input type="checkbox" id="h10_op4"> ANTICONCEPTIVOS ORALES</label>
  <label class="opcion"><input type="checkbox" id="h10_op5"> IMPLANTE SUBDERMICO</label>
  <label class="opcion"><input type="checkbox" id="h10_op6"> NO DESEA</label>

  <button onclick="updateNarrativa()">Generar Narrativa</button>
  <p id="resultado"></p>

  <script>
    // Conexiones (si existieran): origen con data-link="idDestino"
    document.querySelectorAll("input[type='checkbox'][data-link]").forEach(cb => {
      cb.addEventListener("change", function () {
        const target = document.getElementById(this.dataset.link);
        if (target) target.checked = this.checked;
      });
    });

    function updateNarrativa() {
      const checks = document.querySelectorAll("input[type=checkbox]");
      let narrativa = "";

      // header 1: MC: " ** "  /
      {
        let bloque = "";
        const v1 = (document.getElementById("inp_h1_1").value || "").trim();
        if (v1 !== "") {
          bloque += 'MC: " ' + v1 + ' " ';
          narrativa += bloque.trim() + "\n\n";
        }
      }

      // header 2: FORMULA OBSTÉTRICA: G**P**  /
      {
        let bloque = "";
        const v1 = (document.getElementById("inp_h2_1").value || "").trim();
        const v2 = (document.getElementById("inp_h2_2").value || "").trim();
        if (v1 !== "" || v2 !== "") {
          bloque += "FORMULA OBSTÉTRICA: G ";
          if (v1 !== "") bloque += v1 + " ";
          bloque += "P ";
          if (v2 !== "") bloque += v2 + " ";
          narrativa += bloque.trim() + "\n\n";
        }
      }

      // header 3: FECHA ÚLTIMO PARTO:  **-**-**  /
      {
        let bloque = "";
        const v1 = (document.getElementById("inp_h3_1").value || "").trim();
        const v2 = (document.getElementById("inp_h3_2").value || "").trim();
        const v3 = (document.getElementById("inp_h3_3").value || "").trim();
        if (v1 !== "" || v2 !== "" || v3 !== "") {
          bloque += "FECHA ÚLTIMO PARTO: ";
          if (v1 !== "") bloque += v1;
          bloque += "-";
          if (v2 !== "") bloque += v2;
          bloque += "-";
          if (v3 !== "") bloque += v3;
          bloque += " ";
          narrativa += bloque.trim() + "\n\n";
        }
      }

      // header 4: FECHA DE ULTIMA REGLA: **-**-**  /
      {
        let bloque = "";
        const v1 = (document.getElementById("inp_h4_1").value || "").trim();
        const v2 = (document.getElementById("inp_h4_2").value || "").trim();
        const v3 = (document.getElementById("inp_h4_3").value || "").trim();
        if (v1 !== "" || v2 !== "" || v3 !== "") {
          bloque += "FECHA DE ULTIMA REGLA: ";
          if (v1 !== "") bloque += v1;
          bloque += "-";
          if (v2 !== "") bloque += v2;
          bloque += "-";
          if (v3 !== "") bloque += v3;
          bloque += " ";
          narrativa += bloque.trim() + "\n\n";
        }
      }

      // header 5: HEMOCLASIFICACIÓN:  /
      {
        let bloque = "";
        if (checks[0].checked || checks[1].checked || checks[2].checked || checks[3].checked || checks[4].checked || checks[5].checked) {
          bloque += "HEMOCLASIFICACIÓN: ";
          if (checks[0].checked) bloque += "O+ ";
          if (checks[1].checked) bloque += "O- ";
          if (checks[2].checked) bloque += "A+ ";
          if (checks[3].checked) bloque += "A- ";
          if (checks[4].checked) bloque += "AB+ ";
          if (checks[5].checked) bloque += "AB- ";
          narrativa += bloque.trim() + "\n\n";
        }
      }

      // header 6: CONSULTA PRECONCEPCIONAL: /
      // (sin opciones ni ** en tu ejemplo, así que no aporta texto automáticamente)

      // header 7: PLANIFICACIÓN PRECONCEPCIONAL:  /
      {
        let bloque = "";
        if (
          checks[6].checked || checks[7].checked || checks[8].checked ||
          checks[9].checked || checks[10].checked || checks[11].checked
        ) {
          bloque += "PLANIFICACIÓN PRECONCEPCIONAL: ";
          if (checks[6].checked) bloque += "POMEROY ";
          if (checks[7].checked) bloque += "INYECCIÓN MENSUAL ";
          if (checks[8].checked) bloque += "INYECCIÓN TRIMESTRAL ";
          if (checks[9].checked) bloque += "ANTICONCEPTIVOS ORALES ";
          if (checks[10].checked) bloque += "IMPLANTE SUBDERMICO ";
          if (checks[11].checked) bloque += "NO PLANIFICABA ANTERIORMENTE ";
          narrativa += bloque.trim() + "\n\n";
        }
      }

      // header 8: CONTROLES PRENATALES:  /
      {
        let bloque = "";
        if (checks[12].checked || checks[13].checked || checks[14].checked) {
          bloque += "CONTROLES PRENATALES: ";

          // ** (APORTA HISTORIA CLINICA)
          if (checks[12].checked) {
            const v = (document.getElementById("inp_h8_op1").value || "").trim();
            if (v !== "") bloque += v + " ";
            bloque += "(APORTA HISTORIA CLINICA) ";
          }

          // ** (NO APORTA HISTORIA CLINICA)
          if (checks[13].checked) {
            const v = (document.getElementById("inp_h8_op2").value || "").trim();
            if (v !== "") bloque += v + " ";
            bloque += "(NO APORTA HISTORIA CLINICA) ";
          }

          if (checks[14].checked) bloque += "NO RECUERDA (NO AMPORTA HISTORIA CLINICA) ";

          narrativa += bloque.trim() + "\n\n";
        }
      }

      // header 9: EMBARAZO:  /
      {
        let bloque = "";
        if (checks[15].checked || checks[16].checked) {
          bloque += "EMBARAZO: ";
          if (checks[15].checked) bloque += "PLANEADO Y ACEPTADO ";
          if (checks[16].checked) bloque += "NO PLANEADO Y ACEPTADO ";
          narrativa += bloque.trim() + "\n\n";
        }
      }

      // header 10: PLAN DE PLANIFICACIÓN POSTPARTO:  /
      {
        let bloque = "";
        if (
          checks[17].checked || checks[18].checked || checks[19].checked ||
          checks[20].checked || checks[21].checked || checks[22].checked
        ) {
          bloque += "PLAN DE PLANIFICACIÓN POSTPARTO: ";
          if (checks[17].checked) bloque += "POMEROY ";
          if (checks[18].checked) bloque += "INYECCIÓN MENSUAL ";
          if (checks[19].checked) bloque += "INYECCIÓN TRIMESTRAL ";
          if (checks[20].checked) bloque += "ANTICONCEPTIVOS ORALES ";
          if (checks[21].checked) bloque += "IMPLANTE SUBDERMICO ";
          if (checks[22].checked) bloque += "NO DESEA ";
          narrativa += bloque.trim() + "\n\n";
        }
      }

      document.getElementById("resultado").innerHTML = narrativa.trim().replace(/\n/g, "<br>");
    }
  </script>

</body>
</html>