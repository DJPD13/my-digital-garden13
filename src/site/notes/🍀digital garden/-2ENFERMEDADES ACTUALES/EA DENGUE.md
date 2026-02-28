---
{"dg-publish":true,"permalink":"/digital-garden/2-enfermedades-actuales/ea-dengue/","dgPassFrontmatter":true}
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
    label{display:block;margin:6px 0;white-space:pre-wrap}
    input[type="text"]{width:140px}
    select{min-width:180px}
    #resultado{white-space:pre-wrap;border:1px solid #ccc;padding:10px;margin-top:12px;border-radius:8px}
    /* h7/h8 no son headings estándar, los hacemos block */
    h7,h8{display:block;font-weight:700;margin:0 0 10px 0;white-space:pre-wrap}
  </style>
</head>
<body>

  <div class="grupo" data-header="1" data-slashes="0">
    <h1 class="titulo"></h1>

    <label>
      <input type="checkbox" id="h1_op1" data-kind="text" data-prefix="PACIENTE MASCULINO DE " data-suffix="AÑOS " data-input="h1_op1_txt">
      PACIENTE MASCULINO DE <input type="text" id="h1_op1_txt">AÑOS 
    </label>

    <label>
      <input type="checkbox" id="h1_op2" data-kind="text" data-prefix="PACIENTE FEMENINA DE " data-suffix="AÑOS" data-input="h1_op2_txt">
      PACIENTE FEMENINA DE <input type="text" id="h1_op2_txt">AÑOS
    </label>
  </div>

  <div class="grupo" data-header="2" data-slashes="0">
    <h2 class="titulo"></h2>

    <label>
      <input type="checkbox" id="h2_op1" data-kind="plain" data-text="ACUDE AL SERVICIO DE URGENCIAS  SIN ACOMPAÑANTE">
      ACUDE AL SERVICIO DE URGENCIAS  SIN ACOMPAÑANTE
    </label>

    <label>
      <input type="checkbox" id="h2_op2" data-kind="text" data-prefix="ACUDE AL SERVICIO DE URGENCIAS  CON ACOMPAÑANTE (" data-suffix=") " data-input="h2_op2_txt">
      ACUDE AL SERVICIO DE URGENCIAS  CON ACOMPAÑANTE (<input type="text" id="h2_op2_txt">) 
    </label>

    <label>
      <input type="checkbox" id="h2_op3" data-kind="text" data-prefix="EN BRAZOS DE SU MADRE (" data-suffix=")" data-input="h2_op3_txt">
      EN BRAZOS DE SU MADRE (<input type="text" id="h2_op3_txt">)
    </label>
  </div>

  <div class="grupo" data-header="3" data-slashes="0">
    <h3 class="titulo"></h3>

    <label>
      <input type="checkbox" id="h3_op1" data-kind="text" data-prefix="REFIRIENDO CUADRO CLINICO DE " data-suffix=" HORAS DE EVOLUCIÓN CONSISTENTE EN" data-input="h3_op1_txt">
      REFIRIENDO CUADRO CLINICO DE <input type="text" id="h3_op1_txt"> HORAS DE EVOLUCIÓN CONSISTENTE EN
    </label>

    <label>
      <input type="checkbox" id="h3_op2" data-kind="text" data-prefix="REFIRIENDO CUADRO CLINICO DE " data-suffix=" DÍAS DE EVOLUCIÓN CONSISTENTE EN" data-input="h3_op2_txt">
      REFIRIENDO CUADRO CLINICO DE <input type="text" id="h3_op2_txt"> DÍAS DE EVOLUCIÓN CONSISTENTE EN
    </label>
  </div>

  <div class="grupo" data-header="4" data-slashes="0">
    <h4 class="titulo"></h4>

    <label>
      <input type="checkbox" id="h4_op1" data-kind="text" data-prefix="FIEBRE CUANTIFICADA EN (" data-suffix=")" data-input="h4_op1_txt">
      FIEBRE CUANTIFICADA EN (<input type="text" id="h4_op1_txt">)
    </label>

    <label>
      <input type="checkbox" id="h4_op2" data-kind="plain" data-text="FIEBRE NO CUANTIFICADA">
      FIEBRE NO CUANTIFICADA
    </label>
  </div>

  <div class="grupo" data-header="5" data-slashes="0">
    <h5 class="titulo"> QUE MEJORA CON</h5>

    <label>
      <input type="checkbox" id="h5_op1" data-kind="plain" data-text="QUE MEJORA CON ACETAMINOFEN">
      QUE MEJORA CON ACETAMINOFEN
    </label>

    <label>
      <input type="checkbox" id="h5_op2" data-kind="plain" data-text="QUE MEJORA CON AINES">
      QUE MEJORA CON AINES
    </label>

    <label>
      <input type="checkbox" id="h5_op3" data-kind="plain" data-text="QUE MEJORA CON EL REPOSO">
      QUE MEJORA CON EL REPOSO
    </label>

    <label>
      <input type="checkbox" id="h5_op4" data-kind="plain" data-text="QUE NO MEJORA CON ACETAMINOFEN">
      QUE NO MEJORA CON ACETAMINOFEN
    </label>
  </div>

  <div class="grupo" data-header="6" data-slashes="0">
    <h6 class="titulo">, ESTO ASOCIADO A </h6>

    <label>
      <input type="checkbox" id="h6_op1" data-kind="plain" data-text="DOLOR RETROCULAR">
      DOLOR RETROCULAR
    </label>

    <label>
      <input type="checkbox" id="h6_op2" data-kind="plain" data-text="CEFALEA">
      CEFALEA
    </label>

    <label>
      <input type="checkbox" id="h6_op3" data-kind="plain" data-text="NAUSEAS">
      NAUSEAS
    </label>

    <label>
      <input type="checkbox" id="h6_op4" data-kind="plain" data-text="VOMITO">
      VOMITO
    </label>

    <label>
      <input type="checkbox" id="h6_op5" data-kind="plain" data-text="MIALGIAS">
      MIALGIAS
    </label>

    <label>
      <input type="checkbox" id="h6_op6" data-kind="plain" data-text="ARTRALGIAS">
      ARTRALGIAS
    </label>

    <label>
      <input type="checkbox" id="h6_op7" data-kind="plain" data-text="EXANTEMA">
      EXANTEMA
    </label>

    <label>
      <input type="checkbox" id="h6_op8" data-kind="text" data-prefix="PETEQUIAS EN " data-suffix="" data-input="h6_op8_txt">
      PETEQUIAS EN <input type="text" id="h6_op8_txt">
    </label>
  </div>

  <div class="grupo" data-header="7" data-slashes="2">
    <h7 class="titulo"></h7>

    <label>
      <input type="checkbox" id="h7_op1" data-kind="plain" data-text="DOLOR ABDOMINAL INTENSO Y CONTINUO">
      DOLOR ABDOMINAL INTENSO Y CONTINUO
    </label>

    <label>
      <input type="checkbox" id="h7_op2" data-kind="plain" data-text="EMESIS PERSITENTE">
      EMESIS PERSITENTE
    </label>

    <label>
      <input type="checkbox" id="h7_op3" data-kind="plain" data-text="DIARREA ">
      DIARREA 
    </label>

    <label>
      <input type="checkbox" id="h7_op4" data-kind="plain" data-text="LETARGO">
      LETARGO
    </label>

    <label>
      <input type="checkbox" id="h7_op5" data-kind="plain" data-text="IRRITABILIDAD">
      IRRITABILIDAD
    </label>

    <label>
      <input type="checkbox" id="h7_op6" data-kind="plain" data-text="HIPOTENSIÓN POSTURAL">
      HIPOTENSIÓN POSTURAL
    </label>

    <label>
      <input type="checkbox" id="h7_op7" data-kind="plain" data-text="LIPOTIMIA">
      LIPOTIMIA
    </label>
  </div>

  <div class="grupo" data-header="8" data-slashes="0">
    <h8 class="titulo">SE INGRESA AL SERVICIO DE URGENCIAS, SE DILIGENCIA FICHA DE NOTIFICACIÓN, SE INICIA AISLAMIENTO VECTORIAL, SE SOLICITAN HEMOGRAMA, PCR, NS1, IGM E IGG, SE ADMINISTRAN LÍQUIDOS INTRAVENOSOS Y SE PROPORCIONA ANALGESIA.</h8>
  </div>

  <button onclick="updateNarrativa()">Generar Narrativa</button>
  <p id="resultado"></p>

<script>
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

  // Habilita conexiones si algún checkbox trae data-link
  (function initLinks() {
    const cbs = document.querySelectorAll('input[type=checkbox][data-link]');
    cbs.forEach(cb => cb.addEventListener("change", () => syncLinkedOption(cb)));
  })();

  function updateNarrativa() {
    const checks = document.querySelectorAll("input[type=checkbox]");
    let narrativa = "";

    const smartAppend = (txt) => {
      if (txt === undefined || txt === null) return;
      const s = String(txt);
      if (!s) return;

      if (!narrativa) { narrativa += s; return; }

      const last = narrativa.slice(-1);
      const startsWithSpaceOrNL = /^[\s]/.test(s);
      const startsWithPunct = /^[,.;:)\]]/.test(s);

      if (last === "\n" || last === " " || last === "\t") {
        narrativa += s;
      } else if (startsWithSpaceOrNL || startsWithPunct) {
        narrativa += s;
      } else {
        narrativa += " " + s;
      }
    };

    const getOptionText = (cb) => {
      const kind = cb.dataset.kind || "plain";

      if (kind === "text") {
        const pref = cb.dataset.prefix || "";
        const suf = cb.dataset.suffix || "";
        const inputId = cb.dataset.input || "";
        const el = inputId ? document.getElementById(inputId) : null;
        const val = el && typeof el.value === "string" ? el.value : "";
        return pref + (val ? val : "") + suf;
      }

      if (kind === "select") {
        const pref = cb.dataset.prefix || "";
        const suf = cb.dataset.suffix || "";
        const selId = cb.dataset.select || "";
        const el = selId ? document.getElementById(selId) : null;
        const val = el && typeof el.value === "string" ? el.value : "";
        return pref + (val ? val : "") + suf;
      }

      if (kind === "multiline") {
        return cb.dataset.text || "";
      }

      return cb.dataset.text || "";
    };

    const grupos = document.querySelectorAll(".grupo");
    grupos.forEach(grupo => {
      const slashes = parseInt(grupo.getAttribute("data-slashes") || "0", 10) || 0;

      const tituloEl = grupo.querySelector(".titulo");
      const titulo = tituloEl ? tituloEl.textContent : "";

      const cbs = grupo.querySelectorAll('input[type=checkbox]');
      const checked = Array.from(cbs).filter(cb => cb.checked);

      let added = false;

      if (cbs.length === 0) {
        if (titulo) { smartAppend(titulo); added = true; }
      } else if (checked.length > 0) {
        if (titulo) { smartAppend(titulo); added = true; }
        checked.forEach(cb => {
          const txt = getOptionText(cb);
          if ((cb.dataset.kind || "plain") === "multiline") {
            // Para =>>> <<< copiar multilínea tal cual (sin smart spacing)
            narrativa += (narrativa ? "" : "") + txt;
          } else {
            smartAppend(txt);
          }
          added = true;
        });
      }

      if (added && slashes > 0) {
        for (let i = 0; i < slashes; i++) narrativa += "\n\n";
      }
    });

    document.getElementById("resultado").textContent = narrativa.trim();
  }
</script>

</body>
</html>


