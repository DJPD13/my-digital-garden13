---
{"dg-publish":true,"permalink":"/digital-garden/2-examenes-fisicos/prueba-examen-fisico-2/","dgPassFrontmatter":true}
---

<!DOCTYPE html>
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Examen Físico – Anidamiento exacto</title>
  <style>
    body{font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial,sans-serif;line-height:1.35;margin:16px;max-width:1000px;background:#fcfcfc}
    h2{margin:24px 0 8px;border-bottom:1px solid #ccc;padding-bottom:3px;font-weight:600}
    .group{margin:0 0 26px 0;padding-left:12px;border-left:3px solid #5f8ab0}
    label{display:block;margin:6px 0;cursor:pointer}
    .child{margin-left:24px;padding-left:12px;border-left:2px dashed #b0c8dd}
    .hidden{display:none}
    input[type="text"]{margin:0 8px 0 4px;min-width:210px;padding:3px 6px;border:1px solid #aaa;border-radius:5px}
    select{margin:0 8px 0 4px;padding:3px 6px;border-radius:5px}
    button{background:#1e4468;color:white;border:none;font-size:1.2rem;padding:8px 30px;border-radius:40px;margin:25px 0 12px;cursor:pointer;font-weight:600}
    button:hover{background:#0f2b44}
    #resultado{white-space:pre-wrap;border:2px solid #b4c9e2;background:#f3f7fd;padding:16px;border-radius:16px;margin-top:18px;font-family:'Courier New',monospace}
    .marca-agua{color:#5b7c9b;margin:-5px 0 8px 15px;font-style:italic}
  </style>
</head>
<body>
  <!-- CABECERAS PRINCIPALES (9) CON ESPACIADO ENTRE ELLAS PERO SIN SALTO DENTRO DE SUS OPCIONES -->
  <h2>TENDENCIAS:</h2>
  <div class="group" data-header="1">
    <div class="hidden" data-default-text="- TENDENCIAS: NORMAL"></div>
    <label>
      <input type="checkbox" id="h1_op1" data-control="1" data-show="#h1_children" onchange="toggleChildren(this); onAnyChange(this)" />
      ⚡ Activar TENDENCIAS
    </label>
    <div id="h1_children" class="child hidden"></div>
  </div>

  <h2>PIEL:</h2>
  <div class="group" data-header="2">
    <div class="hidden" data-default-text="- PIEL: NORMAL"></div>
    <label>
      <input type="checkbox" id="h2_op1" data-control="1" data-show="#h2_children" onchange="toggleChildren(this); onAnyChange(this)" />
      🩹 Activar PIEL
    </label>
    <div id="h2_children" class="child hidden"></div>
  </div>

  <h2>CABEZA:</h2>
  <div class="group" data-header="3">
    <div class="hidden" data-default-text="- CABEZA: NORMAL"></div>
    <label>
      <input type="checkbox" id="h3_op1" data-control="1" data-show="#h3_children" onchange="toggleChildren(this); onAnyChange(this)" />
      🧠 Activar CABEZA
    </label>
    <div id="h3_children" class="child hidden"></div>
  </div>

  <h2>CAVIDAD ORAL:</h2>
  <div class="group" data-header="4">
    <div class="hidden" data-default-text="- CAVIDAD ORAL: NORMAL"></div>
    <label>
      <input type="checkbox" id="h4_op1" data-control="1" data-show="#h4_children" onchange="toggleChildren(this); onAnyChange(this)" />
      👄 Activar CAVIDAD ORAL
    </label>
    <div id="h4_children" class="child hidden"></div>
  </div>

  <h2>CUELLO:</h2>
  <div class="group" data-header="5">
    <div class="hidden" data-default-text="- CUELLO: NORMAL"></div>
    <label>
      <input type="checkbox" id="h5_op1" data-control="1" data-show="#h5_children" onchange="toggleChildren(this); onAnyChange(this)" />
      🫀 Activar CUELLO
    </label>
    <div id="h5_children" class="child hidden"></div>
  </div>

  <h2>TÓRAX:</h2>
  <div class="group" data-header="6">
    <div class="hidden" data-default-text="- TORAX: NORMAL"></div>
    <label>
      <input type="checkbox" id="h6_op1" data-control="1" data-show="#h6_children" onchange="toggleChildren(this); onAnyChange(this)" />
      🫁 Activar TÓRAX
    </label>
    <div id="h6_children" class="child hidden"></div>
  </div>

  <h2>ABDOMEN:</h2>
  <div class="group" data-header="7">
    <div class="hidden" data-default-text="- ABDOMEN: NORMAL"></div>
    <label>
      <input type="checkbox" id="h7_op1" data-control="1" data-show="#h7_children" onchange="toggleChildren(this); onAnyChange(this)" />
      🩺 Activar ABDOMEN
    </label>
    <div id="h7_children" class="child hidden"></div>
  </div>

  <h2>OSTEOMUSCULAR:</h2>
  <div class="group" data-header="8">
    <div class="hidden" data-default-text="- OSTEOMUSCULAR: NORMAL"></div>
    <label>
      <input type="checkbox" id="h8_op1" data-control="1" data-show="#h8_children" onchange="toggleChildren(this); onAnyChange(this)" />
      🦴 Activar OSTEOMUSCULAR
    </label>
    <div id="h8_children" class="child hidden">
      <!-- Subopciones de OSTEOMUSCULAR (con anidamiento real) -->
      <label><input type="checkbox" id="h8_op2" data-show="#h8_op2_children" onchange="toggleChildren(this); onAnyChange(this)" /> 🦾 EXTREMIDADES SUPERIORES:</label>
      <div id="h8_op2_children" class="child hidden">
        <label><input type="checkbox" id="h8_op3" onchange="onAnyChange(this)" /> SIN LESIONES EXTERNAS</label>
        <label><input type="checkbox" id="h8_op4" onchange="onAnyChange(this)" /> ESTADO NEUROVASCULAR CONSERVADO</label>
        <label><input type="checkbox" id="h8_op5" onchange="onAnyChange(this)" /> NORMOTÉRMICO</label>
        <label><input type="checkbox" id="h8_op6" onchange="onAnyChange(this)" /> SIN DEFORMIDAD</label>
        <label><input type="checkbox" id="h8_op7" onchange="onAnyChange(this)" /> DEFORMIDAD EN VALGO</label>
      </div>

      <label><input type="checkbox" id="h8_op8" data-show="#h8_op8_children" onchange="toggleChildren(this); onAnyChange(this)" /> 📐 COLUMNA:</label>
      <div id="h8_op8_children" class="child hidden">
        <label><input type="checkbox" id="h8_op9" onchange="onAnyChange(this)" /> SIN DOLOR A LA PALPACIÓN</label>
        <label><input type="checkbox" id="h8_op10" onchange="onAnyChange(this)" /> CIFOSIS</label>
        <label><input type="checkbox" id="h8_op11" onchange="onAnyChange(this)" /> ESCOLIOSIS **ÁNGULO DE ** GRADOS</label>
      </div>

      <label><input type="checkbox" id="h8_op12" data-show="#h8_op12_children" onchange="toggleChildren(this); onAnyChange(this)" /> 🦵 ARTICULACIÓN COXOFEMORAL:</label>
      <div id="h8_op12_children" class="child hidden">
        <label><input type="checkbox" id="h8_op13" onchange="onAnyChange(this)" /> SIN ALTERACIONES</label>
        <label><input type="checkbox" id="h8_op14" onchange="onAnyChange(this)" /> DOLOR A LA MOVILIZACIÓN ***1.LEVE 2.MODERADO 3.SEVERO</label>
      </div>

      <label><input type="checkbox" id="h8_op15" data-show="#h8_op15_children" onchange="toggleChildren(this); onAnyChange(this)" /> 🦶 EXTREMIDADES INFERIORES:</label>
      <div id="h8_op15_children" class="child hidden">
        <label><input type="checkbox" id="h8_op16" onchange="onAnyChange(this)" data-link="#h8_op2" /> (CONECTAR CON OPCION 2 DE HEADER 8) → [vínculo]</label>
        <label><input type="checkbox" id="h8_op17" onchange="onAnyChange(this)" data-link="#h6_op1" /> EDEMA + (CONECTAR CON OPCION 1 DE HEADER 6)</label>
        <label><input type="checkbox" id="h8_op18" onchange="onAnyChange(this)" /> PULSOS PEDIOS PALPABLES</label>
        <label><input type="checkbox" id="h8_op19" onchange="onAnyChange(this)" /> VARICES (=>>>Várices de gran tamaño en miembro inferior izquierdo, con edema asociado. Piel circundante con signos de estasis.<<<)</label>
      </div>
    </div>
  </div>

  <h2>NEUROLÓGICO:</h2>
  <div class="group" data-header="9">
    <div class="hidden" data-default-text="- NEUROLOGICO: NORMAL"></div>
    <label>
      <input type="checkbox" id="h9_op1" data-control="1" data-show="#h9_children" onchange="toggleChildren(this); onAnyChange(this)" />
      🧠 Activar NEUROLÓGICO
    </label>
    <div id="h9_children" class="child hidden">
      <label><input type="checkbox" id="h9_op2" data-show="#h9_op2_children" onchange="toggleChildren(this); onAnyChange(this)" /> ESTADO DE CONCIENCIA:</label>
      <div id="h9_op2_children" class="child hidden">
        <label><input type="checkbox" id="h9_op3" onchange="onAnyChange(this)" /> ALERTA</label>
        <label><input type="checkbox" id="h9_op4" onchange="onAnyChange(this)" /> SOMNOLIENTO</label>
        <label><input type="checkbox" id="h9_op5" onchange="onAnyChange(this)" /> CONFUSO</label>
        <label><input type="checkbox" id="h9_op6" onchange="onAnyChange(this)" /> INCONSCIENTE **GLASGOW: **</label>
      </div>
      <label><input type="checkbox" id="h9_op7" data-show="#h9_op7_children" onchange="toggleChildren(this); onAnyChange(this)" /> MOTILIDAD:</label>
      <div id="h9_op7_children" class="child hidden">
        <label><input type="checkbox" id="h9_op8" onchange="onAnyChange(this)" /> CONSERVADA</label>
        <label><input type="checkbox" id="h9_op9" onchange="onAnyChange(this)" /> DEBILIDAD EN ***1.HEMICUE尔PO DERECHO 2.HEMICUE尔PO IZQUIERDO 3.MIEMBRO SUPERIOR 4.MIEMBRO INFERIOR</label>
      </div>
      <label><input type="checkbox" id="h9_op10" data-show="#h9_op10_children" onchange="toggleChildren(this); onAnyChange(this)" /> SENSIBILIDAD:</label>
      <div id="h9_op10_children" class="child hidden">
        <label><input type="checkbox" id="h9_op11" onchange="onAnyChange(this)" /> CONSERVADA</label>
        <label><input type="checkbox" id="h9_op12" onchange="onAnyChange(this)" /> PARESTESIAS EN **LOCALIZACIÓN: **</label>
      </div>
      <label><input type="checkbox" id="h9_op13" data-show="#h9_op13_children" onchange="toggleChildren(this); onAnyChange(this)" /> REFLEJOS:</label>
      <div id="h9_op13_children" class="child hidden">
        <label><input type="checkbox" id="h9_op14" onchange="onAnyChange(this)" /> NORMORREFLEXIA</label>
        <label><input type="checkbox" id="h9_op15" onchange="onAnyChange(this)" /> HIPORREFLEXIA</label>
        <label><input type="checkbox" id="h9_op16" onchange="onAnyChange(this)" /> HIPERRREFLEXIA</label>
      </div>
    </div>
  </div>

  <button onclick="updateNarrativa()">📋 Generar Narrativa</button>
  <p id="resultado"></p>

  <script>
    // Funciones de toggle y limpieza (exactamente como en el ejemplo correcto)
    function toggleChildren(cb){
      const sel = cb.getAttribute("data-show");
      if(!sel) return;
      const el = document.querySelector(sel);
      if(!el) return;

      if(cb.checked){
        el.classList.remove("hidden");
      }else{
        uncheckDescendants(el);
        el.classList.add("hidden");
      }
    }

    function uncheckDescendants(container){
      const innerChecks = container.querySelectorAll('input[type="checkbox"]');
      innerChecks.forEach(c => {
        c.checked = false;
        const link = c.getAttribute("data-link");
        if(link){
          const tgt = document.querySelector(link);
          if(tgt) tgt.checked = false;
        }
        const sel = c.getAttribute("data-show");
        if(sel){
          const el = document.querySelector(sel);
          if(el){
            uncheckDescendants(el);
            el.classList.add("hidden");
          }
        }
      });
      const innerInputs = container.querySelectorAll('input[type="text"]');
      innerInputs.forEach(i => i.value = "");
      const innerSelects = container.querySelectorAll('select');
      innerSelects.forEach(s => s.selectedIndex = 0);
    }

    function onAnyChange(cb){
      const link = cb.getAttribute("data-link");
      if(link){
        const target = document.querySelector(link);
        if(target){
          target.checked = cb.checked;
          toggleChildren(target);
        }
      }
    }

    // ------- parseo de **, ***, =>>> y (CONECTAR CON) -------
    function stripConnectParensAndSetLink(raw, cb){
      const parens = [...raw.matchAll(/\(([^)]*)\)/g)];
      parens.forEach(p => {
        const inside = p[1];
        if(inside.toUpperCase().includes("CONECTAR CON")){
          raw = raw.replace(p[0], "").trim();
          const mm = inside.match(/CONECTAR CON\s+OPCION\s+(\d+)\s+DE\s+HEADER\s+(\d+)/i);
          if(mm){
            const X = mm[1];
            const Y = mm[2];
            cb.setAttribute("data-link", "#h" + Y + "_op" + X);
          }
        }
      });
      return raw;
    }

    function buildOptionUI(){
      const labels = document.querySelectorAll("label");
      labels.forEach(label => {
        const cb = label.querySelector('input[type="checkbox"]');
        if(!cb) return;
        if(label.getAttribute("data-built")==="1") return;

        let raw = label.textContent.replace(/\s+/g, " ").trim();

        // Multilínea =>>> <<<
        const mMulti = raw.match(/=>>>([\s\S]*?)<<</);
        if(mMulti){
          cb.setAttribute("data-multiline", mMulti[1]);
          raw = raw.replace(/=>>>([\s\S]*?)<<</, "").trim();
        }

        raw = stripConnectParensAndSetLink(raw, cb);

        // Dropdown ***
        if(raw.includes("***")){
          const parts = raw.split("***");
          const prefix = parts[0];
          const rest = parts.slice(1).join("***");

          const opts = [];
          const re = /(\d+)\.([^]+?)(?=(\s+\d+\.)|$)/g;
          let match;
          while((match = re.exec(rest)) !== null){
            opts.push(match[2].trim());
          }

          cb.setAttribute("data-prefix", prefix);
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
          label.setAttribute("data-built","1");
          return;
        }

        // Input **
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
          label.setAttribute("data-built","1");
          return;
        }

        // Normal
        label.innerHTML = "";
        label.appendChild(cb);
        label.appendChild(document.createTextNode(" " + raw));
        label.setAttribute("data-built","1");
      });
    }

    buildOptionUI();

    // ---------------- Narrativa final ----------------
    function updateNarrativa(){
      let narrativa = "";
      for(let h=1; h<=9; h++){
        const group = document.querySelector('.group[data-header="'+h+'"]');
        if(!group) continue;

        const defaultEl = group.querySelector("[data-default-text]");
        const titleEl = group.previousElementSibling;
        const titulo = titleEl ? titleEl.textContent.replace(":","") : "";

        const headerChecks = group.querySelectorAll('input[type="checkbox"]');

        let hasReal = false;
        headerChecks.forEach(cb => {
          if(cb.checked && cb.getAttribute("data-control")!=="1"){
            hasReal = true;
          }
        });

        if(!hasReal){
          if(defaultEl){
            narrativa += defaultEl.textContent;
            if(!narrativa.endsWith("\n")) narrativa += "\n";
          }
          continue;
        }

        narrativa += "- " + titulo + " ";

        headerChecks.forEach(cb => {
          if(!cb.checked) return;
          if(cb.getAttribute("data-control")==="1") return;

          const ml = cb.getAttribute("data-multiline");
          if(ml !== null){
            narrativa += ml;
            if(!narrativa.endsWith("\n")) narrativa += "\n";
            return;
          }

          const sel = document.querySelector('select[data-for="'+cb.id+'"]');
          if(sel){
            const pref = cb.getAttribute("data-prefix") || "";
            const suf = cb.getAttribute("data-suffix") || "";
            narrativa += pref;
            if(sel.value) narrativa += sel.value;
            narrativa += suf + " ";
            return;
          }

          const inp = document.querySelector('input[type="text"][data-for="'+cb.id+'"]');
          if(inp){
            const pref = cb.getAttribute("data-prefix") || "";
            const suf = cb.getAttribute("data-suffix") || "";
            narrativa += pref;
            if(inp.value) narrativa += inp.value;
            narrativa += suf + " ";
            return;
          }

          const lab = cb.closest("label");
          if(lab){
            const txt = lab.textContent.replace(/\s+/g, " ").trim();
            narrativa += txt + " ";
          }
        });

        narrativa = narrativa.replace(/[ \t]+$/,"");
        if(!narrativa.endsWith("\n")) narrativa += "\n";
      }
      document.getElementById("resultado").textContent = narrativa.trim();
    }
  </script>
</body>
</html>
