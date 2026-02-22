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
   INPUT: PEGADO DEL USUARIO
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
   PARSER (sin librerías)
   ========================= */
function escapeHtml(s) {
  return s.replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;").replace(/"/g,"&quot;").replace(/'/g,"&#039;");
}

function extractBetweenMarkers(s) {
  const start = s.indexOf("=>>>");
  const end = s.indexOf("<<<");
  if (start === -1 || end === -1 || end < start) return { outer: s, inner: null };
  const inner = s.slice(start + 4, end);
  const outer = (s.slice(0, start) + s.slice(end + 3)).trim();
  return { outer, inner };
}

function stripConnectParens(s) {
  // Remueve SOLO paréntesis que contienen "CONECTAR CON"
  // (mantiene otros paréntesis)
  return s.replace(/\(([^)]*CONECTAR CON[^)]*)\)/gi, "").replace(/\s{2,}/g, " ").trim();
}

function parseLinkTarget(s) {
  // Detecta: (CONECTAR CON OPCION X DE HEADER Y)
  const m = s.match(/\(\s*CONECTAR\s+CON\s+OPCION\s+(\d+)\s+DE\s+HEADER\s+(\d+)\s*\)/i);
  if (!m) return null;
  return { x: Number(m[1]), y: Number(m[2]) };
}

function parseDefaultFromHeaderTitle(titleRaw) {
  // header N: <título> (DEFAULT =>>> <TEXTO_MULTILÍNEA> <<<)
  const m = titleRaw.match(/\(\s*DEFAULT\s*=>>>\s*([\s\S]*?)\s*<<<\s*\)\s*$/i);
  if (!m) return { title: titleRaw.trim(), defText: null };
  const defText = m[1];
  const title = titleRaw.replace(m[0], "").trim();
  return { title, defText };
}

function parseOptionLine(lineRaw) {
  const line = lineRaw.trimEnd();

  const link = parseLinkTarget(line);
  let cleaned = stripConnectParens(line);

  // Multilínea automática por opción
  const multi = extractBetweenMarkers(cleaned);
  cleaned = multi.outer; // para label/narrativa "normal"
  const multilineText = (multi.inner != null) ? multi.inner : null;

  // Dropdown ***
  // Formato: PREFIJO ***1.OPCION 2.OPCION2 3.OPCION3 SUFIJO
  let dropdown = null;
  if (cleaned.includes("***")) {
    const idx = cleaned.indexOf("***");
    const before = cleaned.slice(0, idx);
    const after = cleaned.slice(idx + 3);
    // Opciones inmediatamente después: 1.xxx 2.yyy ...
    const opts = [];
    const re = /(\d+)\.([^]+?)(?=(?:\s+\d+\.)|$)/g; // captura hasta próximo " n."
    let mm;
    while ((mm = re.exec(after)) !== null) {
      const val = mm[2].trim();
      if (val) opts.push(val);
    }
    // Sufijo: si el texto después de las opciones tuviera extra,
    // este parser simple lo incluye dentro de la última opción.
    dropdown = { before: before, options: opts, after: "" };
    cleaned = (before + after).trim(); // no se usa para render, solo para fallback
  }

  // Input ** (un solo input por opción, según regla)
  let textInput = null;
  if (dropdown == null && cleaned.includes("**")) {
    const idx = cleaned.indexOf("**");
    const before = cleaned.slice(0, idx);
    const after = cleaned.slice(idx + 2);
    textInput = { before: before, after: after };
  }

  // Texto base (sin **/*** y sin paréntesis de conectar y sin multilinea)
  let labelParts = null;
  let narrativeParts = null;

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

  return { raw: lineRaw, link, labelParts, narrativeParts, multilineText };
}

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

      const { title: titleNoDefault, defText } = parseDefaultFromHeaderTitle(titleRaw);

      // Si el título trae =>>> <<< (como en tus headers 2 y 3), lo ocultamos del texto del header
      // y NO lo usamos como DEFAULT (no hay regla para eso en header). Se elimina del título mostrado.
      const tMulti = extractBetweenMarkers(titleNoDefault);
      let displayTitle = tMulti.outer;

      // Limpia " //" al final si existe (se mantiene el texto si era parte real)
      displayTitle = displayTitle.replace(/\s*\/\/\s*$/, "").trim();

      current = {
        n,
        titleRaw: titleRaw.trim(),
        titleDisplay: displayTitle,
        defaultText: defText,
        options: []
      };
      headers.push(current);
      i++;
      continue;
    }

    // Opción (si hay header activo)
    if (current && line.trim() !== "") {
      // Si el renglón es solo "<<<" o solo marcadores sueltos, igual lo procesa (pero tu texto ya viene completo)
      const opt = parseOptionLine(line);
      current.options.push(opt);
    }

    i++;
  }

  // Asigna IDs obligatorios id="h<Y>_op<X>"
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

function makeHeaderTag(n) {
  const level = Math.min(Math.max(n, 1), 6);
  return "h" + level;
}

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

      // Espaciado texto
      label.appendChild(document.createTextNode(" "));

      if (op.labelParts.type === "plain") {
        label.appendChild(document.createTextNode(op.labelParts.text));
      } else if (op.labelParts.type === "text") {
        label.appendChild(document.createTextNode(op.labelParts.before));

        const inp = document.createElement("input");
        inp.type = "text";
        inp.id = op.id + "_txt";
        inp.setAttribute("data-for", op.id);
        label.appendChild(inp);

        label.appendChild(document.createTextNode(op.labelParts.after));
      } else if (op.labelParts.type === "dropdown") {
        label.appendChild(document.createTextNode(op.labelParts.before));

        const sel = document.createElement("select");
        sel.id = op.id + "_sel";
        sel.setAttribute("data-for", op.id);

        // placeholder vacío
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

  // (checks se obtiene como pide la regla; lo usamos indirectamente)
  const includeHeaders = !!document.getElementById("toggleHeaders")?.checked;

  let narrativa = "";

  headersData.forEach(h => {
    // ¿alguna marcada en este header?
    const marked = h.options.filter(op => {
      const cb = document.getElementById(op.id);
      return cb && cb.checked;
    });

    if (marked.length === 0) {
      // DEFAULT si existe
      if (h.defaultText != null && String(h.defaultText).length > 0) {
        if (narrativa && !narrativa.endsWith("\n")) narrativa += "\n";
        narrativa += String(h.defaultText);
        if (!narrativa.endsWith("\n")) narrativa += "\n";
      }
      return;
    }

    // Si hay marcadas: NO agregar default
    if (includeHeaders) {
      if (h.titleDisplay && h.titleDisplay.trim() !== "") {
        if (narrativa && !narrativa.endsWith("\n")) narrativa += "\n";
        narrativa += h.titleDisplay.trim() + "\n";
      }
    }

    // Opciones marcadas en orden
    marked.forEach(op => {
      const parts = op.narrativeParts;

      // Construye texto normal (sin mostrar **/***)
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

      // Agrega texto normal si existe
      if (piece.trim() !== "") {
        if (narrativa && !narrativa.endsWith("\n")) narrativa += "\n";
        narrativa += piece.trim();
        if (!narrativa.endsWith("\n")) narrativa += "\n";
      }

      // Multilínea =>>> <<< (tal cual)
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

// Opcional: actualizar narrativa cuando cambias algo (sin romper reglas)
document.addEventListener("input", (e) => {
  const t = e.target;
  if (!t) return;
  if (t.matches('input[type="checkbox"], input[type="text"], select')) {
    // no auto-ejecuta si no quieres; comentar la siguiente línea si prefieres solo con botón:
    // updateNarrativa();
  }
});
</script>

</body>
</html>