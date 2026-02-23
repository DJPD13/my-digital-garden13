---
{"dg-publish":true,"permalink":"/digital-garden/1-ea-13/exxxxx/","dgPassFrontmatter":true}
---

<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Formulario dinámico + Narrativa</title>
  <style>
    body { font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif; margin: 16px; }
    textarea { width: 100%; min-height: 220px; }
    .topbar { display: flex; gap: 12px; align-items: center; flex-wrap: wrap; margin: 12px 0; }
    #formContainer h1, #formContainer h2, #formContainer h3, #formContainer h4, #formContainer h5, #formContainer h6 { margin: 18px 0 8px; }
    .headerBlock { border: 1px solid #ddd; padding: 10px; border-radius: 10px; margin: 10px 0; }
    .opt { display: block; margin: 6px 0; }
    .opt input[type="text"] { margin: 0 6px; }
    .opt select { margin: 0 6px; }
    .muted { opacity: 0.75; font-size: 12px; }
    /* OBLIGATORIO */
    #resultado { white-space: pre-wrap; }
    #resultado { white-space: break-spaces; }
    #resultado { border: 1px solid #ddd; border-radius: 10px; padding: 10px; min-height: 80px; }
  </style>
</head>
<body>

  <h2>Entrada</h2>
  <textarea id="rawInput">
header 1:  .
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
DOLOR EN ANGULO MANDIBULAR ** 
  </textarea>

  <div class="topbar">
    <label>
      <input type="checkbox" id="toggleHeaders" checked />
      Incluir headers en la narrativa
    </label>

    <button type="button" onclick="loadFormFromTextarea()">Cargar/Actualizar Formulario</button>
    <button onclick="updateNarrativa()">Generar Narrativa</button>
    <span class="muted">Tip: marca “NO PATOLOGICO” para ver saltos de línea reales en el resultado.</span>
  </div>

  <h2>Formulario</h2>
  <div id="formContainer"></div>

  <h2>Resultado</h2>
  <p id="resultado"></p>

<script>
/* =========================
   Utilidades (sin librerías)
   ========================= */

function stripSlashMarker(line) {
  // Detecta " /" o " //" al final (con espacios finales opcionales) y lo elimina.
  // Retorna { text, extra } donde extra = 0 | 1 | 2 (líneas en blanco extra).
  let extra = 0;
  let text = line;

  // Sin regex que convierta \n a espacios; aquí solo analizamos la línea.
  // Priorizamos // antes que /
  const trimmedRight = text.replace(/[ \t]+$/g, "");
  if (trimmedRight.endsWith(" //")) {
    extra = 2;
    text = trimmedRight.slice(0, -3);
  } else if (trimmedRight.endsWith(" /")) {
    extra = 1;
    text = trimmedRight.slice(0, -2);
  } else {
    text = line; // conserva lo original si no hay marcador
  }
  return { text, extra };
}

function removeConnectParenKeepLinkInfo(s) {
  // Quita paréntesis que contengan "CONECTAR CON" (no deben mostrarse),
  // pero primero extrae link del tipo: (CONECTAR CON OPCION X DE HEADER Y)
  let link = null;
  const reLink = /\(\s*CONECTAR\s+CON\s+OPCION\s+(\d+)\s+DE\s+HEADER\s+(\d+)\s*\)/i;
  const m = s.match(reLink);
  if (m) {
    link = { op: Number(m[1]), header: Number(m[2]) };
  }
  const cleaned = s.replace(/\([^)]*CONECTAR\s+CON[^)]*\)/ig, "");
  return { cleaned, link };
}

function splitControls(text) {
  // Convierte un texto con ** y *** en partes: text/input/select.
  // ***: inmediatamente después vienen opciones tipo "1.OPCION 2.OPCION2 ..."
  // Devuelve { parts, selectOptionsUsed }
  const parts = [];
  let i = 0;

  while (i < text.length) {
    const idx3 = text.indexOf("***", i);
    const idx2 = text.indexOf("**", i);

    // Elegir el siguiente marcador (*** tiene prioridad si coincide)
    let next = -1;
    let kind = null;

    if (idx3 !== -1 && (idx2 === -1 || idx3 <= idx2)) {
      next = idx3;
      kind = "***";
    } else if (idx2 !== -1) {
      next = idx2;
      kind = "**";
    }

    if (next === -1) {
      parts.push({ type: "text", value: text.slice(i) });
      break;
    }

    if (next > i) {
      parts.push({ type: "text", value: text.slice(i, next) });
    }

    if (kind === "**") {
      parts.push({ type: "input" });
      i = next + 2;
      continue;
    }

    // kind === "***"
    // Tomar el resto de la línea como opciones
    const rest = text.slice(next + 3);
    const options = [];
    const optRe = /(\d+)\.([^0-9]+)/g;
    let mm;
    while ((mm = optRe.exec(rest)) !== null) {
      const label = mm[2].replace(/[ \t]+$/g, "").replace(/^[ \t]+/g, "");
      if (label.length > 0) options.push(label);
    }
    parts.push({ type: "select", options: options.length ? options : [""] });
    i = text.length; // *** consume hasta el final (según regla dada)
  }

  return parts;
}

function isHeaderLine(line) {
  return /^header\s+\d+\s*:/i.test(line);
}

/* =========================
   Parser principal
   ========================= */

let parsed = { headers: [] };

function parseRawFromTextarea() {
  const raw = document.getElementById("rawInput").value; // OBLIGATORIO
  // Importante: NO usar trim() sobre texto multilínea. No usamos trim aquí.

  const lines = raw.split("\n");
  const headers = [];

  let currentHeader = null;
  let headerCounter = 0;

  function startHeader(level, titleText, headerExtraNewlines, defaultBlock) {
    headerCounter += 1;
    const h = {
      idx: headerCounter,          // 1,2,3... en orden de aparición
      level: level,                // N del "header N:"
      title: titleText,            // título limpio (sin / //, sin DEFAULT, sin conectores)
      headerExtraNewlines: headerExtraNewlines, // si el header trae / o // (aplica al separador si se imprime)
      defaultBlock: defaultBlock,  // { text, extraNewlines } o null
      options: []
    };
    headers.push(h);
    currentHeader = h;
  }

  function parseDefaultFromHeaderTail(tail) {
    // Soporta:
    // 1) "TITULO (DEFAULT =>>> TEXTO <<<)"
    // 2) "TITULO =>>> TEXTO <<<"
    // Retorna { titleClean, defaultBlock, trailingExtraNewlinesForHeaderSeparator }
    let headerExtraNewlines = 0;
    let defaultBlock = null;

    // Primero quitar / o // del final de la línea del header
    const stripped = stripSlashMarker(tail);
    let tailNoSlash = stripped.text;
    headerExtraNewlines += stripped.extra;

    // Extraer y remover (CONECTAR CON...) del título visible (regla paréntesis)
    const removedConn = removeConnectParenKeepLinkInfo(tailNoSlash);
    tailNoSlash = removedConn.cleaned;

    // Caso (DEFAULT =>>> ... <<<)
    const defIdx = tailNoSlash.toUpperCase().indexOf("(DEFAULT");
    if (defIdx !== -1) {
      const before = tailNoSlash.slice(0, defIdx);
      const after = tailNoSlash.slice(defIdx);

      const marker = "=>>>";
      const start = after.indexOf(marker);
      if (start !== -1) {
        // Buscar cierre <<<
        const startPos = defIdx + start + marker.length;
        // Construimos el contenido entre =>>> y <<< incluso si hubiera "<<<" en la misma línea (aquí todo es una sola línea)
        const rest = tailNoSlash.slice(startPos);
        const end = rest.indexOf("<<<");
        if (end !== -1) {
          let inside = rest.slice(0, end);
          // Puede haber / o // después del <<< dentro de la misma línea (si existiera, lo tratamos como extraNewlines del DEFAULT)
          const afterClose = rest.slice(end + 3);
          const strippedAfterClose = stripSlashMarker(afterClose);
          const extraDefault = strippedAfterClose.extra;

          defaultBlock = { text: inside, extraNewlines: extraDefault };
          // El título del header es "before" limpio
          return { titleClean: before, defaultBlock, headerExtraNewlines };
        }
      }
      return { titleClean: before, defaultBlock: null, headerExtraNewlines };
    }

    // Caso implícito: "TITULO =>>> ... <<<" (puede ser multilínea, se maneja afuera)
    const idxMarker = tailNoSlash.indexOf("=>>>");
    if (idxMarker !== -1) {
      const titleClean = tailNoSlash.slice(0, idxMarker);
      // El bloque en sí se leerá como multilinea desde esta misma línea hacia adelante
      // Aquí solo devolvemos el título; el defaultBlock se completará por el lector multilinea.
      return { titleClean, defaultBlock: { text: null, extraNewlines: 0, needsMultilineRead: true, startLineRemainder: tailNoSlash.slice(idxMarker + 4) }, headerExtraNewlines };
    }

    return { titleClean: tailNoSlash, defaultBlock: null, headerExtraNewlines };
  }

  function readMultilineBlock(firstRemainder, startLineExtraFromSlash, startAtIndex) {
    // Lee texto desde (firstRemainder) y/o líneas siguientes hasta encontrar '<<<'
    // Preserva \n y espacios TAL CUAL.
    // También detecta / o // al final de la línea donde aparece el cierre '<<<' (o en la misma línea si cierra ahí).
    // Retorna { text, endIndex, extraNewlinesFromClose, extraNewlinesFromStartLine }
    let textParts = [];
    let extraClose = 0;
    let extraStart = startLineExtraFromSlash || 0;

    let remainder = firstRemainder; // puede incluir espacios; NO trim
    if (remainder.includes("<<<")) {
      const pos = remainder.indexOf("<<<");
      const beforeClose = remainder.slice(0, pos);
      textParts.push(beforeClose);

      const afterClose = remainder.slice(pos + 3);
      const stripped = stripSlashMarker(afterClose);
      extraClose += stripped.extra;

      return {
        text: textParts.join(""),
        endIndex: startAtIndex,
        extraNewlinesFromClose: extraClose,
        extraNewlinesFromStartLine: extraStart
      };
    }

    // No cerró en la misma línea: agregar remainder completo tal cual
    textParts.push(remainder);

    let j = startAtIndex + 1;
    while (j < lines.length) {
      const line = lines[j];

      // Si aparece un header antes de cerrar, igual lo consideramos cierre "faltante".
      // (No debería pasar en tu formato, pero evitamos romper.)
      if (isHeaderLine(line)) {
        return {
          text: textParts.join("\n"),
          endIndex: j - 1,
          extraNewlinesFromClose: extraClose,
          extraNewlinesFromStartLine: extraStart
        };
      }

      if (line.includes("<<<")) {
        const pos = line.indexOf("<<<");
        const beforeClose = line.slice(0, pos);
        textParts.push(beforeClose);

        const afterClose = line.slice(pos + 3);
        const stripped = stripSlashMarker(afterClose);
        extraClose += stripped.extra;

        return {
          text: textParts.join("\n"),
          endIndex: j,
          extraNewlinesFromClose: extraClose,
          extraNewlinesFromStartLine: extraStart
        };
      } else {
        textParts.push(line);
      }
      j += 1;
    }

    return {
      text: textParts.join("\n"),
      endIndex: lines.length - 1,
      extraNewlinesFromClose: extraClose,
      extraNewlinesFromStartLine: extraStart
    };
  }

  let i = 0;
  while (i < lines.length) {
    const lineRaw = lines[i];
    const line = lineRaw; // mantener exacto, sin trim

    const headerMatch = line.match(/^header\s+(\d+)\s*:\s*(.*)$/i);
    if (headerMatch) {
      const level = Number(headerMatch[1]);
      const tail = headerMatch[2] || "";

      const defInfo = parseDefaultFromHeaderTail(tail);
      // Limpieza mínima del título: solo quitar espacios laterales del título (esto es una línea; permitido)
      // (No es trim de multilínea.)
      const titleClean = defInfo.titleClean.replace(/^[ \t]+/g, "").replace(/[ \t]+$/g, "");

      let defaultBlock = null;

      if (defInfo.defaultBlock && defInfo.defaultBlock.needsMultilineRead) {
        // leer bloque multilínea empezando desde esta misma línea, después de =>>>
        // Importante: el marcador =>>> ya fue recortado, aquí firstRemainder es lo que venía después.
        const remainder = defInfo.defaultBlock.startLineRemainder;

        // También el header ya pasó por stripSlashMarker (para la línea completa del header),
        // pero si el cierre <<< trae / o //, se detecta aquí.
        const read = readMultilineBlock(remainder, 0, i);
        defaultBlock = {
          text: read.text,
          extraNewlines: read.extraNewlinesFromClose // / o // al cierre
        };
        i = read.endIndex; // saltar líneas consumidas
      } else if (defInfo.defaultBlock && defInfo.defaultBlock.text !== null) {
        defaultBlock = {
          text: defInfo.defaultBlock.text,
          extraNewlines: defInfo.defaultBlock.extraNewlines || 0
        };
      }

      startHeader(level, titleClean, defInfo.headerExtraNewlines, defaultBlock);
      i += 1;
      continue;
    }

    // Si no hay header aún, ignorar líneas sueltas hasta el primer header
    if (!currentHeader) {
      i += 1;
      continue;
    }

    // Línea de opción (hasta el siguiente header)
    // Primero quitar conectores (pero extraer link)
    const conn = removeConnectParenKeepLinkInfo(line);
    let cleanLine = conn.cleaned;

    // Quitar / o // al final de esta línea (si aplica a una opción sin bloque multiline)
    const strippedLine = stripSlashMarker(cleanLine);
    cleanLine = strippedLine.text;
    let extraNewlines = strippedLine.extra;

    // Detectar bloque multilínea de opción: =>>> ... <<<
    const idxMarker = cleanLine.indexOf("=>>>");
    if (idxMarker !== -1) {
      const prefix = cleanLine.slice(0, idxMarker);
      const remainder = cleanLine.slice(idxMarker + 4); // después de =>>>

      const read = readMultilineBlock(remainder, 0, i);
      const multilineText = read.text; // NO trim

      extraNewlines += read.extraNewlinesFromClose;

      currentHeader.options.push({
        rawPrefix: prefix,
        rawSuffix: "", // (no estamos usando sufijo fuera del bloque; el texto está en el bloque)
        parts: null,   // se llena al renderizar
        multilineText: multilineText,
        extraNewlines: extraNewlines,
        link: conn.link
      });

      i = read.endIndex + 1;
      continue;
    }

    // Opción normal (sin =>>>)
    currentHeader.options.push({
      rawPrefix: cleanLine,
      rawSuffix: "",
      parts: null,
      multilineText: null,
      extraNewlines: extraNewlines,
      link: conn.link
    });

    i += 1;
  }

  parsed = { headers };
}

/* =========================
   Render del formulario
   ========================= */

function clearEl(el) {
  while (el.firstChild) el.removeChild(el.firstChild);
}

function makeHeading(level, text) {
  const tag = "h" + Math.max(1, Math.min(6, level));
  const h = document.createElement(tag);
  h.textContent = text;
  return h;
}

function renderForm() {
  const container = document.getElementById("formContainer");
  clearEl(container);

  parsed.headers.forEach((h) => {
    const block = document.createElement("div");
    block.className = "headerBlock";

    const heading = makeHeading(h.level, h.title);
    block.appendChild(heading);

    h.options.forEach((opt, idx) => {
      const optNumber = idx + 1;
      const id = "h" + h.idx + "_op" + optNumber; // OBLIGATORIO

      const label = document.createElement("label");
      label.className = "opt";

      const cb = document.createElement("input");
      cb.type = "checkbox";
      cb.id = id;

      if (opt.link) {
        cb.dataset.link = "h" + opt.link.header + "_op" + opt.link.op; // Implementar con data-link
      }

      cb.addEventListener("change", (e) => {
        const targetId = e.target.dataset.link;
        if (targetId) {
          const target = document.getElementById(targetId);
          if (target && target.type === "checkbox") {
            target.checked = e.target.checked;
          }
        }
      });

      label.appendChild(cb);

      // Texto visible del label:
      // - Si tiene multilineText, NO mostrar ese bloque: solo mostrar el prefijo (antes de =>>>)
      // - Si no, mostrar todo el texto (con inputs/selects donde corresponda)
      const visibleText = (opt.rawPrefix || "");

      const parts = splitControls(visibleText);
      opt.parts = []; // guardamos partes con refs reales para narrativa

      parts.parts.forEach((p) => {
        if (p.type === "text") {
          const span = document.createElement("span");
          span.textContent = p.value;
          label.appendChild(span);
          opt.parts.push({ type: "text", value: p.value });
        } else if (p.type === "input") {
          const inp = document.createElement("input");
          inp.type = "text";
          inp.addEventListener("input", () => {
            // No toca \n. Solo actualiza narrativa si el usuario quiere.
          });
          label.appendChild(inp);
          opt.parts.push({ type: "input", el: inp });
        } else if (p.type === "select") {
          const sel = document.createElement("select");
          p.options.forEach((optText) => {
            const o = document.createElement("option");
            o.value = optText;
            o.textContent = optText;
            sel.appendChild(o);
          });
          label.appendChild(sel);
          opt.parts.push({ type: "select", el: sel });
        }
      });

      block.appendChild(label);
    });

    // Nota de DEFAULT si existe (solo informativo, sin alterar reglas)
    if (h.defaultBlock && typeof h.defaultBlock.text === "string") {
      const note = document.createElement("div");
      note.className = "muted";
      note.textContent = "DEFAULT configurado para este header (se usará si no marcas ninguna opción).";
      block.appendChild(note);
    }

    container.appendChild(block);
  });
}

function loadFormFromTextarea() {
  parseRawFromTextarea();
  renderForm();
}

/* =========================
   Narrativa
   ========================= */

function partsToText(parts) {
  // Construye prefijo/sufijo con valores de input/select.
  let out = "";
  parts.forEach((p) => {
    if (p.type === "text") out += p.value;
    if (p.type === "input") out += (p.el.value || "");
    if (p.type === "select") out += (p.el.value || "");
  });
  return out;
}

function applyExtraNewlines(narr, extra) {
  if (extra === 1) return narr + "\n";
  if (extra === 2) return narr + "\n\n";
  return narr;
}

/* REGLA OBLIGATORIA:
   updateNarrativa() debe iniciar EXACTAMENTE con:
   const checks = document.querySelectorAll("input[type=checkbox]");
*/
function updateNarrativa() {
  const checks = document.querySelectorAll("input[type=checkbox]");

  const includeHeaders = document.getElementById("toggleHeaders").checked;

  let narrativa = "";

  parsed.headers.forEach((h) => {
    // recolectar checks de opciones de este header en orden
    const selectedOptions = [];
    for (let i = 0; i < h.options.length; i++) {
      const optId = "h" + h.idx + "_op" + (i + 1);
      const cb = document.getElementById(optId);
      if (cb && cb.checked) selectedOptions.push({ opt: h.options[i], cbId: optId });
    }

    const hasAny = selectedOptions.length > 0;

    // Si se deben incluir headers en narrativa, imprimir separador del header
    // SIEMPRE que se vaya a imprimir contenido (opciones marcadas o DEFAULT).
    if (includeHeaders && (hasAny || (h.defaultBlock && typeof h.defaultBlock.text === "string"))) {
      narrativa += "-" + h.title + "\n"; // Formato exacto: "-" + TÍTULO + "\n"
      narrativa = applyExtraNewlines(narrativa, h.headerExtraNewlines);
    }

    if (hasAny) {
      selectedOptions.forEach(({ opt }) => {
        const prefixText = opt.parts ? partsToText(opt.parts) : (opt.rawPrefix || "");

        if (opt.multilineText !== null && opt.multilineText !== undefined) {
          // Regla multilínea por opción:
          // - agregar prefijo en una línea
          // - luego el bloque TAL CUAL (sin trim)
          // - preservar \n y espacios
          narrativa += prefixText + "\n";
          narrativa += opt.multilineText;
          narrativa += "\n";
        } else {
          // Opción normal en una línea
          narrativa += prefixText + "\n";
        }

        narrativa = applyExtraNewlines(narrativa, opt.extraNewlines);
      });
    } else {
      // DEFAULT si no hay ninguna opción marcada
      if (h.defaultBlock && typeof h.defaultBlock.text === "string") {
        // Si includeHeaders está desmarcado, NO agregar header (ya cumplido arriba),
        // solo el DEFAULT.
        narrativa += h.defaultBlock.text;
        narrativa += "\n";
        narrativa = applyExtraNewlines(narrativa, h.defaultBlock.extraNewlines || 0);
      }
    }
  });

  // OBLIGATORIO: solo se permite narrativa.trim() AL FINAL
  document.getElementById("resultado").textContent = narrativa.trim();
}

/* =========================
   Auto-carga inicial (usa el textarea, NO hardcode)
   ========================= */
loadFormFromTextarea();
</script>

</body>
</html>