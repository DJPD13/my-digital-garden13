---
{"dg-publish":true,"permalink":"/digital-garden/1-ingreso/prueba-examen-fisico-2/","dgPassFrontmatter":true}
---

<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Plan de Examen Físico</title>
  <style>
    body{
      font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial,sans-serif;
      line-height:1.35;
      margin:16px;
      max-width:1100px;
    }
    h2{margin:18px 0 8px}
    .opciones{margin:6px 0 14px 0;padding-left:8px;border-left:2px solid #ddd}
    label{display:block;margin:6px 0;cursor:pointer}
    .child{margin-left:18px;padding-left:10px;border-left:2px dashed #ddd}
    .hidden{display:none}
    input[type="text"]{margin:0 6px;min-width:260px}
    select{margin:0 6px}
    #resultado{
      display:block;
      width:100%;
      max-width:1100px;
      min-height:240px;
      white-space:pre-wrap;     /* RESPETA SALTOS DE LÍNEA */
      overflow-wrap:anywhere;   /* EVITA QUE SE “SALGA” */
      word-break:break-word;
      border:1px solid #ddd;
      padding:14px;
      border-radius:10px;
      margin-top:12px;
      font-size:16px;
      line-height:1.45;
      background:#fafafa;
      color:#111;
    }
  </style>
</head>
<body>

  <h2>TENDENCIAS:</h2>
  <div class="opciones" data-header-index="1">
    <div class="hidden" data-default-text>- TENDENCIAS: (TEXTO PREDETERMINADO)</div>

    <label>
      <input type="checkbox" id="h1_op1" data-skip="1" data-show="#h1_children" onchange="toggleChildren(this); syncLinks(this)" />
      Activar opciones de Tendencias
    </label>

    <div id="h1_children" class="child hidden">
      <label><input type="checkbox" id="h1_op2" onchange="syncLinks(this)" /> Afebril</label>
      <label><input type="checkbox" id="h1_op3" onchange="syncLinks(this)" /> Hemodinámicamente estable</label>
      <label><input type="checkbox" id="h1_op4" onchange="syncLinks(this)" /> Dolor **/10</label>
      <label><input type="checkbox" id="h1_op5" onchange="syncLinks(this)" /> Estado general ***1.Bueno 2.Regular 3.Malo</label>
    </div>
  </div>

  <h2>PIEL:</h2>
  <div class="opciones" data-header-index="2">
    <div class="hidden" data-default-text>- PIEL: (TEXTO PREDETERMINADO)</div>

    <label>
      <input type="checkbox" id="h2_op1" data-skip="1" data-show="#h2_children" onchange="toggleChildren(this); syncLinks(this)" />
      Activar opciones de Piel
    </label>

    <div id="h2_children" class="child hidden">
      <label><input type="checkbox" id="h2_op2" onchange="syncLinks(this)" /> Íntegra</label>
      <label><input type="checkbox" id="h2_op3" onchange="syncLinks(this)" /> Sin lesiones aparentes</label>
      <label><input type="checkbox" id="h2_op4" onchange="syncLinks(this)" /> Con lesiones (describir) **</label>
      <label><input type="checkbox" id="h2_op5" onchange="syncLinks(this)" /> =>>>Eritema localizado en región indicada<<<</label>
    </div>
  </div>

  <h2>CABEZA:</h2>
  <div class="opciones" data-header-index="3">
    <div class="hidden" data-default-text>- CABEZA: (TEXTO PREDETERMINADO)</div>

    <label>
      <input type="checkbox" id="h3_op1" data-skip="1" data-show="#h3_children" onchange="toggleChildren(this); syncLinks(this)" />
      Activar opciones de Cabeza
    </label>

    <div id="h3_children" class="child hidden">
      <label><input type="checkbox" id="h3_op2" onchange="syncLinks(this)" /> Normocefálica</label>
      <label><input type="checkbox" id="h3_op3" onchange="syncLinks(this)" /> Sin signos de trauma</label>
      <label><input type="checkbox" id="h3_op4" onchange="syncLinks(this)" /> Dolor a la palpación en **</label>
    </div>
  </div>

  <h2>CAVIDAD ORAL:</h2>
  <div class="opciones" data-header-index="4">
    <div class="hidden" data-default-text>- CAVIDAD ORAL: (TEXTO PREDETERMINADO)</div>

    <label>
      <input type="checkbox" id="h4_op1" data-skip="1" data-show="#h4_children" onchange="toggleChildren(this); syncLinks(this)" />
      Activar opciones de Cavidad Oral
    </label>

    <div id="h4_children" class="child hidden">
      <label><input type="checkbox" id="h4_op2" onchange="syncLinks(this)" /> Mucosas húmedas</label>
      <label><input type="checkbox" id="h4_op3" onchange="syncLinks(this)" /> Sin lesiones orales</label>
      <label><input type="checkbox" id="h4_op4" onchange="syncLinks(this)" /> Faringe sin exudados</label>
    </div>
  </div>

  <h2>CUELLO:</h2>
  <div class="opciones" data-header-index="5">
    <div class="hidden" data-default-text>- CUELLO: (TEXTO PREDETERMINADO)</div>

    <label>
      <input type="checkbox" id="h5_op1" data-skip="1" data-show="#h5_children" onchange="toggleChildren(this); syncLinks(this)" />
      Activar opciones de Cuello
    </label>

    <div id="h5_children" class="child hidden">
      <label><input type="checkbox" id="h5_op2" onchange="syncLinks(this)" /> Sin adenopatías</label>
      <label><input type="checkbox" id="h5_op3" onchange="syncLinks(this)" /> Movilidad conservada</label>
      <label><input type="checkbox" id="h5_op4" onchange="syncLinks(this)" /> Dolor a la movilización **</label>
    </div>
  </div>

  <h2>TORAX:</h2>
  <div class="opciones" data-header-index="6">
    <div class="hidden" data-default-text>- TORAX: (TEXTO PREDETERMINADO)</div>

    <label>
      <input type="checkbox" id="h6_op1" data-skip="1" data-show="#h6_children" onchange="toggleChildren(this); syncLinks(this)" />
      Activar opciones de Tórax
    </label>

    <div id="h6_children" class="child hidden">
      <label><input type="checkbox" id="h6_op2" onchange="syncLinks(this)" /> Murmullo vesicular conservado</label>
      <label><input type="checkbox" id="h6_op3" onchange="syncLinks(this)" /> Sin ruidos agregados</label>
      <label><input type="checkbox" id="h6_op4" onchange="syncLinks(this)" /> Dolor torácico (localización) **</label>
    </div>
  </div>

  <h2>ABDOMEN:</h2>
  <div class="opciones" data-header-index="7">
    <div class="hidden" data-default-text>- ABDOMEN: (TEXTO PREDETERMINADO)</div>

    <label>
      <input type="checkbox" id="h7_op1" data-skip="1" data-show="#h7_children" onchange="toggleChildren(this); syncLinks(this)" />
      Activar opciones de Abdomen
    </label>

    <div id="h7_children" class="child hidden">
      <label><input type="checkbox" id="h7_op2" onchange="syncLinks(this)" /> Blando, depresible</label>
      <label><input type="checkbox" id="h7_op3" onchange="syncLinks(this)" /> No doloroso</label>
      <label><input type="checkbox" id="h7_op4" onchange="syncLinks(this)" /> Dolor a la palpación en **</label>
      <label><input type="checkbox" id="h7_op5" onchange="syncLinks(this)" /> Signos peritoneales ***1.No 2.Sí</label>
    </div>
  </div>

  <h2>OSTEOMUSCULAR:</h2>
  <div class="opciones" data-header-index="8">
    <div class="hidden" data-default-text>- OSTEOMUSCULAR: (TEXTO PREDETERMINADO)</div>

    <label>
      <input type="checkbox" id="h8_op1" data-skip="1" data-show="#h8_children" onchange="toggleChildren(this); syncLinks(this)" />
      Activar opciones de Osteomuscular
    </label>

    <div id="h8_children" class="child hidden">
      <label>
        <input type="checkbox" id="h8_op2" data-show="#h8_op2_children" onchange="toggleChildren(this); syncLinks(this)" />
        EXTREMIDADES SUPERIORES:
      </label>

      <div id="h8_op2_children" class="child hidden">
        <label><input type="checkbox" id="h8_op3" onchange="syncLinks(this)" /> SIN LESIONES EXTERNAS</label>
        <label><input type="checkbox" id="h8_op4" onchange="syncLinks(this)" /> ESTADO NEUROVASCULAR CONSERVADO</label>
        <label><input type="checkbox" id="h8_op5" onchange="syncLinks(this)" /> NORMOTÉRMICO</label>
        <label><input type="checkbox" id="h8_op6" onchange="syncLinks(this)" /> SIN DEFORMIDAD</label>
        <label><input type="checkbox" id="h8_op7" onchange="syncLinks(this)" /> DEFORMIDAD EN VALGO</label>
      </div>

      <label>
        <input type="checkbox" id="h8_op8" data-show="#h8_op8_children" onchange="toggleChildren(this); syncLinks(this)" />
        COLUMNA:
      </label>
      <div id="h8_op8_children" class="child hidden">
        <label><input type="checkbox" id="h8_op9" onchange="syncLinks(this)" /> Alineación conservada</label>
        <label><input type="checkbox" id="h8_op10" onchange="syncLinks(this)" /> Dolor a la palpación en **</label>
      </div>

      <label>
        <input type="checkbox" id="h8_op11" data-show="#h8_op11_children" onchange="toggleChildren(this); syncLinks(this)" />
        ARTICULACIÓN COXOFEMORAL:
      </label>
      <div id="h8_op11_children" class="child hidden">
        <label><input type="checkbox" id="h8_op12" onchange="syncLinks(this)" /> Rango de movimiento conservado</label>
        <label><input type="checkbox" id="h8_op13" onchange="syncLinks(this)" /> Dolor a la movilización **</label>
      </div>

      <label>
        <input type="checkbox" id="h8_op14" data-show="#h8_op14_children" onchange="toggleChildren(this); syncLinks(this)" />
        EXTREMIDADES INFERIORES:
      </label>
      <div id="h8_op14_children" class="child hidden">
        <label><input type="checkbox" id="h8_op15" onchange="syncLinks(this)" /> Sin edema</label>
        <label><input type="checkbox" id="h8_op16" onchange="syncLinks(this)" /> Pulsos periféricos presentes</label>
        <label><input type="checkbox" id="h8_op17" onchange="syncLinks(this)" /> Deformidad (describir) **</label>
      </div>
    </div>
  </div>

  <h2>NEUROLÓGICO:</h2>
  <div class="opciones" data-header-index="9">
    <div class="hidden" data-default-text>- NEUROLÓGICO: (TEXTO PREDETERMINADO)</div>

    <label>
      <input type="checkbox" id="h9_op1" data-skip="1" data-show="#h9_children" onchange="toggleChildren(this); syncLinks(this)" />
      Activar opciones de Neurológico
    </label>

    <div id="h9_children" class="child hidden">
      <label><input type="checkbox" id="h9_op2" onchange="syncLinks(this)" /> Glasgow **</label>
      <label><input type="checkbox" id="h9_op3" onchange="syncLinks(this)" /> Pares craneales conservados</label>
      <label><input type="checkbox" id="h9_op4" onchange="syncLinks(this)" /> Fuerza ***1/5 2/5 3/5 4/5 5/5</label>
      <label><input type="checkbox" id="h9_op5" onchange="syncLinks(this)" /> Sensibilidad conservada</label>
    </div>
  </div>

  <button onclick="updateNarrativa()">Generar Narrativa</button>
  <p id="resultado"></p>

<script>
  function toggleChildren(cb){
    const sel = cb.getAttribute("data-show");
    if(!sel) return;
    const el = document.querySelector(sel);
    if(!el) return;
    el.classList.toggle("hidden", !cb.checked);
  }

  function syncLinks(cb){
    const link = cb.getAttribute("data-link");
    if(!link) return;
    const target = document.querySelector(link);
    if(!target) return;
    target.checked = cb.checked;
    toggleChildren(target);
  }

  function buildOptionUI(){
    const labels = document.querySelectorAll("label");
    labels.forEach(label => {
      const cb = label.querySelector('input[type="checkbox"]');
      if(!cb) return;
      if(label.getAttribute("data-built") === "1") return;

      let raw = label.textContent.replace(/\s+/g, " ").trim();

      // MULTILÍNEA =>>> <<<
      const mMulti = raw.match(/=>>>([\s\S]*?)<<</);
      if(mMulti){
        cb.setAttribute("data-multiline", mMulti[1]);
        raw = raw.replace(/=>>>([\s\S]*?)<<</, "").trim();
      }

      // PARÉNTESIS CONECTAR CON
      const parens = [...raw.matchAll(/\(([^)]*)\)/g)];
      parens.forEach(p => {
        const inside = p[1];
        if(inside.toUpperCase().includes("CONECTAR CON")){
          raw = raw.replace(p[0], "").trim();
          const mm = inside.match(/CONECTAR CON\s+OPCION\s+(\d+)\s+DE\s+HEADER\s+(\d+)/i);
          if(mm){
            cb.setAttribute("data-link", "#h" + mm[2] + "_op" + mm[1]);
          }
        }
      });

      // DROPDOWN ***
      if(raw.includes("***")){
        const parts = raw.split("***");
        const prefix = parts[0];
        const rest = parts.slice(1).join("***");

        const opts = [];
        const re = /(\d+)\.([^]+?)(?=(\s+\d+\.)|$)/g;
        let match;
        while((match = re.exec(rest)) !== null) opts.push(match[2].trim());

        cb.setAttribute("data-prefix", prefix.trimEnd());
        cb.setAttribute("data-suffix", "");

        const selectEl = document.createElement("select");
        selectEl.setAttribute("data-for", cb.id);

        const empty = document.createElement("option");
        empty.value = "";
        empty.textContent = "";
        selectEl.appendChild(empty);

        opts.forEach(t => {
          const o = document.createElement("option");
          o.value = t;
          o.textContent = t;
          selectEl.appendChild(o);
        });

        label.innerHTML = "";
        label.appendChild(cb);
        label.appendChild(document.createTextNode(" " + prefix.trimEnd() + " "));
        label.appendChild(selectEl);
        label.setAttribute("data-built", "1");
        return;
      }

      // INPUT **
      if(raw.includes("**")){
        const parts = raw.split("**");
        const prefix = parts[0];
        const suffix = parts.slice(1).join("**");

        cb.setAttribute("data-prefix", prefix);
        cb.setAttribute("data-suffix", suffix);

        const input = document.createElement("input");
        input.type = "text";
        input.setAttribute("data-for", cb.id);

        label.innerHTML = "";
        label.appendChild(cb);
        label.appendChild(document.createTextNode(" " + prefix));
        label.appendChild(input);
        label.appendChild(document.createTextNode(suffix));
        label.setAttribute("data-built", "1");
        return;
      }

      // NORMAL
      label.innerHTML = "";
      label.appendChild(cb);
      label.appendChild(document.createTextNode(" " + raw));
      label.setAttribute("data-built", "1");
    });
  }

  buildOptionUI();

  function updateNarrativa(){
    const checks = document.querySelectorAll("input[type=checkbox]");
    let narrativa = "";

    const headers = document.querySelectorAll(".opciones");
    headers.forEach(h => {
      const titleEl = h.previousElementSibling;
      const titulo = titleEl ? titleEl.textContent : "";

      const headerChecks = h.querySelectorAll('input[type="checkbox"]');
      const markedMeaningful = Array.from(headerChecks).some(cb => cb.checked && cb.getAttribute("data-skip") !== "1");

      // DEFAULT si no hay selección real
      if(!markedMeaningful){
        const defEl = h.querySelector("[data-default-text]");
        if(defEl){
          narrativa += defEl.textContent.trim();
          narrativa += "\n\n";  // <-- ESPACIO ENTRE SECCIONES
        }
        return;
      }

      // Con selección real
      narrativa += "- " + titulo + " ";

      headerChecks.forEach(cb => {
        if(!cb.checked) return;
        if(cb.getAttribute("data-skip") === "1") return;

        const ml = cb.getAttribute("data-multiline");
        if(ml !== null && ml !== undefined){
          narrativa += ml;
          narrativa += "\n";   // multilínea ya trae saltos; cerramos línea
          return;
        }

        const sel = h.querySelector('select[data-for="' + cb.id + '"]');
        if(sel){
          const pref = cb.getAttribute("data-prefix") || "";
          const suf = cb.getAttribute("data-suffix") || "";
          narrativa += pref;
          if(sel.value) narrativa += sel.value;
          narrativa += suf;
          narrativa += " ";
          return;
        }

        const inp = h.querySelector('input[type="text"][data-for="' + cb.id + '"]');
        if(inp){
          const pref = cb.getAttribute("data-prefix") || "";
          const suf = cb.getAttribute("data-suffix") || "";
          narrativa += pref;
          if(inp.value) narrativa += inp.value;
          narrativa += suf;
          narrativa += " ";
          return;
        }

        const lab = cb.closest("label");
        if(lab){
          const txt = lab.textContent.replace(/\s+/g, " ").trim();
          narrativa += txt + " ";
        }
      });

      narrativa = narrativa.replace(/[ \t]+$/,"");
      narrativa += "\n\n";     // <-- ESPACIO ENTRE SECCIONES
    });

    document.getElementById("resultado").textContent = narrativa.trim();
  }
</script>

</body>
</html>