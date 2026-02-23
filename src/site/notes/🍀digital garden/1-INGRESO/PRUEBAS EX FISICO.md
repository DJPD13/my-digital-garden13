---
{"dg-publish":true,"permalink":"/digital-garden/1-ingreso/pruebas-ex-fisico/","dgPassFrontmatter":true}
---

<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Examen Físico</title>
  <style>
    body{font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial,sans-serif;line-height:1.35;margin:16px;max-width:980px}
    h2{margin:18px 0 8px}
    .group{margin:6px 0 16px 0;padding-left:10px;border-left:2px solid #ddd}
    label{display:block;margin:6px 0;cursor:pointer}
    .child{margin-left:18px;padding-left:10px;border-left:2px dashed #ddd}
    .hidden{display:none}
    input[type="text"]{margin:0 6px;min-width:220px}
    select{margin:0 6px}
    #resultado{white-space:pre-wrap;border:1px solid #ddd;padding:10px;border-radius:8px;margin-top:12px}
  </style>
</head>
<body>

  <!-- header 2: TENDENCIAS: (DEFAULT =>>> - TENDENCIAS: NORMAL <<<) -->
  <h2>TENDENCIAS:</h2>
  <div class="group" data-header="1">
    <div class="hidden" data-default-text>- TENDENCIAS: NORMAL</div>

    <label>
      <input type="checkbox" id="h1_op1" data-control="1" data-show="#h1_children" onchange="toggleChildren(this); onAnyChange(this)" />
      Activar opciones de TENDENCIAS
    </label>

    <div id="h1_children" class="child hidden"></div>
  </div>

  <!-- header 2: PIEL: (DEFAULT =>>> - PIEL: NORMAL <<<) -->
  <h2>PIEL:</h2>
  <div class="group" data-header="2">
    <div class="hidden" data-default-text>- PIEL: NORMAL</div>

    <label>
      <input type="checkbox" id="h2_op1" data-control="1" data-show="#h2_children" onchange="toggleChildren(this); onAnyChange(this)" />
      Activar opciones de PIEL
    </label>

    <div id="h2_children" class="child hidden"></div>
  </div>

  <!-- header 2: CABEZA: (DEFAULT =>>> - CABEZA: NORMAL <<<) -->
  <h2>CABEZA:</h2>
  <div class="group" data-header="3">
    <div class="hidden" data-default-text>- CABEZA: NORMAL</div>

    <label>
      <input type="checkbox" id="h3_op1" data-control="1" data-show="#h3_children" onchange="toggleChildren(this); onAnyChange(this)" />
      Activar opciones de CABEZA
    </label>

    <div id="h3_children" class="child hidden"></div>
  </div>

  <!-- header 2: CAVIDAD ORAL: (DEFAULT =>>> - CAVIDAD ORAL: NORMAL <<<) -->
  <h2>CAVIDAD ORAL:</h2>
  <div class="group" data-header="4">
    <div class="hidden" data-default-text>- CAVIDAD ORAL: NORMAL</div>

    <label>
      <input type="checkbox" id="h4_op1" data-control="1" data-show="#h4_children" onchange="toggleChildren(this); onAnyChange(this)" />
      Activar opciones de CAVIDAD ORAL
    </label>

    <div id="h4_children" class="child hidden"></div>
  </div>

  <!-- header 2: CUELLO: (DEFAULT =>>> - CUELLO: NORMAL <<<) -->
  <h2>CUELLO:</h2>
  <div class="group" data-header="5">
    <div class="hidden" data-default-text>- CUELLO: NORMAL</div>

    <label>
      <input type="checkbox" id="h5_op1" data-control="1" data-show="#h5_children" onchange="toggleChildren(this); onAnyChange(this)" />
      Activar opciones de CUELLO
    </label>

    <div id="h5_children" class="child hidden"></div>
  </div>

  <!-- header 2: TORAX: (DEFAULT =>>> - TORAX: NORMAL <<<) -->
  <h2>TORAX:</h2>
  <div class="group" data-header="6">
    <div class="hidden" data-default-text>- TORAX: NORMAL</div>

    <label>
      <input type="checkbox" id="h6_op1" data-control="1" data-show="#h6_children" onchange="toggleChildren(this); onAnyChange(this)" />
      Activar opciones de TORAX
    </label>

    <div id="h6_children" class="child hidden"></div>
  </div>

  <!-- header 2: ABDOMEN: (DEFAULT =>>> - ABDOMEN: NORMAL <<<) -->
  <h2>ABDOMEN:</h2>
  <div class="group" data-header="7">
    <div class="hidden" data-default-text>- ABDOMEN: NORMAL</div>

    <label>
      <input type="checkbox" id="h7_op1" data-control="1" data-show="#h7_children" onchange="toggleChildren(this); onAnyChange(this)" />
      Activar opciones de ABDOMEN
    </label>

    <div id="h7_children" class="child hidden"></div>
  </div>

  <!-- header 2: OSTEOMUSCULAR: (DEFAULT =>>> - OSTEOMUSCULAR: NORMAL <<<) -->
  <h2>OSTEOMUSCULAR:</h2>
  <div class="group" data-header="8">
    <div class="hidden" data-default-text>- OSTEOMUSCULAR: NORMAL</div>

    <label>
      <input type="checkbox" id="h8_op1" data-control="1" data-show="#h8_children" onchange="toggleChildren(this); onAnyChange(this)" />
      Activar opciones de OSTEOMUSCULAR
    </label>

    <div id="h8_children" class="child hidden">
      <label>
        <input type="checkbox" id="h8_op2" data-show="#h8_op2_children" onchange="toggleChildren(this); onAnyChange(this)" />
        EXTREMIDADES SUPERIORES:
      </label>

      <div id="h8_op2_children" class="child hidden">
        <label><input type="checkbox" id="h8_op3" onchange="onAnyChange(this)" /> SIN LESIONES EXTERNAS</label>
        <label><input type="checkbox" id="h8_op4" onchange="onAnyChange(this)" /> ESTADO NEUROVASCULAR CONSERVADO</label>
        <label><input type="checkbox" id="h8_op5" onchange="onAnyChange(this)" /> NORMOTERMICO</label>
        <label><input type="checkbox" id="h8_op6" onchange="onAnyChange(this)" /> SIN DEFORMIDAD</label>
        <label><input type="checkbox" id="h8_op7" onchange="onAnyChange(this)" /> DEFORMIDAD EN VALGO</label>
      </div>

      <label><input type="checkbox" id="h8_op8" onchange="onAnyChange(this)" /> COLUMNA:</label>
      <label><input type="checkbox" id="h8_op9" onchange="onAnyChange(this)" /> ARTICULACIÒN COXOFEMORAL:</label>
      <label><input type="checkbox" id="h8_op10" onchange="onAnyChange(this)" /> EXTREMIDADES INFERIORES:</label>
    </div>
  </div>

  <!-- header 2: NEUROLOGICO: (DEFAULT =>>> - NEUROLOGICO: NORMAL <<<) -->
  <h2>NEUROLOGICO:</h2>
  <div class="group" data-header="9">
    <div class="hidden" data-default-text>- NEUROLOGICO: NORMAL</div>

    <label>
      <input type="checkbox" id="h9_op1" data-control="1" data-show="#h9_children" onchange="toggleChildren(this); onAnyChange(this)" />
      Activar opciones de NEUROLOGICO
    </label>

    <div id="h9_children" class="child hidden"></div>
  </div>

  <button onclick="updateNarrativa()">Generar Narrativa</button>
  <p id="resultado"></p>

<script>
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

    // también limpia inputs/selects asociados
    const innerInputs = container.querySelectorAll('input[type="text"]');
    innerInputs.forEach(i => i.value = "");
    const innerSelects = container.querySelectorAll('select');
    innerSelects.forEach(s => s.value = "");
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

  // ------- Parser: (CONECTAR CON...), ** input, *** dropdown, =>>> <<< multilínea -------
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

  // ---------------- updateNarrativa() ----------------
  function updateNarrativa(){
    const checks = document.querySelectorAll("input[type=checkbox]");
    let narrativa = "";

    for(let h=1; h<=9; h++){
      const group = document.querySelector('.group[data-header="'+h+'"]');
      if(!group) continue;

      const defaultEl = group.querySelector("[data-default-text]");
      const titleEl = group.previousElementSibling;
      const titulo = titleEl ? titleEl.textContent : "";

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
        if(ml !== null && ml !== undefined){
          narrativa += ml;
          if(!narrativa.endsWith("\n")) narrativa += "\n";
          return;
        }

        const sel = group.querySelector('select[data-for="'+cb.id+'"]');
        if(sel){
          const pref = cb.getAttribute("data-prefix") || "";
          const suf = cb.getAttribute("data-suffix") || "";
          narrativa += pref;
          if(sel.value) narrativa += sel.value;
          narrativa += suf;
          narrativa += " ";
          return;
        }

        const inp = group.querySelector('input[type="text"][data-for="'+cb.id+'"]');
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
      if(!narrativa.endsWith("\n")) narrativa += "\n";
    }

    document.getElementById("resultado").textContent = narrativa.trim();
  }
</script>

</body>
</html>