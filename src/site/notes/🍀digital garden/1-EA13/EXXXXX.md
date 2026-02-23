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
    textarea {
      width: 100%;
      height: 240px;
      font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", monospace;
      white-space: pre;
    }
    /* CRÍTICO: preservar saltos y espacios */
    #resultado{
      white-space: break-spaces;
      font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", monospace;
      border:1px solid #ddd; padding:12px; border-radius:10px; margin-top:12px;
      tab-size: 4;
    }
    button { margin-top: 10px; padding: 10px 12px; border-radius: 10px; border: 1px solid #ccc; cursor: pointer; }
    .row { display:flex; gap:10px; flex-wrap: wrap; align-items: center; }
    .hint { font-size: 12px; opacity: .85; margin-top: 6px; }
  </style>
</head>
<body>

  <div class="topbar">
    <div class="row">
      <label class="opt" style="margin:0">
        <input type="checkbox" id="toggleHeaders" checked>
        Incluir headers en la narrativa
      </label>

      <button onclick="cargarDesdeTextarea()">Cargar/Actualizar Formulario</button>
      <button onclick="updateNarrativa()">Generar Narrativa</button>
      <button onclick="copiarNarrativa()">Copiar narrativa</button>
    </div>

    <div class="hint">
      Al FINAL de una línea puedes usar: <b>/</b> = +1 línea en blanco; <b>//</b> = +2 líneas en blanco.
      (No se muestra en el label ni en el título.)
      <br>Además: la narrativa queda con <b>1 línea en blanco entre cada línea</b> (doble espaciado) para separar “PIEL”, “CABEZA Y CUELLO”, etc.
    </div>

    <textarea id="rawInput" spellcheck="false"></textarea>
  </div>

  <div id="formulario"></div>

  <p id="resultado"></p>

<script>
let headersData = [];

/* =========================
   / y // al final de línea
   ========================= */
function extractSlashGapFromEnd(s) {
  const m = s.match(/^(.*?)(\s*\/\/\s*|\s*\/\s*)$/);
  if (!m) return { text: s, gap: 0 };
  const token = m[2].replace(/\s/g, "");
  return { text: m[1], gap: (token === "//") ? 2 : 1 };
}

/* =========================
   Doble espaciado:
   1 línea en blanco entre líneas (sin perder espacios)
   ========================= */
function doubleSpacePreserve(text) {
  // NO trim, NO colapsar. Solo convertimos LF -> LF LF.
  // Preserva líneas vacías y líneas con solo espacios.
  const t = String(text).replace(/\r/g, "");
  return t.split("\n").join("\n\n");
}

function stripConnectParens_onlyForNormalText(s) {
  return s.replace(/\(([^)]*CONECTAR CON[^)]*)\)/gi, "");
}
function parseLinkTarget(s) {
  const m = s.match(/\(\s*CONECTAR\s+CON\s+OPCION\s+(\d+)\s+DE\s+HEADER\s+(\d+)\s*\)/i);
  if (!m) return null;
  return { x: Number(m[1]), y: Number(m[2]) };
}
function parseDefaultFromHeaderTitle(titleRaw) {
  const m = titleRaw.match(/\(\s*DEFAULT\s*=>>>\s*([\s\S]*?)\s*<<<\s*\)\s*$/i);
  if (!m) return { title: titleRaw, defText: null };
  return { title: titleRaw.replace(m[0], ""), defText: m[1] };
}
function makeHeaderTag(n) {
  const level = Math.min(Math.max(n, 1), 6);
  return "h" + level;
}

/* =========================
   Parse opción 1 línea
   ========================= */
function parseOptionLineSingleLine(lineRaw) {
  const gapInfo = extractSlashGapFromEnd(lineRaw);
  const lineNoGap = gapInfo.text;

  const link = parseLinkTarget(lineNoGap);
  let cleaned = stripConnectParens_onlyForNormalText(lineNoGap);
  cleaned = cleaned.replace(/^\s+/,"").replace(/\s+$/,"");

  let dropdown = null;
  if (cleaned.includes("***")) {
    const idx = cleaned.indexOf("***");
    const before = cleaned.slice(0, idx);
    const after = cleaned.slice(idx + 3);

    const opts = [];
    const re = /(\d+)\.([^]+?)(?=(?:\s+\d+\.)|$)/g;
    let mm;
    while ((mm = re.exec(after)) !== null) {
      const val = mm[2];
      if (val != null) opts.push(val.trim());
    }
    dropdown = { before, options: opts, after: "" };
  }

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
    labelParts = { type: "plain", text: cleaned };
    narrativeParts = { type: "plain", text: cleaned };
  }

  return { raw: lineRaw, link, labelParts, narrativeParts, multilineText: null, gapAfter: gapInfo.gap };
}

/* =========================
   Parse headers + multilínea
   ========================= */
function parseHeaders(raw) {
  const lines = raw.replace(/\r/g, "").split("\n");

  const headers = [];
  let current = null;

  let i = 0;
  while (i < lines.length) {
    const line = lines[i];

    const headerMatch = line.match(/^\s*header\s+(\d+)\s*:\s*(.*)\s*$/i);
    if (headerMatch) {
      const n = Number(headerMatch[1]);
      let titleRaw = headerMatch[2] ?? "";

      // gap al final del header (para cuando se use DEFAULT)
      const gapInfoHeader = extractSlashGapFromEnd(titleRaw);
      titleRaw = gapInfoHeader.text;

      const { title: titleNoDefault, defText: defFormal } = parseDefaultFromHeaderTitle(titleRaw);

      // DEFAULT implícito en header: =>>> ... <<<
      let titleDisplay = titleNoDefault;
      let defImplicit = null;

      const start = titleDisplay.indexOf("=>>>");
      const end = titleDisplay.indexOf("<<<");
      if (start !== -1 && end !== -1 && end > start) {
        defImplicit = titleDisplay.slice(start + 4, end);
        titleDisplay = (titleDisplay.slice(0, start) + titleDisplay.slice(end + 3));
      }

      titleDisplay = titleDisplay.replace(/^\s+/,"").replace(/\s+$/,"");

      current = {
        n,
        titleDisplay,
        defaultText: (defFormal != null ? defFormal : defImplicit),
        defaultGapAfter: gapInfoHeader.gap,
        options: []
      };
      headers.push(current);
      i++;
      continue;
    }

    if (!current) { i++; continue; }
    if (line.trim() === "") { i++; continue; }

    const idxStart = line.indexOf("=>>>");
    if (idxStart !== -1) {
      // gap puede venir al final de la línea de inicio o de la línea del cierre
      const gapInfoStartLine = extractSlashGapFromEnd(line);
      const lineNoGap = gapInfoStartLine.text;

      const s2 = lineNoGap.indexOf("=>>>");
      const endSame = lineNoGap.indexOf("<<<", s2 + 4);

      if (endSame !== -1) {
        const before = lineNoGap.slice(0, s2);
        const inner = lineNoGap.slice(s2 + 4, endSame);
        const after = lineNoGap.slice(endSame + 3);

        const base = parseOptionLineSingleLine(before + after);
        base.multilineText = inner;
        base.gapAfter = gapInfoStartLine.gap || base.gapAfter;
        current.options.push(base);
        i++;
        continue;
      }

      const before = lineNoGap.slice(0, s2);
      const collected = [];
      collected.push(lineNoGap.slice(s2 + 4)); // puede ser "  " o ""

      i++;
      while (i < lines.length) {
        const l2 = lines[i];
        const gapInfoCloseLine = extractSlashGapFromEnd(l2);
        const l2NoGap = gapInfoCloseLine.text;

        const idxEnd = l2NoGap.indexOf("<<<");
        if (idxEnd !== -1) {
          collected.push(l2NoGap.slice(0, idxEnd));
          const base = parseOptionLineSingleLine(before);
          base.multilineText = collected.join("\n");
          base.gapAfter = gapInfoStartLine.gap || gapInfoCloseLine.gap || base.gapAfter;
          current.options.push(base);
          i++;
          break;
        } else {
          collected.push(l2);
          i++;
        }
      }
      continue;
    }

    current.options.push(parseOptionLineSingleLine(line));
    i++;
  }

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
   Render
   ========================= */
function render() {
  const form = document.getElementById("formulario");
  form.innerHTML = "";

  headersData.forEach(h => {
    const block = document.createElement("div");
    block.className = "header-block";

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

function cargarDesdeTextarea() {
  const raw = document.getElementById("rawInput").value;
  headersData = parseHeaders(raw);
  render();
  document.getElementById("resultado").textContent = "";
}

/* =========================
   Append con gaps + doble espaciado
   ========================= */
function appendBlock(narr, text, extraBlankLines) {
  // text se imprime con DOBLE ESPACIADO
  const doubled = doubleSpacePreserve(text);

  if (narr !== "" && !narr.endsWith("\n")) narr += "\n";
  narr += doubled;

  if (!narr.endsWith("\n")) narr += "\n";

  // extraBlankLines:
  // 1 => +1 línea en blanco adicional (ya hay doble espaciado)
  // 2 => +2 líneas en blanco adicionales
  if (extraBlankLines > 0) narr += "\n".repeat(extraBlankLines);

  return narr;
}

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
        // AHORA: si includeHeaders está activo, sí ponemos el título como separador
        if (includeHeaders && h.titleDisplay && h.titleDisplay.trim() !== "") {
          narrativa = appendBlock(narrativa, h.titleDisplay.trim(), 0);
        }
        narrativa = appendBlock(narrativa, String(h.defaultText), h.defaultGapAfter || 0);
      }
      return;
    }

    // Header title normal
    if (includeHeaders) {
      if (h.titleDisplay && h.titleDisplay.trim() !== "") {
        narrativa = appendBlock(narrativa, h.titleDisplay.trim(), 0);
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
        narrativa = appendBlock(narrativa, piece.trim(), 0);
      }

      if (op.multilineText != null) {
        const mt = String(op.multilineText); // sin trim
        if (mt.length > 0) {
          narrativa = appendBlock(narrativa, mt, op.gapAfter || 0);
        } else if (op.gapAfter) {
          narrativa = appendBlock(narrativa, "", op.gapAfter);
        }
      } else if (op.gapAfter) {
        narrativa = appendBlock(narrativa, "", op.gapAfter);
      }
    });
  });

  document.getElementById("resultado").textContent = narrativa.trim();
}

/* =========================
   Copiar narrativa
   ========================= */
async function copiarNarrativa() {
  const txt = document.getElementById("resultado").textContent;
  try {
    await navigator.clipboard.writeText(txt);
    alert("Narrativa copiada.");
  } catch (e) {
    const ta = document.createElement("textarea");
    ta.value = txt;
    document.body.appendChild(ta);
    ta.select();
    document.execCommand("copy");
    document.body.removeChild(ta);
    alert("Narrativa copiada.");
  }
}

/* =========================
   Precarga tu ejemplo
   ========================= */
document.getElementById("rawInput").value =
`header 1:  .
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
header 2:  PIEL =>>> PIEL: SIN LESIONES<<< /
PETEQUIAS EN **
MACULAS ERITEMATOSAS EN ** 
header 3:  CABEZA Y CUELLO: =>>>NORMOCEFALO, CONJUNTIVAS NORMOCROMICAS, ESCLERAS ANICTERICAS, ISOCORIA NORMOREACTIVA, MOVIMIENTOS OCULARES NORMALES; MUCOSA NASAL NORMAL; MUCOSA ORAL HUMEDA, OROFARINGE LIMPIA; OTOSCOPIA BILATERAL NORMAL.<<< /
ESCLERAS ICTERICAS
MUCOSA ORAL SECA SIN LESIONES
CONGESTIÓN CONJUNTIVAL SIN SECRECIÓN PURULENTA O MUCOSA
DOLOR EN ANGULO MANDIBULAR **`;

cargarDesdeTextarea();
</script>

</body>
</html>