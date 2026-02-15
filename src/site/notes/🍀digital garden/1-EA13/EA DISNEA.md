---
{"dg-publish":true,"permalink":"/digital-garden/1-ea-13/ea-disnea/","dgPassFrontmatter":true}
---

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Narrativa Dinámica</title>
</head>
<body>
  <h1>parte 1</h1>
  <label><input type="checkbox"> ACUDE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE, REFIERE</label><br>
  <label><input type="checkbox"> ACUDE AL SERVICIO DE URGENCIAS ACOMPAÑADO DE XXXX, REFIERE</label><br>
  <label><input type="checkbox"> ES TRAIDO AL SERVICIO DE URGENCIAS POR MADRE QUIEN REFIERE QUE HA PRESENTADO</label><br>

  <h2>sintoma cardinal</h2>
  <label><input type="checkbox"> cuadro clinico de  # de evolución consistente en disnea en reposo</label><br>
  <label><input type="checkbox"> cuadro clinico de  # de evolución consistente en disnea de minimos esfuerzos</label><br>
  <label><input type="checkbox"> cuadro clinico de  # de evolución consistente en disnea de medianos esfuerzos</label><br>

  <h3>acompañado</h3>
  <label><input type="checkbox"> dolor con la respiración</label><br>
  <label><input type="checkbox"> tos seca</label><br>
  <label><input type="checkbox"> tos con esputo mucopurulento</label><br>
  <label><input type="checkbox"> tos con esputo verdoso</label><br>
  <label><input type="checkbox"> tiraje subcostal</label><br>
  <label><input type="checkbox"> tiraje intercostal</label><br>
  <label><input type="checkbox"> tiraje supraclavicular</label><br>

  <button onclick="updateNarrativa()">Generar Narrativa</button>
  <p id="resultado"></p>

  <script>
    function updateNarrativa() {
      const checks = document.querySelectorAll("input[type=checkbox]");
      let narrativa = "";
      if (checks[0].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS SIN ACOMPAÑANTE, REFIERE ";
      if (checks[1].checked) narrativa += "ACUDE AL SERVICIO DE URGENCIAS ACOMPAÑADO DE XXXX, REFIERE ";
      if (checks[2].checked) narrativa += "ES TRAIDO AL SERVICIO DE URGENCIAS POR MADRE QUIEN REFIERE QUE HA PRESENTADO ";
      if (checks[3].checked) narrativa += "cuadro clinico de  # de evolución consistente en disnea en reposo ";
      if (checks[4].checked) narrativa += "cuadro clinico de  # de evolución consistente en disnea de minimos esfuerzos ";
      if (checks[5].checked) narrativa += "cuadro clinico de  # de evolución consistente en disnea de medianos esfuerzos ";
      if (checks[6].checked) narrativa += "dolor con la respiración ";
      if (checks[7].checked) narrativa += "tos seca ";
      if (checks[8].checked) narrativa += "tos con esputo mucopurulento ";
      if (checks[9].checked) narrativa += "tos con esputo verdoso ";
      if (checks[10].checked) narrativa += "tiraje subcostal ";
      if (checks[11].checked) narrativa += "tiraje intercostal ";
      if (checks[12].checked) narrativa += "tiraje supraclavicular ";
      document.getElementById("resultado").textContent = narrativa.trim();
    }
  </script>
</body>
</html>

