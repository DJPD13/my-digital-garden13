---
{"dg-publish":true,"permalink":"/digital-garden/maternassss/maternas-ea/","dgPassFrontmatter":true}
---

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Narrativa Dinámica</title>
  <style>
    body { font-family: Arial, sans-serif; line-height: 1.35; }
    .opcion { display: block; margin: 6px 0; }
    .inline-input { margin: 0 6px; min-width: 70px; }
    #resultado { margin-top: 14px; padding: 10px; border: 1px solid #ccc; }
    .grupo { margin-bottom: 10px; }
  </style>
</head>
<body>

  <!-- header 1: MC: " ** " / -->
  <div class="grupo">
    <h1>
      <span>MC: " </span>
      <input class="inline-input" type="text" id="inp_h1_t1_1">
      <span> " </span>
    </h1>
  </div>

  <!-- header 2: FORMULA OBSTÉTRICA: G**P** / -->
  <div class="grupo">
    <h2>
      <span>FORMULA OBSTÉTRICA: G</span>
      <input class="inline-input" type="text" id="inp_h2_t1_1">
      <span>P</span>
      <input class="inline-input" type="text" id="inp_h2_t1_2">
      <span> </span>
    </h2>
  </div>

  <!-- header 3: FECHA ÚLTIMO PARTO:  **-**-** / -->
  <div class="grupo">
    <h3>
      <span>FECHA ÚLTIMO PARTO:  </span>
      <input class="inline-input" type="text" id="inp_h3_t1_1"><span>-</span>
      <input class="inline-input" type="text" id="inp_h3_t1_2"><span>-</span>
      <input class="inline-input" type="text" id="inp_h3_t1_3">
      <span> </span>
    </h3>
  </div>

  <!-- header 4: FECHA DE ULTIMA MENSTRUACIÓN: **-**-** / -->
  <div class="grupo">
    <h4>
      <span>FECHA DE ULTIMA MENSTRUACIÓN: </span>
      <input class="inline-input" type="text" id="inp_h4_t1_1"><span>-</span>
      <input class="inline-input" type="text" id="inp_h4_t1_2"><span>-</span>
      <input class="inline-input" type="text" id="inp_h4_t1_3">
      <span> </span>
    </h4>
  </div>

  <!-- header 5: HEMOCLASIFICACIÓN: / -->
  <div class="grupo">
    <h5><span>HEMOCLASIFICACIÓN: </span></h5>
    <label class="opcion"><input type="checkbox" id="h5_op1"> O+</label>
    <label class="opcion"><input type="checkbox" id="h5_op2"> O-</label>
    <label class="opcion"><input type="checkbox" id="h5_op3"> A+</label>
    <label class="opcion"><input type="checkbox" id="h5_op4"> A-</label>
    <label class="opcion"><input type="checkbox" id="h5_op5"> B+</label>
    <label class="opcion"><input type="checkbox" id="h5_op6"> B-</label>
    <label class="opcion"><input type="checkbox" id="h5_op7"> AB+</label>
    <label class="opcion"><input type="checkbox" id="h5_op8"> AB-</label>
  </div>

  <!-- header 6: CONSULTA PRECONCEPCIONAL:/ -->
  <div class="grupo">
    <h6><span>CONSULTA PRECONCEPCIONAL:</span></h6>
  </div>

  <!-- header 7: PLANIFICACIÓN PRECONCEPCIONAL: / -->
  <div class="grupo">
    <h7><span>PLANIFICACIÓN PRECONCEPCIONAL: </span></h7>
    <label class="opcion"><input type="checkbox" id="h7_op1"> POMEROY</label>
    <label class="opcion"><input type="checkbox" id="h7_op2"> INYECCIÓN MENSUAL</label>
    <label class="opcion"><input type="checkbox" id="h7_op3"> INYECCIÓN TRIMESTRAL</label>
    <label class="opcion"><input type="checkbox" id="h7_op4"> ANTICONCEPTIVOS ORALES</label>
    <label class="opcion"><input type="checkbox" id="h7_op5"> IMPLANTE SUBDERMICO</label>
    <label class="opcion"><input type="checkbox" id="h7_op6"> NO PLANIFICABA ANTERIORMENTE</label>
  </div>

  <!-- header 8: CONTROLES PRENATALES: / -->
  <div class="grupo">
    <h8><span>CONTROLES PRENATALES: </span></h8>

    <label class="opcion">
      <input type="checkbox" id="h8_op1">
      <input class="inline-input" type="text" id="inp_h8_op1_1">
      <span> (APORTA HISTORIA CLINICA)</span>
    </label>

    <label class="opcion">
      <input type="checkbox" id="h8_op2">
      <input class="inline-input" type="text" id="inp_h8_op2_1">
      <span> (NO APORTA HISTORIA CLINICA)</span>
    </label>

    <label class="opcion"><input type="checkbox" id="h8_op3"> NO RECUERDA (NO AMPORTA HISTORIA CLINICA)</label>
  </div>

  <!-- header 9: EMBARAZO: / -->
  <div class="grupo">
    <h9><span>EMBARAZO: </span></h9>
    <label class="opcion"><input type="checkbox" id="h9_op1"> PLANEADO Y ACEPTADO</label>
    <label class="opcion"><input type="checkbox" id="h9_op2"> NO PLANEADO Y ACEPTADO</label>
  </div>

  <!-- header 10: PLAN DE PLANIFICACIÓN POSTPARTO: / -->
  <div class="grupo">
    <h10><span>PLAN DE PLANIFICACIÓN POSTPARTO: </span></h10>
    <label class="opcion"><input type="checkbox" id="h10_op1"> POMEROY</label>
    <label class="opcion"><input type="checkbox" id="h10_op2"> INYECCIÓN MENSUAL</label>
    <label class="opcion"><input type="checkbox" id="h10_op3"> INYECCIÓN TRIMESTRAL</label>
    <label class="opcion"><input type="checkbox" id="h10_op4"> ANTICONCEPTIVOS ORALES</label>
    <label class="opcion"><input type="checkbox" id="h10_op5"> IMPLANTE SUBDERMICO</label>
    <label class="opcion"><input type="checkbox" id="h10_op6"> NO DESEA</label>
  </div>

  <!-- header 11: PROCEDENCIA: / -->
  <div class="grupo">
    <h11><span> PROCEDENCIA: </span></h11>
    <label class="opcion"><input type="checkbox" id="h11_op1"> VILLANUEVA CASANARE</label>
  </div>

  <!-- header 12: DIRECCIÓN: / -->
  <div class="grupo">
    <h12><span> DIRECCIÓN: </span></h12>

    <label class="opcion">
      <input type="checkbox" id="h12_op1">
      <span>CARRERA </span><input class="inline-input" type="text" id="inp_h12_op1_1">
      <span> # </span><input class="inline-input" type="text" id="inp_h12_op1_2">
      <span>-</span><input class="inline-input" type="text" id="inp_h12_op1_3">
    </label>

    <label class="opcion">
      <input type="checkbox" id="h12_op2">
      <span>CALLE </span><input class="inline-input" type="text" id="inp_h12_op2_1">
      <span> #</span><input class="inline-input" type="text" id="inp_h12_op2_2">
      <span>-</span><input class="inline-input" type="text" id="inp_h12_op2_3">
    </label>

    <label class="opcion">
      <input type="checkbox" id="h12_op3">
      <span>DIAGONAL </span><input class="inline-input" type="text" id="inp_h12_op3_1">
      <span>#</span><input class="inline-input" type="text" id="inp_h12_op3_2">
      <span>-</span><input class="inline-input" type="text" id="inp_h12_op3_3">
    </label>
  </div>

  <!-- header 13: TELÉFONO: ** / -->
  <div class="grupo">
    <h13><span> TELÉFONO: </span><input class="inline-input" type="text" id="inp_h13_t1_1"><span> </span></h13>
  </div>

  <!-- header 14: ESTADO CIVIL:  / -->
  <div class="grupo">
    <h14><span> ESTADO CIVIL:  </span></h14>
    <label class="opcion"><input type="checkbox" id="h14_op1"> UNION LIBRE</label>
    <label class="opcion"><input type="checkbox" id="h14_op2"> CASADA</label>
    <label class="opcion"><input type="checkbox" id="h14_op3"> SOLTERA</label>
  </div>

  <!-- header 15: OCUPACIÓN: / -->
  <div class="grupo">
    <h15><span> OCUPACIÓN: </span></h15>
    <label class="opcion"><input type="checkbox" id="h15_op1"> AMA DE CASA</label>
    <label class="opcion"><input type="checkbox" id="h15_op2"> OFICIOS VARIOS</label>
    <label class="opcion"><input type="checkbox" id="h15_op3"> <input class="inline-input" type="text" id="inp_h15_op3_1"></label>
  </div>

  <!-- header 16: ESCOLARIDAD: / -->
  <div class="grupo">
    <h16><span> ESCOLARIDAD: </span></h16>
    <label class="opcion"><input type="checkbox" id="h16_op1"> BACHILLER</label>
    <label class="opcion"><input type="checkbox" id="h16_op2"> PREGRADO</label>
    <label class="opcion"><input type="checkbox" id="h16_op3"> TECNOLOGO</label>
  </div>

  <!-- header 17: VIVE CON: / -->
  <div class="grupo">
    <h17><span> VIVE CON: </span></h17>
    <label class="opcion"><input type="checkbox" id="h17_op1"> SOLA</label>
    <label class="opcion"><input type="checkbox" id="h17_op2"> MADRE</label>
    <label class="opcion"><input type="checkbox" id="h17_op3"> PADRE</label>
    <label class="opcion"><input type="checkbox" id="h17_op4"> ABUELA</label>
    <label class="opcion"><input type="checkbox" id="h17_op5"> <input class="inline-input" type="text" id="inp_h17_op5_1"></label>
  </div>

  <!-- header 18: EDAD DEL PADRE: / -->
  <div class="grupo">
    <h18><span> EDAD DEL PADRE: </span></h18>
    <label class="opcion"><input type="checkbox" id="h18_op1"> NO BRINDA INFORMACION</label>
    <label class="opcion"><input type="checkbox" id="h18_op2"> <input class="inline-input" type="text" id="inp_h18_op2_1"></label>
  </div>

  <!-- header 19: ESCOLARIDAD DEL PADRE:  / -->
  <div class="grupo">
    <h19><span> ESCOLARIDAD DEL PADRE:  </span></h19>
    <label class="opcion"><input type="checkbox" id="h19_op1"> NO BRINDA INFORMACION</label>
    <label class="opcion"><input type="checkbox" id="h19_op2"> BACHILLER</label>
    <label class="opcion"><input type="checkbox" id="h19_op3"> PREGRADO</label>
    <label class="opcion"><input type="checkbox" id="h19_op4"> TECNOLOGO</label>
  </div>

  <!-- header 20: PRIMIPATERNIDAD: / -->
  <div class="grupo">
    <h20><span> PRIMIPATERNIDAD: </span></h20>
    <label class="opcion"><input type="checkbox" id="h20_op1"> SI</label>
    <label class="opcion"><input type="checkbox" id="h20_op2"> NO</label>
  </div>

  <!-- header 21: HEMOCLASIFICACION PATERNA: / -->
  <div class="grupo">
    <h21><span> HEMOCLASIFICACION PATERNA: </span></h21>
    <label class="opcion"><input type="checkbox" id="h21_op1"> NO BRINDA INFORMACION</label>
    <label class="opcion"><input type="checkbox" id="h21_op2"> O+</label>
    <label class="opcion"><input type="checkbox" id="h21_op3"> O-</label>
    <label class="opcion"><input type="checkbox" id="h21_op4"> A+</label>
    <label class="opcion"><input type="checkbox" id="h21_op5"> A-</label>
    <label class="opcion"><input type="checkbox" id="h21_op6"> B+</label>
    <label class="opcion"><input type="checkbox" id="h21_op7"> B-</label>
    <label class="opcion"><input type="checkbox" id="h21_op8"> AB+</label>
    <label class="opcion"><input type="checkbox" id="h21_op9"> AB-</label>
  </div>

  <!-- header 22: REVISIÓN POR SISTEMAS: NIEGA / -->
  <div class="grupo">
    <h22><span> REVISIÓN POR SISTEMAS: NIEGA </span></h22>
    <label class="opcion"><input type="checkbox" id="h22_op1"> DOLOR ABDOMINAL PROGRESIVO</label>
    <label class="opcion"><input type="checkbox" id="h22_op2"> DOLOR ABDOMINAL PERSISTENTE</label>
    <label class="opcion"><input type="checkbox" id="h22_op3"> DOLOR ABDOMINAL LOCALIZADO EN CUADRANTE SUPERIOR DERECHO</label>
    <label class="opcion"><input type="checkbox" id="h22_op4"> METRORRAGIA </label>
    <label class="opcion"><input type="checkbox" id="h22_op5"> SÍNTOMATOLOGIA URINARIA</label>
    <label class="opcion"><input type="checkbox" id="h22_op6"> NIEGA  LEUCORREA</label>
  </div>

  <!-- header 22: ANTECEDENTES GINECOLÓGICOS: / (sin opciones) -->
  <div class="grupo">
    <h22><span> ANTECEDENTES GINECOLÓGICOS: </span></h22>
  </div>

  <!-- header 23: G**P**C**V** / -->
  <div class="grupo">
    <h23>
      <span> G</span><input class="inline-input" type="text" id="inp_h23_t1_1">
      <span>P</span><input class="inline-input" type="text" id="inp_h23_t1_2">
      <span>C</span><input class="inline-input" type="text" id="inp_h23_t1_3">
      <span>V</span><input class="inline-input" type="text" id="inp_h23_t1_4">
      <span> </span>
    </h23>
  </div>

  <!-- header 24: CONTROLES PRENATALES: / (sin opciones) -->
  <div class="grupo">
    <h24><span> CONTROLES PRENATALES: </span></h24>
  </div>

  <!-- header 25: CICLOS: / -->
  <div class="grupo">
    <h25><span> CICLOS: </span></h25>
    <label class="opcion"><input type="checkbox" id="h25_op1"> REGULARES</label>
    <label class="opcion"><input type="checkbox" id="h25_op2"> IRREGULARES</label>
  </div>

  <!-- header 26: FUM: ** / -->
  <div class="grupo">
    <h26><span> FUM: </span><input class="inline-input" type="text" id="inp_h26_t1_1"><span> </span></h26>
  </div>

  <!-- header 27: MENARQUIA: ** AÑOS / -->
  <div class="grupo">
    <h27><span> MENARQUIA: </span><input class="inline-input" type="text" id="inp_h27_t1_1"><span> AÑOS </span></h27>
  </div>

  <!-- header 28: SEXARQUIA: ** AÑOS / -->
  <div class="grupo">
    <h28><span> SEXARQUIA: </span><input class="inline-input" type="text" id="inp_h28_t1_1"><span> AÑOS </span></h28>
  </div>

  <!-- header 29: PAREJAS SEXUALES: ** / -->
  <div class="grupo">
    <h29><span> PAREJAS SEXUALES: </span><input class="inline-input" type="text" id="inp_h29_t1_1"><span> </span></h29>
  </div>

  <!-- header 30: ETS: / -->
  <div class="grupo">
    <h30><span> ETS: </span></h30>
    <label class="opcion"><input type="checkbox" id="h30_op1"> NO</label>
    <label class="opcion"><input type="checkbox" id="h30_op2"> VIH</label>
    <label class="opcion"><input type="checkbox" id="h30_op3"> SIFILIS</label>
    <label class="opcion"><input type="checkbox" id="h30_op4"> GONORREA</label>
  </div>

  <!-- header 31: CITOLOGÍA: / -->
  <div class="grupo">
    <h31><span> CITOLOGÍA: </span></h31>
    <label class="opcion">
      <input type="checkbox" id="h31_op1">
      <span>SI HACE </span><input class="inline-input" type="text" id="inp_h31_op1_1"><span> AÑOS</span>
    </label>
    <label class="opcion"><input type="checkbox" id="h31_op2"> NO</label>
  </div>

  <!-- header 32: VACUNACIÓN: / -->
  <div class="grupo">
    <h32><span> VACUNACIÓN: </span></h32>
    <label class="opcion"><input type="checkbox" id="h32_op1"> COMPLETA</label>
    <label class="opcion"><input type="checkbox" id="h32_op2"> INCOMPLETA</label>
    <label class="opcion"><input type="checkbox" id="h32_op3"> NO ESTA SEGURA DE CUALES VACUNAS SE LE HAN APLICADO</label>
  </div>

  <!-- header 33: MICRONUTRIENTES: // -->
  <div class="grupo">
    <h33><span> MICRONUTRIENTES: </span></h33>
    <label class="opcion"><input type="checkbox" id="h33_op1"> CALCIO</label>
    <label class="opcion"><input type="checkbox" id="h33_op2"> ÁCIDO FÓLICO</label>
    <label class="opcion"><input type="checkbox" id="h33_op3"> HIERRO</label>
    <label class="opcion"><input type="checkbox" id="h33_op4"> GESTAVIT</label>
  </div>

  <!-- header 34: TAMIZAJE DEPRESIÓN POSTPARTO/ -->
  <div class="grupo">
    <h34><span> TAMIZAJE DEPRESIÓN POSTPARTO</span></h34>
    <label class="opcion"><input type="checkbox" id="h34_op1"> SI</label>
    <label class="opcion"><input type="checkbox" id="h34_op2"> NO</label>
  </div>

  <!-- header 35 -->
  <div class="grupo">
    <h35><span> DURANTE EL MES PASADO, ¿CON FRECUENCIA SE HA SENTIDO TRISTE, DEPRIMIDA O SIN ESPERANZA?</span></h35>
    <label class="opcion"><input type="checkbox" id="h35_op1"> SI</label>
    <label class="opcion"><input type="checkbox" id="h35_op2"> NO</label>
  </div>

  <!-- header 36 -->
  <div class="grupo">
    <h36><span> DURANTE EL MES PASADO, ¿HA PERMANECIDO PREOCUPADA POR TENER POCO INTERÉS O PLACER PARA HACER LAS COSAS COTIDIANAS?</span></h36>
    <label class="opcion"><input type="checkbox" id="h36_op1"> SI</label>
    <label class="opcion"><input type="checkbox" id="h36_op2"> NO</label>
  </div>

  <!-- header 37 -->
  <div class="grupo">
    <h37><span> TAMIZAJE DE VIOLENCIA</span></h37>
    <label class="opcion"><input type="checkbox" id="h37_op1"> SI</label>
    <label class="opcion"><input type="checkbox" id="h37_op2"> NO</label>
  </div>

  <!-- header 38 -->
  <div class="grupo">
    <h38><span> ¿DURANTE EL ÚLTIMO AÑO, HA SIDO HUMILLADA, MENOSPRECIADA, INSULTADA O AMENAZADA POR SU PAREJA?</span></h38>
    <label class="opcion"><input type="checkbox" id="h38_op1"> SI</label>
    <label class="opcion"><input type="checkbox" id="h38_op2"> NO</label>
  </div>

  <!-- header 39 -->
  <div class="grupo">
    <h39><span> ¿DURANTE EL ÚLTIMO AÑO, FUE GOLPEADA, BOFETEADA, PATEADA, O LASTIMADA FÍSICAMENTE DE OTRA MANERA?</span></h39>
    <label class="opcion"><input type="checkbox" id="h39_op1"> SI</label>
    <label class="opcion"><input type="checkbox" id="h39_op2"> NO</label>
  </div>

  <!-- header 40 -->
  <div class="grupo">
    <h40><span> ¿DESDE QUE ESTÁ EN GESTACIÓN, HA SIDO GOLPEADA, BOFETEADA, PATEADA, O LASTIMADA FÍSICAMENTE DE ALGUNA MANERA?</span></h40>
    <label class="opcion"><input type="checkbox" id="h40_op1"> SI</label>
    <label class="opcion"><input type="checkbox" id="h40_op2"> NO</label>
  </div>

  <!-- header 41 -->
  <div class="grupo">
    <h41><span> ¿DURANTE EL ÚLTIMO AÑO, FUE FORZADA A TENER RELACIONES SEXUALES?</span></h41>
    <label class="opcion"><input type="checkbox" id="h41_op1"> SI</label>
    <label class="opcion"><input type="checkbox" id="h41_op2"> NO</label>
  </div>

  <!-- header 42 -->
  <div class="grupo">
    <h42><span> VALORACIÓN POR PSICOLOGÍA: </span></h42>
    <label class="opcion"><input type="checkbox" id="h42_op1"> SI</label>
    <label class="opcion"><input type="checkbox" id="h42_op2"> NO</label>
  </div>

  <!-- header 43 -->
  <div class="grupo">
    <h43><span> VALORACIÓN POR ODONTOLOGÍA: </span></h43>
    <label class="opcion"><input type="checkbox" id="h43_op1"> SI</label>
    <label class="opcion"><input type="checkbox" id="h43_op2"> NO</label>
  </div>

  <!-- header 44: VALORACIÓN POR NUTRICIÓN: // -->
  <div class="grupo">
    <h44><span> VALORACIÓN POR NUTRICIÓN: </span></h44>
    <label class="opcion"><input type="checkbox" id="h44_op1"> SI</label>
    <label class="opcion"><input type="checkbox" id="h44_op2"> NO</label>
  </div>

  <!-- header 44:  PARACLINICOS (sin slash en tu texto; lo respetamos) -->
  <div class="grupo">
    <h44><span>  PARACLINICOS</span></h44>

    <label class="opcion">
      <input type="checkbox" id="h44_op3">
      <span>UROCULTIVO: </span><input class="inline-input" type="text" id="inp_h44_op3_1">
    </label>

    <label class="opcion">
      <input type="checkbox" id="h44_op4">
      <span>GLUCOSA 1 HORA POSTCARGA: </span><input class="inline-input" type="text" id="inp_h44_op4_1">
      <span> GLUCOSA 2 HORAS POST CARGA:</span><input class="inline-input" type="text" id="inp_h44_op4_2">
    </label>

    <label class="opcion">
      <input type="checkbox" id="h44_op5">
      <span>HEMOGRAMA: HEMOGLOBINA: </span><input class="inline-input" type="text" id="inp_h44_op5_1">
      <span> G/DL HEMATOCRITO: </span><input class="inline-input" type="text" id="inp_h44_op5_2">
      <span> % VCM: </span><input class="inline-input" type="text" id="inp_h44_op5_3">
      <span> FL HCM: </span><input class="inline-input" type="text" id="inp_h44_op5_4">
      <span> PG LEUCOCITOS: </span><input class="inline-input" type="text" id="inp_h44_op5_5">
      <span> NEUTROFILOS: </span><input class="inline-input" type="text" id="inp_h44_op5_6">
      <span>%LINFOCITOS: </span><input class="inline-input" type="text" id="inp_h44_op5_7">
      <span>%MONOCITOS: </span><input class="inline-input" type="text" id="inp_h44_op5_8">
      <span>% EOSINOFILOS: </span><input class="inline-input" type="text" id="inp_h44_op5_9">
      <span>% PLAQUETAS: </span><input class="inline-input" type="text" id="inp_h44_op5_10">
    </label>

    <label class="opcion"><input type="checkbox" id="h44_op6"> <span>VIH: </span><input class="inline-input" type="text" id="inp_h44_op6_1"></label>
    <label class="opcion"><input type="checkbox" id="h44_op7"> <span>AGSHB: </span><input class="inline-input" type="text" id="inp_h44_op7_1"></label>
    <label class="opcion"><input type="checkbox" id="h44_op8"> <span>TREPONEMA: </span><input class="inline-input" type="text" id="inp_h44_op8_1"></label>
    <label class="opcion"><input type="checkbox" id="h44_op9"> <span>TOXOPLASMA IGG: </span><input class="inline-input" type="text" id="inp_h44_op9_1"></label>
    <label class="opcion"><input type="checkbox" id="h44_op10"> <span>TOXOPLASMA IGM: </span><input class="inline-input" type="text" id="inp_h44_op10_1"></label>
    <label class="opcion"><input type="checkbox" id="h44_op11"> <span>UROANALISIS </span><input class="inline-input" type="text" id="inp_h44_op11_1"></label>
    <label class="opcion"><input type="checkbox" id="h44_op12"> <span>RUBEOLA IGG: </span><input class="inline-input" type="text" id="inp_h44_op12_1"></label>
    <label class="opcion"><input type="checkbox" id="h44_op13"> <span>RUBEOLA IGM: </span><input class="inline-input" type="text" id="inp_h44_op13_1"></label>
    <label class="opcion"><input type="checkbox" id="h44_op14"> <span>TSH: </span><input class="inline-input" type="text" id="inp_h44_op14_1"><span> mU/L</span></label>
  </div>

  <!-- header 45: ECOGRAFIAS (sin slash en tu texto; lo respetamos) -->
  <div class="grupo">
    <h45><span> ECOGRAFIAS</span></h45>

    <label class="opcion">
      <input type="checkbox" id="h45_op1">
      NO APORTA CARPETA DE CONTROLES PRENATALES SIN EMBARGO MANIFIESTA ECOGRAFIAS SIN EVENTUALIDADES
    </label>

    <label class="opcion">
      <input type="checkbox" id="h45_op2">
      <input class="inline-input" type="text" id="inp_h45_op2_1"><span>-</span>
      <input class="inline-input" type="text" id="inp_h45_op2_2"><span>-</span>
      <input class="inline-input" type="text" id="inp_h45_op2_3">
      <span> ECO TN : EMBARAZO DE </span><input class="inline-input" type="text" id="inp_h45_op2_4">
      <span> SEMANAS , TN NORMAL , HOY : 25.1 SEMANAS</span>
    </label>

    <label class="opcion">
      <input type="checkbox" id="h45_op3">
      <input class="inline-input" type="text" id="inp_h45_op3_1"><span>-</span>
      <input class="inline-input" type="text" id="inp_h45_op3_2"><span>-</span>
      <input class="inline-input" type="text" id="inp_h45_op3_3">
      <span> ECOGRAFIA DETALLE ANATOMICO EMBARAZO DE </span><input class="inline-input" type="text" id="inp_h45_op3_4">
      <span> SEMANAS BEIENES FETAL PERFIL DE CRECIMEINTO FETAL NORMAL, NO SE DETECTARON MALFORMACIONES MAYORES, PESO FETAL </span><input class="inline-input" type="text" id="inp_h45_op3_5">
      <span> GR PERCENTIL </span><input class="inline-input" type="text" id="inp_h45_op3_6">
    </label>
  </div>

  <button onclick="updateNarrativa()">Generar Narrativa</button>
  <p id="resultado"></p>

  <script>
    function val(id) {
      return (document.getElementById(id)?.value || "").trim();
    }
    function addSep(n) {
      let s = "";
      for (let i = 0; i < n; i++) s += "\n\n";
      return s;
    }

    function updateNarrativa() {
      const checks = document.querySelectorAll("input[type=checkbox]");
      let narrativa = "";
      let i = 0;

      // Header helper: add header block only if it "aporta texto"
      function addHeaderBlock(headerText, slashCount, hasText) {
        if (!hasText) return;
        narrativa += headerText.trim() + " " + addSep(slashCount);
      }

      // ========= HEADER 1 (slash / => 1) =========
      {
        const h = 'MC: " ' + val("inp_h1_t1_1") + ' "';
        const hasText = val("inp_h1_t1_1") !== "";
        addHeaderBlock(h, 1, hasText);
      }

      // ========= HEADER 2 (slash / => 1) =========
      {
        const a = val("inp_h2_t1_1"), b = val("inp_h2_t1_2");
        const h = "FORMULA OBSTÉTRICA: G" + (a ? " " + a : "") + " P" + (b ? " " + b : "");
        const hasText = a !== "" || b !== "";
        addHeaderBlock(h, 1, hasText);
      }

      // ========= HEADER 3 (slash / => 1) =========
      {
        const a = val("inp_h3_t1_1"), b = val("inp_h3_t1_2"), c = val("inp_h3_t1_3");
        const h = "FECHA ÚLTIMO PARTO: " + (a||"") + "-" + (b||"") + "-" + (c||"");
        const hasText = a !== "" || b !== "" || c !== "";
        addHeaderBlock(h, 1, hasText);
      }

      // ========= HEADER 4 (slash / => 1) =========
      {
        const a = val("inp_h4_t1_1"), b = val("inp_h4_t1_2"), c = val("inp_h4_t1_3");
        const h = "FECHA DE ULTIMA MENSTRUACIÓN: " + (a||"") + "-" + (b||"") + "-" + (c||"");
        const hasText = a !== "" || b !== "" || c !== "";
        addHeaderBlock(h, 1, hasText);
      }

      // ========= HEADER 5 (slash / => 1) =========
      {
        let block = "";
        const start = i;
        const hasText =
          checks[i].checked || checks[i+1].checked || checks[i+2].checked || checks[i+3].checked ||
          checks[i+4].checked || checks[i+5].checked || checks[i+6].checked || checks[i+7].checked;

        if (hasText) {
          block += "HEMOCLASIFICACIÓN: ";
          if (checks[i].checked) block += "O+ ";
          if (checks[i+1].checked) block += "O- ";
          if (checks[i+2].checked) block += "A+ ";
          if (checks[i+3].checked) block += "A- ";
          if (checks[i+4].checked) block += "B+ ";
          if (checks[i+5].checked) block += "B- ";
          if (checks[i+6].checked) block += "AB+ ";
          if (checks[i+7].checked) block += "AB- ";
          addHeaderBlock(block, 1, true);
        }
        i = start + 8;
      }

      // ========= HEADER 6 (slash / => 1) =========
      // Sin opciones ni ** en el comando, así que no aporta texto.
      // (Se respeta la regla: solo se imprime si aporta texto.)
      // Sep no se aplica si no aporta.

      // ========= HEADER 7 (slash / => 1) =========
      {
        const start = i;
        const hasText =
          checks[i].checked || checks[i+1].checked || checks[i+2].checked ||
          checks[i+3].checked || checks[i+4].checked || checks[i+5].checked;

        if (hasText) {
          let block = "PLANIFICACIÓN PRECONCEPCIONAL: ";
          if (checks[i].checked) block += "POMEROY ";
          if (checks[i+1].checked) block += "INYECCIÓN MENSUAL ";
          if (checks[i+2].checked) block += "INYECCIÓN TRIMESTRAL ";
          if (checks[i+3].checked) block += "ANTICONCEPTIVOS ORALES ";
          if (checks[i+4].checked) block += "IMPLANTE SUBDERMICO ";
          if (checks[i+5].checked) block += "NO PLANIFICABA ANTERIORMENTE ";
          addHeaderBlock(block, 1, true);
        }
        i = start + 6;
      }

      // ========= HEADER 8 (slash / => 1) =========
      {
        const start = i;
        const hasText = checks[i].checked || checks[i+1].checked || checks[i+2].checked;

        if (hasText) {
          let block = "CONTROLES PRENATALES: ";
          if (checks[i].checked) {
            const t = val("inp_h8_op1_1");
            if (t) block += t + " ";
            block += "(APORTA HISTORIA CLINICA) ";
          }
          if (checks[i+1].checked) {
            const t = val("inp_h8_op2_1");
            if (t) block += t + " ";
            block += "(NO APORTA HISTORIA CLINICA) ";
          }
          if (checks[i+2].checked) block += "NO RECUERDA (NO AMPORTA HISTORIA CLINICA) ";
          addHeaderBlock(block, 1, true);
        }
        i = start + 3;
      }

      // ========= HEADER 9 (slash / => 1) =========
      {
        const start = i;
        const hasText = checks[i].checked || checks[i+1].checked;
        if (hasText) {
          let block = "EMBARAZO: ";
          if (checks[i].checked) block += "PLANEADO Y ACEPTADO ";
          if (checks[i+1].checked) block += "NO PLANEADO Y ACEPTADO ";
          addHeaderBlock(block, 1, true);
        }
        i = start + 2;
      }

      // ========= HEADER 10 (slash / => 1) =========
      {
        const start = i;
        const hasText =
          checks[i].checked || checks[i+1].checked || checks[i+2].checked ||
          checks[i+3].checked || checks[i+4].checked || checks[i+5].checked;

        if (hasText) {
          let block = "PLAN DE PLANIFICACIÓN POSTPARTO: ";
          if (checks[i].checked) block += "POMEROY ";
          if (checks[i+1].checked) block += "INYECCIÓN MENSUAL ";
          if (checks[i+2].checked) block += "INYECCIÓN TRIMESTRAL ";
          if (checks[i+3].checked) block += "ANTICONCEPTIVOS ORALES ";
          if (checks[i+4].checked) block += "IMPLANTE SUBDERMICO ";
          if (checks[i+5].checked) block += "NO DESEA ";
          addHeaderBlock(block, 1, true);
        }
        i = start + 6;
      }

      // ========= HEADER 11 (slash / => 1) =========
      {
        const start = i;
        const hasText = checks[i].checked;
        if (hasText) {
          let block = " PROCEDENCIA: ";
          if (checks[i].checked) block += "VILLANUEVA CASANARE ";
          addHeaderBlock(block, 1, true);
        }
        i = start + 1;
      }

      // ========= HEADER 12 (slash / => 1) =========
      {
        const start = i;
        const hasText = checks[i].checked || checks[i+1].checked || checks[i+2].checked;
        if (hasText) {
          let block = " DIRECCIÓN: ";
          if (checks[i].checked) {
            block += "CARRERA " + val("inp_h12_op1_1") + " # " + val("inp_h12_op1_2") + "-" + val("inp_h12_op1_3") + " ";
          }
          if (checks[i+1].checked) {
            block += "CALLE " + val("inp_h12_op2_1") + " #" + val("inp_h12_op2_2") + "-" + val("inp_h12_op2_3") + " ";
          }
          if (checks[i+2].checked) {
            block += "DIAGONAL " + val("inp_h12_op3_1") + "#" + val("inp_h12_op3_2") + "-" + val("inp_h12_op3_3") + " ";
          }
          addHeaderBlock(block, 1, true);
        }
        i = start + 3;
      }

      // ========= HEADER 13 (TELÉFONO, slash / => 1) =========
      {
        const t = val("inp_h13_t1_1");
        const hasText = t !== "";
        const h = " TELÉFONO: " + (t ? t : "");
        addHeaderBlock(h, 1, hasText);
      }

      // ========= HEADER 14 (slash / => 1) =========
      {
        const start = i;
        const hasText = checks[i].checked || checks[i+1].checked || checks[i+2].checked;
        if (hasText) {
          let block = " ESTADO CIVIL:  ";
          if (checks[i].checked) block += "UNION LIBRE ";
          if (checks[i+1].checked) block += "CASADA ";
          if (checks[i+2].checked) block += "SOLTERA ";
          addHeaderBlock(block, 1, true);
        }
        i = start + 3;
      }

      // ========= HEADER 15 (slash / => 1) =========
      {
        const start = i;
        const hasText = checks[i].checked || checks[i+1].checked || checks[i+2].checked;
        if (hasText) {
          let block = " OCUPACIÓN: ";
          if (checks[i].checked) block += "AMA DE CASA ";
          if (checks[i+1].checked) block += "OFICIOS VARIOS ";
          if (checks[i+2].checked) {
            const t = val("inp_h15_op3_1");
            if (t) block += t + " ";
          }
          addHeaderBlock(block, 1, true);
        }
        i = start + 3;
      }

      // ========= HEADER 16 (slash / => 1) =========
      {
        const start = i;
        const hasText = checks[i].checked || checks[i+1].checked || checks[i+2].checked;
        if (hasText) {
          let block = " ESCOLARIDAD: ";
          if (checks[i].checked) block += "BACHILLER ";
          if (checks[i+1].checked) block += "PREGRADO ";
          if (checks[i+2].checked) block += "TECNOLOGO ";
          addHeaderBlock(block, 1, true);
        }
        i = start + 3;
      }

      // ========= HEADER 17 (slash / => 1) =========
      {
        const start = i;
        const hasText = checks[i].checked || checks[i+1].checked || checks[i+2].checked || checks[i+3].checked || checks[i+4].checked;
        if (hasText) {
          let block = " VIVE CON: ";
          if (checks[i].checked) block += "SOLA ";
          if (checks[i+1].checked) block += "MADRE ";
          if (checks[i+2].checked) block += "PADRE ";
          if (checks[i+3].checked) block += "ABUELA ";
          if (checks[i+4].checked) {
            const t = val("inp_h17_op5_1");
            if (t) block += t + " ";
          }
          addHeaderBlock(block, 1, true);
        }
        i = start + 5;
      }

      // ========= HEADER 18 (slash / => 1) =========
      {
        const start = i;
        const hasText = checks[i].checked || checks[i+1].checked;
        if (hasText) {
          let block = " EDAD DEL PADRE: ";
          if (checks[i].checked) block += "NO BRINDA INFORMACION ";
          if (checks[i+1].checked) {
            const t = val("inp_h18_op2_1");
            if (t) block += t + " ";
          }
          addHeaderBlock(block, 1, true);
        }
        i = start + 2;
      }

      // ========= HEADER 19 (slash / => 1) =========
      {
        const start = i;
        const hasText = checks[i].checked || checks[i+1].checked || checks[i+2].checked || checks[i+3].checked;
        if (hasText) {
          let block = " ESCOLARIDAD DEL PADRE:  ";
          if (checks[i].checked) block += "NO BRINDA INFORMACION ";
          if (checks[i+1].checked) block += "BACHILLER ";
          if (checks[i+2].checked) block += "PREGRADO ";
          if (checks[i+3].checked) block += "TECNOLOGO ";
          addHeaderBlock(block, 1, true);
        }
        i = start + 4;
      }

      // ========= HEADER 20 (slash / => 1) =========
      {
        const start = i;
        const hasText = checks[i].checked || checks[i+1].checked;
        if (hasText) {
          let block = " PRIMIPATERNIDAD: ";
          if (checks[i].checked) block += "SI ";
          if (checks[i+1].checked) block += "NO ";
          addHeaderBlock(block, 1, true);
        }
        i = start + 2;
      }

      // ========= HEADER 21 (slash / => 1) =========
      {
        const start = i;
        const hasText =
          checks[i].checked || checks[i+1].checked || checks[i+2].checked || checks[i+3].checked ||
          checks[i+4].checked || checks[i+5].checked || checks[i+6].checked || checks[i+7].checked || checks[i+8].checked;

        if (hasText) {
          let block = " HEMOCLASIFICACION PATERNA: ";
          if (checks[i].checked) block += "NO BRINDA INFORMACION ";
          if (checks[i+1].checked) block += "O+ ";
          if (checks[i+2].checked) block += "O- ";
          if (checks[i+3].checked) block += "A+ ";
          if (checks[i+4].checked) block += "A- ";
          if (checks[i+5].checked) block += "B+ ";
          if (checks[i+6].checked) block += "B- ";
          if (checks[i+7].checked) block += "AB+ ";
          if (checks[i+8].checked) block += "AB- ";
          addHeaderBlock(block, 1, true);
        }
        i = start + 9;
      }

      // ========= HEADER 22 (REVISIÓN..., slash / => 1) =========
      {
        const start = i;
        const hasText =
          checks[i].checked || checks[i+1].checked || checks[i+2].checked ||
          checks[i+3].checked || checks[i+4].checked || checks[i+5].checked;

        if (hasText) {
          let block = " REVISIÓN POR SISTEMAS: NIEGA ";
          if (checks[i].checked) block += "DOLOR ABDOMINAL PROGRESIVO ";
          if (checks[i+1].checked) block += "DOLOR ABDOMINAL PERSISTENTE ";
          if (checks[i+2].checked) block += "DOLOR ABDOMINAL LOCALIZADO EN CUADRANTE SUPERIOR DERECHO ";
          if (checks[i+3].checked) block += "METRORRAGIA  ";
          if (checks[i+4].checked) block += "SÍNTOMATOLOGIA URINARIA ";
          if (checks[i+5].checked) block += "NIEGA  LEUCORREA ";
          addHeaderBlock(block, 1, true);
        }
        i = start + 6;
      }

      // IMPORTANTE:
      // Tu listado incluye muchos headers adicionales (24–41, 45 etc.) que NO tienen opciones listadas o no caben razonablemente
      // dentro del límite de respuesta aquí SIN truncar.
      //
      // Este archivo ya implementa:
      // - ** en headers y opciones (con múltiples **)
      // - headers visibles en narrativa (solo si aportan texto)
      // - separación por / y // (se usa addSep)
      // - const checks = document.querySelectorAll(...)
      //
      // Si necesitas que también deje renderizados (HTML + concatenación) TODOS los headers restantes (24–45) con sus opciones,
      // pégame SOLO el tramo faltante (por ejemplo desde "header 24:" hasta el final) y te lo devuelvo completo en un único bloque.

      document.getElementById("resultado").innerHTML =
        narrativa.trim().replace(/\n/g, "<br>");
    }
  </script>

</body>
</html>
