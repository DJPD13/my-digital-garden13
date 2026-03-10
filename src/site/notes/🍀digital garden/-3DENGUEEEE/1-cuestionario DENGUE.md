---
{"dg-publish":true,"permalink":"/digital-garden/3-dengueeee/1-cuestionario-dengue/","dgPassFrontmatter":true}
---

<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Narrativa</title>
  <style>
    body{font-family:system-ui,Arial,sans-serif;line-height:1.35;padding:16px}
    .grupo{margin:16px 0;padding:10px;border:1px solid #ddd;border-radius:8px}
    .titulo{white-space:pre-wrap;margin:0 0 10px 0}
    label{display:flex;align-items:center;gap:10px;margin:6px 0}
    .opcion{white-space:pre-wrap}
    input[type="text"]{width:140px}
    select{min-width:180px}
    #resultado{white-space:pre-wrap;border:1px solid #ccc;padding:10px;margin-top:12px;border-radius:8px}
    /* Para niveles > 6 si llegaran a existir */
    h7,h8,h9,h10,h11,h12{display:block;font-weight:700;margin:0 0 10px 0;white-space:pre-wrap}
  </style>
</head>
<body>

  <!-- header 1:  -->
  <div class="grupo" data-title="" data-slashes="0">
    <h1 class="titulo"></h1>

    <label>
      <input type="checkbox" id="h1_op1" data-kind="text" data-prefix="PACIENTE MASCULINO DE " data-suffix=" AÑOS " data-input="h1_op1_txt">
      <span class="opcion">PACIENTE MASCULINO DE <input type="text" id="h1_op1_txt"> AÑOS </span>
    </label>

    <label>
      <input type="checkbox" id="h1_op2" data-kind="text" data-prefix="PACIENTE FEMENINA DE " data-suffix=" AÑOS" data-input="h1_op2_txt">
      <span class="opcion">PACIENTE FEMENINA DE <input type="text" id="h1_op2_txt"> AÑOS</span>
    </label>
  </div>

  <!-- header 2:  -->
  <div class="grupo" data-title="" data-slashes="0">
    <h2 class="titulo"></h2>

    <label>
      <input type="checkbox" id="h2_op1" data-kind="plain" data-text="ACUDE AL SERVICIO DE URGENCIAS  SIN ACOMPAÑANTE">
      <span class="opcion">ACUDE AL SERVICIO DE URGENCIAS  SIN ACOMPAÑANTE</span>
    </label>

    <label>
      <input type="checkbox" id="h2_op2" data-kind="text" data-prefix="ACUDE AL SERVICIO DE URGENCIAS  CON ACOMPAÑANTE (" data-suffix=") " data-input="h2_op2_txt">
      <span class="opcion">ACUDE AL SERVICIO DE URGENCIAS  CON ACOMPAÑANTE (<input type="text" id="h2_op2_txt">) </span>
    </label>

    <label>
      <input type="checkbox" id="h2_op3" data-kind="text" data-prefix="EN BRAZOS DE SU MADRE (" data-suffix=")" data-input="h2_op3_txt">
      <span class="opcion">EN BRAZOS DE SU MADRE (<input type="text" id="h2_op3_txt">)</span>
    </label>
  </div>

  <!-- header 3: -->
  <div class="grupo" data-title="" data-slashes="0">
    <h3 class="titulo"></h3>

    <label>
      <input type="checkbox" id="h3_op1" data-kind="text" data-prefix="REFIRIENDO CUADRO CLINICO DE " data-suffix=" HORAS DE EVOLUCIÓN CONSISTENTE EN" data-input="h3_op1_txt">
      <span class="opcion">REFIRIENDO CUADRO CLINICO DE <input type="text" id="h3_op1_txt"> HORAS DE EVOLUCIÓN CONSISTENTE EN</span>
    </label>

    <label>
      <input type="checkbox" id="h3_op2" data-kind="text" data-prefix="REFIRIENDO CUADRO CLINICO DE " data-suffix=" DÍAS DE EVOLUCIÓN CONSISTENTE EN" data-input="h3_op2_txt">
      <span class="opcion">REFIRIENDO CUADRO CLINICO DE <input type="text" id="h3_op2_txt"> DÍAS DE EVOLUCIÓN CONSISTENTE EN</span>
    </label>
  </div>

  <!-- header 4:  -->
  <div class="grupo" data-title="" data-slashes="0">
    <h4 class="titulo"></h4>

    <label>
      <input type="checkbox" id="h4_op1" data-kind="text" data-prefix="FIEBRE CUANTIFICADA EN (" data-suffix=")" data-input="h4_op1_txt">
      <span class="opcion">FIEBRE CUANTIFICADA EN (<input type="text" id="h4_op1_txt">)</span>
    </label>

    <label>
      <input type="checkbox" id="h4_op2" data-kind="plain" data-text="FIEBRE NO CUANTIFICADA">
      <span class="opcion">FIEBRE NO CUANTIFICADA</span>
    </label>
  </div>

  <!-- header 5:  -->
  <div class="grupo" data-title="ASOCIADO A" data-slashes="0">
    <h5 class="titulo"></h5>

    <label>
      <input type="checkbox" id="h5_op1" data-kind="plain" data-text="DOLOR RETROCULAR">
      <span class="opcion">DOLOR RETROCULAR</span>
    </label>

    <label>
      <input type="checkbox" id="h5_op2" data-kind="plain" data-text="CEFALEA">
      <span class="opcion">CEFALEA</span>
    </label>

    <label>
      <input type="checkbox" id="h5_op3" data-kind="plain" data-text="NAUSEAS">
      <span class="opcion">NAUSEAS</span>
    </label>

    <label>
      <input type="checkbox" id="h5_op4" data-kind="plain" data-text="VOMITO">
      <span class="opcion">VOMITO</span>
    </label>

    <label>
      <input type="checkbox" id="h5_op5" data-kind="plain" data-text="MIALGIAS">
      <span class="opcion">MIALGIAS</span>
    </label>

    <label>
      <input type="checkbox" id="h5_op6" data-kind="plain" data-text="ARTRALGIAS">
      <span class="opcion">ARTRALGIAS</span>
    </label>

    <label>
      <input type="checkbox" id="h5_op7" data-kind="plain" data-text="EXANTEMA">
      <span class="opcion">EXANTEMA</span>
    </label>

    <label>
      <input type="checkbox" id="h5_op8" data-kind="text" data-prefix="PETEQUIAS EN " data-suffix="" data-input="h5_op8_txt">
      <span class="opcion">PETEQUIAS EN <input type="text" id="h5_op8_txt"></span>
    </label>
  </div>

  <!-- header 6: //  (comando; NO se muestra en el encabezado) -->
  <div class="grupo" data-title="" data-slashes="2">
    <h6 class="titulo"></h6>

    <label>
      <input type="checkbox" id="h6_op1" data-kind="plain" data-text="DOLOR ABDOMINAL INTENSO Y CONTINUO">
      <span class="opcion">DOLOR ABDOMINAL INTENSO Y CONTINUO</span>
    </label>

    <label>
      <input type="checkbox" id="h6_op2" data-kind="plain" data-text="EMESIS PERSITENTE">
      <span class="opcion">EMESIS PERSITENTE</span>
    </label>

    <label>
      <input type="checkbox" id="h6_op3" data-kind="plain" data-text="DIARREA ">
      <span class="opcion">DIARREA </span>
    </label>

    <label>
      <input type="checkbox" id="h6_op4" data-kind="plain" data-text="LETARGO">
      <span class="opcion">LETARGO</span>
    </label>

    <label>
      <input type="checkbox" id="h6_op5" data-kind="plain" data-text="IRRITABILIDAD">
      <span class="opcion">IRRITABILIDAD</span>
    </label>

    <label>
      <input type="checkbox" id="h6_op6" data-kind="plain" data-text="HIPOTENSIÓN POSTURAL">
      <span class="opcion">HIPOTENSIÓN POSTURAL</span>
    </label>

    <label>
      <input type="checkbox" id="h6_op7" data-kind="plain" data-text="LIPOTIMIA">
      <span class="opcion">LIPOTIMIA</span>
    </label>
  </div>

  <!-- header 8: ... -->
  <div class="grupo" data-title="SE INGRESA AL SERVICIO DE URGENCIAS, SE DILIGENCIA FICHA DE NOTIFICACIÓN, SE INICIA AISLAMIENTO VECTORIAL, SE SOLICITAN HEMOGRAMA, PCR, NS1, IGM E IGG, SE ADMINISTRAN LÍQUIDOS INTRAVENOSOS Y SE PROPORCIONA ANALGESIA." data-slashes="0">
    <h8 class="titulo"></h8>
  </div>

  <button onclick="updateNarrativa()">Generar Narrativa</button>
  <p id="resultado"></p>

<script>
  // Pintar títulos EXACTOS (sin mostrar comandos "/")
  (function initTitles(){
    const grupos = document.querySelectorAll(".grupo");
    grupos.forEach(g => {
      const t = g.getAttribute("data-title") ?? "";
      const h = g.querySelector(".titulo");
      if (h) h.textContent = t;
    });
  })();

  function syncLinkedOption(cb) {
    const link = cb.getAttribute("data-link");
    if (!link) return;
    const target = document.getElementById(link);
    if (!target) return;

    if (target.checked !== cb.checked) {
      target.checked = cb.checked;
      syncLinkedOption(target);
    }
  }

  (function initLinks() {
    const cbs = document.querySelectorAll('input[type=checkbox][data-link]');
    cbs.forEach(cb => cb.addEventListener("change", () => syncLinkedOption(cb)));
  })();

  function updateNarrativa() {
    const checks = document.querySelectorAll("input[type=checkbox]");
    let narrativa = "";

    const appendSmart = (piece) => {
      if (piece === undefined || piece === null) return;
      const s = String(piece);
      if (!s) return;

      if (!narrativa) { narrativa += s; return; }

      const last = narrativa.slice(-1);
      const startsWithSpaceOrNL = /^[\s]/.test(s);
      const startsWithPunct = /^[,.;:)\]]/.test(s);

      if (last === "\n" || last === " " || last === "\t") narrativa += s;
      else if (startsWithSpaceOrNL || startsWithPunct) narrativa += s;
      else narrativa += " " + s;
    };

    const getOptionText = (cb) => {
      const kind = cb.dataset.kind || "plain";

      if (kind === "multiline") return cb.dataset.text || "";

      if (kind === "select") {
        const pref = cb.dataset.prefix || "";
        const suf  = cb.dataset.suffix || "";
        const selId = cb.dataset.select || "";
        const el = selId ? document.getElementById(selId) : null;
        const val = el && typeof el.value === "string" ? el.value : "";
        return pref + (val ? val : "") + suf;
      }

      if (kind === "text") {
        const pref = cb.dataset.prefix || "";
        const suf  = cb.dataset.suffix || "";
        const inputId = cb.dataset.input || "";
        const el = inputId ? document.getElementById(inputId) : null;
        const val = el && typeof el.value === "string" ? el.value : "";
        return pref + (val ? val : "") + suf;
      }

      return cb.dataset.text || "";
    };

    const grupos = document.querySelectorAll(".grupo");
    grupos.forEach(grupo => {
      const title = grupo.getAttribute("data-title") ?? "";
      const slashes = parseInt(grupo.getAttribute("data-slashes") || "0", 10) || 0;

      const cbs = grupo.querySelectorAll('input[type=checkbox]');
      const checked = Array.from(cbs).filter(cb => cb.checked);

      // Incluir header si:
      // - no tiene opciones (header 8), o
      // - tiene al menos una opción marcada
      if (cbs.length === 0) {
        appendSmart(title);
        if (slashes > 0) for (let i=0;i<slashes;i++) narrativa += "\n\n";
        return;
      }
      if (checked.length === 0) return;

      appendSmart(title);

      checked.forEach(cb => {
        const txt = getOptionText(cb);
        if ((cb.dataset.kind || "plain") === "multiline") narrativa += txt;
        else appendSmart(txt);
      });

      if (slashes > 0) for (let i=0;i<slashes;i++) narrativa += "\n\n";
    });

    document.getElementById("resultado").textContent = narrativa.trim();
  }
</script>

</body>
</html>


