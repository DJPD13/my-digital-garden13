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
    body { font-family: system-ui, Arial, sans-serif; line-height: 1.35; padding: 16px; }
    .seccion { margin-bottom: 18px; }
    label { display: block; margin: 6px 0; }
    input[type="text"] { width: 120px; }
    select { min-width: 160px; }
    #resultado { white-space: pre-wrap; border: 1px solid #ccc; padding: 10px; margin-top: 12px; }
  </style>
</head>
<body>

  <div class="seccion" data-header="1">
    <h1 class="titulo"> .</h1>

    <label>
      <input type="checkbox" id="h1_op1" data-type="text" data-prefix="PACIENTE MASCULINO DE " data-suffix="AÑOS " data-input-id="h1_op1_txt">
      MASCULINO <input type="text" id="h1_op1_txt" />AÑOS
    </label>

    <label>
      <input type="checkbox" id="h1_op2" data-type="text" data-prefix="PACIENTE FEMENINA DE " data-suffix="AÑOS" data-input-id="h1_op2_txt">
      PACIENTE FEMENINA DE <input type="text" id="h1_op2_txt" />AÑOS
    </label>
  </div>

  <div class="seccion" data-header="2">
    <h2 class="titulo">ACUDE AL SERVICIO DE URGENCIAS </h2>

    <label>
      <input type="checkbox" id="h2_op1" data-type="plain" data-text="SIN ACOMPAÑANTE">
      SIN ACOMPAÑANTE
    </label>

    <label>
      <input type="checkbox" id="h2_op2" data-type="text" data-prefix="CON ACOMPAÑANTE (" data-suffix=")" data-input-id="h2_op2_txt">
      CON ACOMPAÑANTE (<input type="text" id="h2_op2_txt" />)
    </label>

    <label>
      <input type="checkbox" id="h2_op3" data-type="text" data-prefix="EN BRAZOS DE SU MADRE (" data-suffix=")" data-input-id="h2_op3_txt">
      EN BRAZOS DE SU MADRE (<input type="text" id="h2_op3_txt" />)
    </label>
  </div>

  <div class="seccion" data-header="3">
    <h3 class="titulo"> ,</h3>

    <label>
      <input type="checkbox" id="h3_op1" data-type="text" data-prefix="REFIRIENDO CUADRO CLINICO DE " data-suffix=" HORAS DE EVOLUCIÓN CONSISTENTE EN" data-input-id="h3_op1_txt">
      REFIRIENDO CUADRO CLINICO DE <input type="text" id="h3_op1_txt" /> HORAS DE EVOLUCIÓN CONSISTENTE EN
    </label>

    <label>
      <input type="checkbox" id="h3_op2" data-type="text" data-prefix="REFIRIENDO CUADRO CLINICO DE " data-suffix=" DÍAS DE EVOLUCIÓN CONSISTENTE EN" data-input-id="h3_op2_txt">
      REFIRIENDO CUADRO CLINICO DE <input type="text" id="h3_op2_txt" /> DÍAS DE EVOLUCIÓN CONSISTENTE EN
    </label>
  </div>

  <div class="seccion" data-header="4">
    <h4 class="titulo"> CONSISTENTE EN</h4>

    <label>
      <input type="checkbox" id="h4_op1" data-type="text" data-prefix="FIEBRE CUANTIFICADA EN (" data-suffix=")" data-input-id="h4_op1_txt">
      FIEBRE CUANTIFICADA EN (<input type="text" id="h4_op1_txt" />)
    </label>

    <label>
      <input type="checkbox" id="h4_op2" data-type="plain" data-text="FIEBRE NO CUANTIFICADA">
      FIEBRE NO CUANTIFICADA
    </label>
  </div>

  <div class="seccion" data-header="5">
    <h5 class="titulo"> QUE MEJORA CON</h5>

    <label>
      <input type="checkbox" id="h5_op1" data-type="plain" data-text="ACETAMINOFEN">
      ACETAMINOFEN
    </label>

    <label>
      <input type="checkbox" id="h5_op2" data-type="plain" data-text="AINES">
      AINES
    </label>

    <label>
      <input type="checkbox" id="h5_op3" data-type="plain" data-text="PAÑOS HUMEDOS">
      PAÑOS HUMEDOS
    </label>

    <label>
      <input type="checkbox" id="h5_op4" data-type="plain" data-text="REPOSO">
      REPOSO
    </label>
  </div>

  <div class="seccion" data-header="6">
    <h6 class="titulo">, ESTO ASOCIADO A </h6>

    <label>
      <input type="checkbox" id="h6_op1" data-type="plain" data-text="CEFALEA">
      CEFALEA
    </label>

    <label>
      <input type="checkbox" id="h6_op2" data-type="plain" data-text="NAUSEAS">
      NAUSEAS
    </label>

    <label>
      <input type="checkbox" id="h6_op3" data-type="plain" data-text="VOMITO">
      VOMITO
    </label>

    <label>
      <input type="checkbox" id="h6_op4" data-type="plain" data-text="MIALGIAS">
      MIALGIAS
    </label>

    <label>
      <input type="checkbox" id="h6_op5" data-type="plain" data-text="ARTRALGIAS">
      ARTRALGIAS
    </label>

    <label>
      <input type="checkbox" id="h6_op6" data-type="plain" data-text="EXANTEMA">
      EXANTEMA
    </label>

    <label>
      <input type="checkbox" id="h6_op7" data-type="text" data-prefix="PETEQUIAS EN " data-suffix="" data-input-id="h6_op7_txt">
      PETEQUIAS EN <input type="text" id="h6_op7_txt" />
    </label>
  </div>

  <div class="seccion" data-header="7">
    <h7 class="titulo">, //</h7>

    <label>
      <input type="checkbox" id="h7_op1" data-type="plain" data-text="DOLOR ABDOMINAL INTENSO Y CONTINUO">
      DOLOR ABDOMINAL INTENSO Y CONTINUO
    </label>

    <label>
      <input type="checkbox" id="h7_op2" data-type="plain" data-text="EMESIS PERSITENTE">
      EMESIS PERSITENTE
    </label>

    <label>
      <input type="checkbox" id="h7_op3" data-type="plain" data-text="DIARREA">
      DIARREA
    </label>

    <label>
      <input type="checkbox" id="h7_op4" data-type="plain" data-text="LETARGO">
      LETARGO
    </label>

    <label>
      <input type="checkbox" id="h7_op5" data-type="plain" data-text="IRRITABILIDAD">
      IRRITABILIDAD
    </label>

    <label>
      <input type="checkbox" id="h7_op6" data-type="plain" data-text="HIPOTENSIÓN POSTURAL">
      HIPOTENSIÓN POSTURAL
    </label>

    <label>
      <input type="checkbox" id="h7_op7" data-type="plain" data-text="LIPOTIMIA">
      LIPOTIMIA
    </label>
  </div>

  <div class="seccion" data-header="8">
    <h8 class="titulo">SE INGRESA AL SERVICIO DE URGENCIAS, SE LLENA FICHA DE NOTIFICACIÓN, SE INICIA AISLAMIENTO VECTORIAL, SE PIDE HEMOGRAMA, PCR, NS1, IGM E IGG, SE INICIAN LIQUIDOS, Y ANALGESIA.  </h8>
  </div>

  <button onclick="updateNarrativa()">Generar Narrativa</button>
  <p id="resultado"></p>

<script>
  function syncLinkedOption(sourceCb) {
    const link = sourceCb.getAttribute("data-link");
    if (!link) return;

    const targetCb = document.getElementById(link);
    if (!targetCb) return;

    if (targetCb.checked !== sourceCb.checked) {
      targetCb.checked = sourceCb.checked;
      syncLinkedOption(targetCb); // encadenar si aplica
    }
  }

  // Activar auto-conexiones por data-link (si existen)
  (function initLinks() {
    const checks = document.querySelectorAll('input[type=checkbox]');
    checks.forEach(cb => {
      cb.addEventListener("change", function () {
        syncLinkedOption(cb);
      });
    });
  })();

  function updateNarrativa() {
    const checks = document.querySelectorAll("input[type=checkbox]");
    let narrativa = "";

    function append(str) {
      if (!str) return;
      if (narrativa && !/\s$/.test(narrativa) && !/^[\s,.;:]/.test(str)) {
        narrativa += " ";
      }
      narrativa += str;
    }

    function buildOptionText(cb) {
      const type = cb.dataset.type || "plain";

      if (type === "text") {
        const pref = cb.dataset.prefix || "";
        const suf = cb.dataset.suffix || "";
        const inputId = cb.dataset.inputId;
        const el = inputId ? document.getElementById(inputId) : null;
        const val = el && typeof el.value === "string" ? el.value : "";
        return pref + (val ? val : "") + suf;
      }

      if (type === "select") {
        const pref = cb.dataset.prefix || "";
        const suf = cb.dataset.suffix || "";
        const selectId = cb.dataset.selectId;
        const el = selectId ? document.getElementById(selectId) : null;
        const val = el && typeof el.value === "string" ? el.value : "";
        return pref + (val ? val : "") + suf;
      }

      return cb.dataset.text || "";
    }

    const secciones = document.querySelectorAll(".seccion");
    secciones.forEach(sec => {
      const tituloEl = sec.querySelector(".titulo");
      const titulo = tituloEl ? tituloEl.textContent : "";

      const ops = sec.querySelectorAll('input[type=checkbox]');
      if (ops.length === 0) {
        append(titulo);
        return;
      }

      let anyChecked = false;
      ops.forEach(cb => { if (cb.checked) anyChecked = true; });
      if (!anyChecked) return;

      append(titulo);
      ops.forEach(cb => {
        if (!cb.checked) return;
        append(buildOptionText(cb));
      });
    });

    document.getElementById("resultado").textContent = narrativa.trim();
  }
</script>

</body>
</html>


