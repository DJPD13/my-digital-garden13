---
{"dg-publish":true,"permalink":"/digital-garden/1-ea-13/exxxxx/","dgPassFrontmatter":true}
---

<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Narrativa por Headers</title>
  <style>
    body { font-family: Arial, sans-serif; line-height: 1.35; padding: 16px; }
    .topbar { margin-bottom: 14px; padding: 10px 12px; border: 1px solid #ddd; border-radius: 8px; }
    .header-block { margin: 14px 0 18px; padding: 12px; border: 1px solid #e3e3e3; border-radius: 10px; }
    .opt { display: block; margin: 6px 0; }
    .opt input[type="text"] { width: 260px; max-width: 100%; }
    .opt select { max-width: 100%; }
    #resultado { white-space: pre-wrap; border: 1px solid #ddd; padding: 12px; border-radius: 10px; margin-top: 12px; }
    button { margin-top: 10px; padding: 10px 12px; border-radius: 10px; border: 1px solid #ccc; cursor: pointer; }
  </style>
</head>
<body>

  <div class="topbar">
    <label class="opt">
      <input type="checkbox" id="toggleHeaders" checked>
      Incluir headers en la narrativa
    </label>

    <button onclick="updateNarrativa()">Generar Narrativa</button>
  </div>

  <div id="formulario"></div>

  <p id="resultado"></p>

<script>
/* =========================
   RAW: TU TEXTO (PEGADO)
   ========================= */
const RAW = `header 1:  .
NO PATOLOGICO =>>>  
 PACIENTE EN BUENAS CONDICIONES GENERALES, ALERTA, CONCIENTE, AFEBRIL, HIDRATADO
- PIEL: SIN LESIONES.
- NORMOCEFALO, CONJUNTIVAS NORMOCROMICAS, ESCLERAS, ANICTERICAS, ISOCORIA NORMOREACTIVA, MOVIMIENTOS OCULARES NORMALES; MUCOSA NASAL NORMAL; MUCOSA ORAL HUMEDA, OROFARINGE LIMPIA; OTOSCOPIA BILATERAL NORMAL.
- CUELLO: MOVIL, NO DOLOROSO, NO SE PALPAN MASAS NI ADENOMEGALIAS.
- TORAX: SIMETRICO, EXPANSIBILIDAD NORMAL, SIN RETRACCIONES, PERCUSION NORMAL.RUIDOS CARDIACOS RITMICOS, NO AUSCULTO SOPLOS; MURMULLO VESICULAR CONSERVADO, NO SE AUSCULTAN AGREGADOS.
- ABDOMEN BLANDO, NO DOLOROSO A LA PALPACION, PERISTALSIS PRESENTE, NO SE PALPAN MASAS NI VISCEROMEGALIAS, SIN SIGNOS DE IRRITACION PERITONEAL.
- GENITOURINARIO NO EVALUADO. 
- EXTREMIDADES SIMETRICAS, SIN EDEMAS, MOVILES, PERFUSION DISTAL MENOR A 2 SEGUNDOS, PULSOS DISTALES PRESENTES.
- OSTEOMUCULAR: SIN DEFORMIDADES, ARCOS DE MOVILIDAD CONSERVADOS.
- NEUROLOGICO: SIN DEFICIT MOTOR NI SENSITIVO APARENTE, FUERZA 5/5 EN 4 EXTREMIDADES, SENSIBILIDAD CONSERVADA, NO SIGNOS MENINGEOS, NO FOCALIZACIÓN
<<<
PATOLOGICO
header 2:  PIEL =>>> PIEL: SIN LESIONES<<< //
PETEQUIAS EN **
MACULAS ERITEMATOSAS EN ** 
header 3:  CABEZA Y CUELLO: =>>>NORMOCEFALO, CONJUNTIVAS NORMOCROMICAS, ESCLERAS ANICTERICAS, ISOCORIA NORMOREACTIVA, MOVIMIENTOS OCULARES NORMALES; MUCOSA NASAL NORMAL; MUCOSA ORAL HUMEDA, OROFARINGE LIMPIA; OTOSCOPIA BILATERAL NORMAL.<<<
ESCLERAS ICTERICAS
MUCOSA ORAL SECA SIN LESIONES
CONGESTIÓN CONJUNTIVAL SIN SECRECIÓN PURULENTA O MUCOSA
DOLOR EN ANGULO MANDIBULAR **`;

/* =========================
   HELPERS
   ========================= */
function stripConnectParens(s) {
  return s.replace(/\(([^)]*CONECTAR CON[^)]*)\)/gi, "").replace(/\s{2,}/g, " ").trim();
}
function parseLinkTarget(s) {
  const m = s.match(/\(\s*CONECTAR\s+CON\s+OPCION\s+(\d+)\s+DE\s+HEADER\s+(\d+)\s*\)/i);
  if (!m) return null;
  return { x: Number(m[1]), y: Number(m[2]) };
}
function parseDefaultFromHeaderTitle(titleRaw) {
  const m = titleRaw.match(/\(\s*DEFAULT\s*=>>>\s*([\s\S]*?)\s*<<<\s*\)\s*$/i);
  if (!m) return { title: titleRaw.trim(), defText: null };
  const defText = m[1];
  const title = titleRaw.replace(m[0], "").trim();
  return { title, defText };
}
function makeHeaderTag(n) {
  const level = Math.min(Math.max(n, 1), 6);
  return "h" + level;
}

/* =========================
   OPTION PARSER (una línea)
   ========================= */
function parseOptionLineSingleLine(lineRaw) {
  const lineWithLink = lineRaw.trimEnd();
  const link = parseLinkTarget(lineWithLink);
  let cleaned = stripConnectParens(lineWithLink);

  // Dropdown ***
  let dropdown = null;
  if (cleaned.includes("***")) {
    const idx = cleaned.indexOf("***");
    const before = cleaned.slice(0, idx);
    const after = cleaned.slice(idx + 3);

    const opts = [];
    const re = /(\d+)\.([^]+?)(?=(?:\s+\d+\.)|$)/g;
    let mm;
    while ((mm = re.exec(after)) !== null) {
      const val = mm[2].trim();
      if (val) opts.push(val);
    }

    dropdown = { before, options: opts, after: "" };
  }

  // Input **
  let textInput = null;
  if (!dropdown && cleaned.includes("**")) {
    const idx = cleaned.indexOf("**");
    textInput = { before: cleaned.slice(0, idx), after: cleaned.slice(idx + 2) };
  }

  let labelParts, narrativeParts;

  if (dropdown) {
    labelParts = { type: "dropdown", before: dropdown.before, after: dropdown.after, options: dropdown.options };
    narrativeParts = { type: "dropdown", before: dropdown.before, after: dropdown.after };
  } else if (textInput) {
    labelParts = { type: "text", before: textInput.before, after: textInput.after };
    narrativeParts = { type: "text", before: textInput.before, after: textInput.after };
  } else {
    labelParts = { type: "plain", text: cleaned.trim() };
    narrativeParts = { type: "plain", text: cleaned.trim() };
  }

  return { raw: lineRaw, link, labelParts, narrativeParts, multilineText: null };
}

/* =========================
   HEADER PARSER (multilínea real)
   - Opciones con =>>> ... <<< pueden abarcar varias líneas
   - Si header trae =>>> ... <<< sin "DEFAULT", se usa como DEFAULT implícito
   ========================= */
function parseHeaders(raw) {
  const lines = raw.split(/\r?\n/);

  const headers = [];
  let current = null;

  let i = 0;
  while (i < lines.length) {
    const line = lines[i];

    const headerMatch = line.match(/^\s*header\s+(\d+)\s*:\s*(.*)\s*$/i);
    if (headerMatch) {
      const n = Number(headerMatch[1]);
      const titleRaw = headerMatch[2] || "";

      const { title: titleNoDefault, defText: defFormal } = parseDefaultFromHeaderTitle(titleRaw);

      // DEFAULT implícito en la línea del header (=>>> ... <<<)
      let titleDisplay = titleNoDefault;
      let defImplicit = null;

      const start = titleDisplay.indexOf("=>>>");
      const end = titleDisplay.indexOf("<<<");
      if (start !== -1 && end !== -1 && end > start) {
        defImplicit = titleDisplay.slice(start + 4, end);
        titleDisplay = (titleDisplay.slice(0, start) + titleDisplay.slice(end + 3)).trim();
      }

      titleDisplay = titleDisplay.replace(/\s*\/\/\s*$/, "").trim();

      current = {
        n,
        titleDisplay,
        defaultText: (defFormal != null ? defFormal : defImplicit),
        options: []
      };
      headers.push(current);
      i++;
      continue;
    }

    if (!current || line.trim() === "") {
      i++;
      continue;
    }

    // Opciones con =>>> ... <<< (pueden ser varias líneas)
    const idxStart = line.indexOf("=>>>");
    if (idxStart !== -1) {
      // Caso cierre en misma línea
      const idxEndSame = line.indexOf("<<<", idxStart + 4);
      if (idxEndSame !== -1) {
        const before = line.slice(0, idxStart);
        const inner = line.slice(idxStart + 4, idxEndSame);
        const after = line.slice(idxEndSame + 3);

        const base = parseOptionLineSingleLine((before + after).trim());
        base.multilineText = inner; // tal cual
        current.options.push(base);
        i++;
        continue;
      }

      // Caso cierre en línea futura
      const before = line.slice(0, idxStart);
      let collected = line.slice(idxStart + 4);
      collected += "\n";

      i++;
      while (i < lines.length) {
        const l2 = lines[i];
        const idxEnd = l2.indexOf("<<<");
        if (idxEnd !== -1) {
          collected += l2.slice(0, idxEnd);
          i++; // consume línea que cierra
          break;
        } else {
          collected += l2 + "\n";
          i++;
        }
      }

      const base = parseOptionLineSingleLine(before.trim());
      base.multilineText = collected; // tal cual
      current.options.push(base);
      continue;
    }

    // Opción normal
    current.options.push(parseOptionLineSingleLine(line));
    i++;
  }

  // IDs obligatorios id="h<Y>_op<X>"
  headers.forEach(h => {
    h.options.forEach((op, idx) => {
      op.optionIndex = idx + 1;
      op.id = `h${h.n}_op${op.optionIndex}`;
      if (op.link) op.linkTargetId = `h${op.link.y}_op${op.link.x}`;
    });
  });

  return headers;
}

/* =========================
   RENDER
   ========================= */
const headersData = parseHeaders(RAW);
const form = document.getElementById("formulario");

function render() {
  form.innerHTML = "";

  headersData.forEach(h => {
    const block = document.createElement("div");
    block.className = "header-block";
    block.dataset.headerN = String(h.n);

    const tag = makeHeaderTag(h.n);
    const hdr = document.createElement(tag);
    hdr.textContent = h.titleDisplay;
    block.appendChild(hdr);

    h.options.forEach(op => {
      const label = document.createElement("label");
      label.className = "opt";

      const cb = document.createElement("input");
      cb.type = "checkbox";
      cb.id = op.id;

      if (op.linkTargetId) cb.setAttribute("data-link", op.linkTargetId);

      label.appendChild(cb);
      label.appendChild(document.createTextNode(" "));

      if (op.labelParts.type === "plain") {
        label.appendChild(document.createTextNode(op.labelParts.text));
      } else if (op.labelParts.type === "text") {
        label.appendChild(document.createTextNode(op.labelParts.before));
        const inp = document.createElement("input");
        inp.type = "text";
        inp.id = op.id + "_txt";
        label.appendChild(inp);
        label.appendChild(document.createTextNode(op.labelParts.after));
      } else if (op.labelParts.type === "dropdown") {
        label.appendChild(document.createTextNode(op.labelParts.before));
        const sel = document.createElement("select");
        sel.id = op.id + "_sel";
        const empty = document.createElement("option");
        empty.value = "";
        empty.textContent = "";
        sel.appendChild(empty);
        (op.labelParts.options || []).forEach(v => {
          const o = document.createElement("option");
          o.value = v;
          o.textContent = v;
          sel.appendChild(o);
        });
        label.appendChild(sel);
        label.appendChild(document.createTextNode(op.labelParts.after || ""));
      }

      block.appendChild(label);
    });

    form.appendChild(block);
  });

  // Conexiones
  const linkChecks = document.querySelectorAll('input[type="checkbox"][data-link]');
  linkChecks.forEach(cb => {
    cb.addEventListener("change", () => {
      const targetId = cb.getAttribute("data-link");
      const target = document.getElementById(targetId);
      if (!target) return;
      target.checked = cb.checked;
    });
  });
}

render();

/* =========================
   updateNarrativa (OBLIGATORIO)
   ========================= */
function updateNarrativa() {
  const checks = document.querySelectorAll("input[type=checkbox]");

  const includeHeaders = !!document.getElementById("toggleHeaders")?.checked;
  let narrativa = "";

  headersData.forEach(h => {
    const marked = h.options.filter(op => {
      const cb = document.getElementById(op.id);
      return cb && cb.checked;
    });

    // DEFAULT por header
    if (marked.length === 0) {
      if (h.defaultText != null && String(h.defaultText).length > 0) {
        if (narrativa && !narrativa.endsWith("\n")) narrativa += "\n";
        narrativa += String(h.defaultText);
        if (!narrativa.endsWith("\n")) narrativa += "\n";
      }
      return;
    }

    // Header title (según toggleHeaders)
    if (includeHeaders) {
      if (h.titleDisplay && h.titleDisplay.trim() !== "") {
        if (narrativa && !narrativa.endsWith("\n")) narrativa += "\n";
        narrativa += h.titleDisplay.trim() + "\n";
      }
    }

    // Opciones marcadas en orden
    marked.forEach(op => {
      const parts = op.narrativeParts;
      let piece = "";

      if (parts.type === "plain") {
        piece = parts.text || "";
      } else if (parts.type === "text") {
        const inp = document.getElementById(op.id + "_txt");
        piece += parts.before || "";
        const val = inp ? inp.value : "";
        if (val) piece += val;
        piece += parts.after || "";
      } else if (parts.type === "dropdown") {
        const sel = document.getElementById(op.id + "_sel");
        piece += parts.before || "";
        const val = sel ? sel.value : "";
        if (val) piece += val;
        piece += parts.after || "";
      }

      if (piece.trim() !== "") {
        if (narrativa && !narrativa.endsWith("\n")) narrativa += "\n";
        narrativa += piece.trim();
        if (!narrativa.endsWith("\n")) narrativa += "\n";
      }

      // Multilínea =>>> ... <<< (tal cual)
      if (op.multilineText != null) {
        const mt = String(op.multilineText);
        if (mt.length > 0) {
          if (narrativa && !narrativa.endsWith("\n")) narrativa += "\n";
          narrativa += mt;
          if (!narrativa.endsWith("\n")) narrativa += "\n";
        }
      }
    });
  });

  document.getElementById("resultado").textContent = narrativa.trim();
}
</script>

</body>
</html>