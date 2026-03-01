---
{"dg-publish":true,"permalink":"/digital-garden/1-maternassss/1-maternas-ea/","dgPassFrontmatter":true}
---

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Examen Físico – Generador de Narrativa</title>
  <style>
    body{
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      line-height: 1.35;
      margin: 16px;
      max-width: 1100px;
      background:#fcfcfc;
    }
    .grupo{
      margin: 0 0 18px 0;
      padding: 10px 12px;
      border-left: 3px solid #5f8ab0;
      background: #fff;
      border-radius: 10px;
      box-shadow: 0 0 0 1px #eef3fb inset;
    }
    h1,h2,h3,h4,h5,h6{
      margin: 0 0 10px 0;
      font-weight: 700;
      white-space: pre-wrap;
    }
    /* Conserva "nivel" visual para N>=7 */
    h6[class^="h"]{ font-size: 1.05rem; }
    label{
      display:block;
      margin: 6px 0;
      cursor:pointer;
      white-space: pre-wrap;
    }
    input[type="checkbox"]{ margin-right: 8px; transform: translateY(1px); }

    input[type="text"], input[type="date"], select{
      margin: 0 6px;
      padding: 6px 8px;
      border: 1px solid #aeb8c6;
      border-radius: 10px;
      background: #fff;
      font: inherit;
      line-height: 1.1;
      box-shadow: 0 1px 0 rgba(0,0,0,0.03);
      vertical-align: middle;
    }
    input[type="text"]{ min-width: 180px; }
    input[type="date"]{ min-width: 170px; }

    /* “Look” de selector de fecha (sin librerías) */
    input[type="date"]{
      padding-right: 10px;
    }
    input[type="date"]:focus, input[type="text"]:focus, select:focus{
      outline: none;
      border-color: #5f8ab0;
      box-shadow: 0 0 0 3px rgba(95,138,176,0.18);
    }

    button{
      background: #1e4468;
      color:#fff;
      border:none;
      font-size: 1.05rem;
      padding: 10px 22px;
      border-radius: 999px;
      margin: 18px 0 10px;
      cursor:pointer;
      font-weight: 700;
    }
    button:hover{ background:#0f2b44; }

    #resultado{
      margin-top: 12px;
      padding: 14px 16px;
      border-radius: 14px;
      background: #f3f7fd;
      border: 2px solid #b4c9e2;
    }
    #resultado p{ margin: 0 0 12px 0; }
  </style>
</head>
<body>

  <div id="app"></div>

  <button onclick="updateNarrativa()">Generar Narrativa</button>
  <div id="resultado"></div>

  <script>
    const COMANDOS = `
header 1:MC: " ** " /
header 2:FORMULA OBSTÉTRICA: G**P** /
header 3:FECHA ÚLTIMO PARTO:  "FECHA" /
header 4:FECHA DE ULTIMA MENSTRUACIÓN: "FECHA" /
header 5:HEMOCLASIFICACIÓN: //
O+
O-
A+
A-
B+
B-
AB+
AB-
header 6:CONSULTA PRECONCEPCIONAL:/
NO
SI
header 7:PLANIFICACIÓN PRECONCEPCIONAL: /
POMEROY
INYECCIÓN MENSUAL
INYECCIÓN TRIMESTRAL
ANTICONCEPTIVOS ORALES
IMPLANTE SUBDERMICO
NO PLANIFICABA ANTERIORMENTE
header 8:CONTROLES PRENATALES: /
** (APORTA HISTORIA CLINICA)
** (NO APORTA HISTORIA CLINICA)
NO RECUERDA (NO APORTA HISTORIA CLINICA)
header 9:EMBARAZO: /
PLANEADO Y ACEPTADO
NO PLANEADO Y ACEPTADO
header 10:PLAN DE PLANIFICACIÓN POSTPARTO: //
POMEROY
INYECCIÓN MENSUAL
INYECCIÓN TRIMESTRAL
ANTICONCEPTIVOS ORALES
IMPLANTE SUBDERMICO
NO DESEA
header 11: PROCEDENCIA: /
VILLANUEVA CASANARE
header 12: DIRECCIÓN: /
CARRERA ** # **-**
CALLE ** #**-**
DIAGONAL **#**-**
header 13: TELÉFONO: ** /
header 14: ESTADO CIVIL:  /
UNION LIBRE
CASADA
SOLTERA
header 15: OCUPACIÓN: /
AMA DE CASA
OFICIOS VARIOS
**
header 16: ESCOLARIDAD: /
BACHILLER
PREGRADO
TECNOLOGO
header 17: VIVE CON: //
SOLA
MADRE
PADRE
ABUELA
**
header 18: EDAD DEL PADRE: /
NO BRINDA INFORMACION
**
header 19: ESCOLARIDAD DEL PADRE:  /
NO BRINDA INFORMACION
BACHILLER
PREGRADO
TECNOLOGO
header 20: PRIMIPATERNIDAD: /
SI
NO
header 21: HEMOCLASIFICACION PATERNA: //
NO BRINDA INFORMACION
O+
O-
A+
A-
B+
B-
AB+
AB-
header 22: REVISIÓN POR SISTEMAS: NIEGA //
DOLOR ABDOMINAL PROGRESIVO
DOLOR ABDOMINAL PERSISTENTE
DOLOR ABDOMINAL LOCALIZADO EN CUADRANTE SUPERIOR DERECHO
METRORRAGIA 
SÍNTOMATOLOGIA URINARIA
NIEGA  LEUCORREA
header 22: ANTECEDENTES GINECOLÓGICOS: /
header 23: G**P**C**V** /
header 24: CONTROLES PRENATALES: /
header 25: CICLOS: /
REGULARES
IRREGULARES
header 26: FUM: "FECHA" /
header 27: MENARQUIA: ** AÑOS /
header 28: SEXARQUIA: ** AÑOS /
header 29: PAREJAS SEXUALES: ** /
header 30: ETS: /
NO
VIH
SIFILIS
GONORREA
header 31: CITOLOGÍA: /
SI HACE ** AÑOS
NO
header 32: VACUNACIÓN: /
COMPLETA
INCOMPLETA
NO ESTA SEGURA DE CUALES VACUNAS SE LE HAN APLICADO
header 33: MICRONUTRIENTES: //
CALCIO
ÁCIDO FÓLICO
HIERRO
GESTAVIT
header 34: TAMIZAJE DEPRESIÓN POSTPARTO/
SI
NO
header 35: DURANTE EL MES PASADO, ¿CON FRECUENCIA SE HA SENTIDO TRISTE, DEPRIMIDA O SIN ESPERANZA?/
SI
NO
header 36: DURANTE EL MES PASADO, ¿HA PERMANECIDO PREOCUPADA POR TENER POCO INTERÉS O PLACER PARA HACER LAS COSAS COTIDIANAS?/
SI
NO
header 37: TAMIZAJE DE VIOLENCIA/
SI
NO
header 38: ¿DURANTE EL ÚLTIMO AÑO, HA SIDO HUMILLADA, MENOSPRECIADA, INSULTADA O AMENAZADA POR SU PAREJA?/
SI
NO
header 39: ¿DURANTE EL ÚLTIMO AÑO, FUE GOLPEADA, BOFETEADA, PATEADA, O LASTIMADA FÍSICAMENTE DE OTRA MANERA?/
SI
NO
header 40: ¿DESDE QUE ESTÁ EN GESTACIÓN, HA SIDO GOLPEADA, BOFETEADA, PATEADA, O LASTIMADA FÍSICAMENTE DE ALGUNA MANERA?/
SI
NO
header 41: ¿DURANTE EL ÚLTIMO AÑO, FUE FORZADA A TENER RELACIONES SEXUALES?/
SI
NO
header 42: VALORACIÓN POR PSICOLOGÍA: /
SI
NO
header 43: VALORACIÓN POR ODONTOLOGÍA: /
SI
NO
header 44: VALORACIÓN POR NUTRICIÓN: ///
SI
NO
header 44:  PARACLINICOS
UROCULTIVO: **
GLUCOSA 1 HORA POSTCARGA: ** GLUCOSA 2 HORAS POST CARGA:**
HEMOGRAMA: HEMOGLOBINA: ** G/DL HEMATOCRITO: ** % VCM: ** FL HCM: ** PG LEUCOCITOS: ** NEUTROFILOS: **%LINFOCITOS: **%MONOCITOS: **% EOSINOFILOS: **% PLAQUETAS: **
VIH: **
AGSHB: **
TREPONEMA: **
TOXOPLASMA IGG: **
TOXOPLASMA IGM: **
UROANALISIS **
RUBEOLA IGG: **
RUBEOLA IGM: **
TSH: ** mU/L
header 45: ECOGRAFIAS
NO APORTA CARPETA DE CONTROLES PRENATALES SIN EMBARGO MANIFIESTA ECOGRAFIAS SIN EVENTUALIDADES
**-**-** ECO TN : EMBARAZO DE ** SEMANAS , TN NORMAL , HOY :  SEMANAS
**-**-** ECOGRAFIA DETALLE ANATOMICO EMBARAZO DE ** SEMANAS BEIENES FETAL PERFIL DE CRECIMEINTO FETAL NORMAL, NO SE DETECTARON MALFORMACIONES MAYORES, PESO FETAL ** GR PERCENTIL **
`.trim();

    function parseHeadersAndOptions(raw){
      const lines = raw.split(/\r?\n/);
      const groups = [];
      let current = null;

      for (let line of lines){
        // mantener contenido, pero evita líneas solo whitespace
        if (!line || !line.trim()) continue;

        const m = line.match(/^header\s+(\d+)\s*:(.*)$/i);
        if (m){
          const n = parseInt(m[1], 10);
          let titlePart = m[2]; // NO trim al inicio: puede tener espacios intencionales
          // contar slashes finales
          let t = titlePart.replace(/\s+$/g, "");
          let slashes = 0;
          while (t.endsWith("/")){
            slashes++;
            t = t.slice(0, -1);
          }
          t = t.replace(/\s+$/g, ""); // quita espacios sobrantes por el comando /
          current = {
            n,
            titleRaw: t,
            slashes,
            options: []
          };
          groups.push(current);
        } else {
          if (!current) continue;
          current.options.push(line); // no tocar texto
        }
      }
      return groups;
    }

    function headingTagForN(n){
      if (n === 1) return { tag: "h1", cls: "" };
      if (n === 2) return { tag: "h2", cls: "" };
      if (n === 3) return { tag: "h3", cls: "" };
      if (n === 4) return { tag: "h4", cls: "" };
      if (n === 5) return { tag: "h5", cls: "" };
      if (n >= 6) return { tag: "h6", cls: (n >= 7 ? `h${n}` : "") };
      return { tag: "h6", cls: "" };
    }

    function extractLinkCommand(rawOption){
      // Si hay paréntesis con "CONECTAR CON", eso NO se muestra, y el texto visible es lo anterior a ese paréntesis.
      const rx = /\(([^)]*CONECTAR CON[^)]*)\)/i;
      const m = rawOption.match(rx);
      if (!m) return { visible: rawOption, link: null };

      const parenAll = m[0];
      const idx = rawOption.indexOf(parenAll);
      const visible = rawOption.slice(0, idx).replace(/\s+$/g, "");
      const inside = m[1];

      const m2 = inside.match(/OPCION\s+(\d+)\s+DE\s+HEADER\s+(\d+)/i);
      if (!m2) return { visible, link: null };

      return {
        visible,
        link: { op: parseInt(m2[1], 10), header: parseInt(m2[2], 10) }
      };
    }

    function findNextFechaToken(str, startAt){
      // 1) Preferir "FECHA" (con comillas)
      const q = str.indexOf('"FECHA"', startAt);
      if (q !== -1) return { type: "date", index: q, length: 7 };

      // 2) FECHA suelta, pero SOLO si NO está seguida de espacios + letra (para no capturar "FECHA DE ...")
      // Buscamos ocurrencias de FECHA y validamos contexto
      const word = "FECHA";
      let i = str.indexOf(word, startAt);
      while (i !== -1){
        const before = i - 1 >= 0 ? str[i - 1] : "";
        const after = i + word.length < str.length ? str[i + word.length] : "";

        // límites de palabra (antes y después no deben ser letras/números/underscore)
        const isBoundaryBefore = !before || !(/[A-Za-zÁÉÍÓÚÑáéíóúñ0-9_]/).test(before);
        const isBoundaryAfter = !after || !(/[A-Za-zÁÉÍÓÚÑáéíóúñ0-9_]/).test(after);

        // después de FECHA: si hay espacios y luego letra, NO es placeholder (ej: "FECHA DE")
        let j = i + word.length;
        while (j < str.length && str[j] === " ") j++;
        const nextChar = j < str.length ? str[j] : "";
        const followedByLetter = nextChar && (/[A-Za-zÁÉÍÓÚÑáéíóúñ]/).test(nextChar);

        if (isBoundaryBefore && isBoundaryAfter && !followedByLetter){
          return { type: "date", index: i, length: 5 };
        }
        i = str.indexOf(word, i + word.length);
      }
      return null;
    }

    function renderTextWithFields(raw, fieldPrefix){
      // Inserta inputs por ** y date inputs por FECHA/"FECHA" en la posición exacta.
      const frag = document.createDocumentFragment();
      let s = raw;
      let pos = 0;
      let textInputCount = 0;
      let dateInputCount = 0;

      while (pos < s.length){
        const idxStars = s.indexOf("**", pos);
        const fechaTok = findNextFechaToken(s, pos);

        let next = null;
        if (idxStars !== -1) next = { type: "text", index: idxStars, length: 2 };
        if (fechaTok && (!next || fechaTok.index < next.index)) next = fechaTok;

        if (!next){
          frag.appendChild(document.createTextNode(s.slice(pos)));
          break;
        }

        // texto antes del token
        if (next.index > pos){
          frag.appendChild(document.createTextNode(s.slice(pos, next.index)));
        }

        if (next.type === "text"){
          textInputCount++;
          const inp = document.createElement("input");
          inp.type = "text";
          inp.setAttribute("data-field", "text");
          inp.id = `${fieldPrefix}_t${textInputCount}`;
          inp.addEventListener("input", () => updateNarrativa());
          frag.appendChild(inp);
        } else if (next.type === "date"){
          dateInputCount++;
          const inp = document.createElement("input");
          inp.type = "date";
          inp.setAttribute("data-field", "date");
          inp.setAttribute("data-date", "1");
          inp.id = `${fieldPrefix}_d${dateInputCount}`;
          inp.addEventListener("input", () => updateNarrativa());
          frag.appendChild(inp);
        }

        pos = next.index + next.length;
      }

      return frag;
    }

    function formatDateDDMMYYYY(iso){
      // iso esperado: YYYY-MM-DD
      if (!iso || typeof iso !== "string") return "";
      const m = iso.match(/^(\d{4})-(\d{2})-(\d{2})$/);
      if (!m) return "";
      return `${m[3]}/${m[2]}/${m[1]}`;
    }

    function escapeHtml(s){
      return String(s)
        .replace(/&/g, "&amp;")
        .replace(/</g, "&lt;")
        .replace(/>/g, "&gt;")
        .replace(/"/g, "&quot;")
        .replace(/'/g, "&#39;");
    }

    function collectCompositeText(rootEl){
      // Reconstruye texto respetando inputs ** y FECHA dentro del elemento (ignorando checkbox)
      let out = "";

      function walk(node){
        if (node.nodeType === Node.TEXT_NODE){
          out += node.nodeValue;
          return;
        }
        if (node.nodeType !== Node.ELEMENT_NODE) return;

        const el = node;

        if (el.tagName === "INPUT"){
          const type = (el.getAttribute("type") || "").toLowerCase();
          if (type === "checkbox") return; // NO entra a narrativa como texto
          if (type === "text"){
            const v = (el.value || "").trim();
            out += v ? v : "____";
            return;
          }
          if (type === "date"){
            const v = (el.value || "").trim();
            const f = formatDateDDMMYYYY(v);
            out += f ? f : "____";
            return;
          }
        }

        if (el.tagName === "SELECT"){
          out += (el.value || "");
          return;
        }

        for (const child of el.childNodes) walk(child);
      }

      walk(rootEl);
      return out;
    }

    function resolveTargetId(link, groups){
      // 1) intentar como "HEADER Y" = índice de grupo (orden)
      const direct = `h${link.header}_op${link.op}`;
      if (document.getElementById(direct)) return direct;

      // 2) intentar como "HEADER Y" = número N del comando (primera ocurrencia)
      const foundIdx = groups.findIndex(g => g.n === link.header);
      if (foundIdx !== -1){
        const alt = `h${foundIdx + 1}_op${link.op}`;
        if (document.getElementById(alt)) return alt;
      }
      return direct; // fallback
    }

    function buildUI(){
      const groups = parseHeadersAndOptions(COMANDOS);
      const app = document.getElementById("app");
      app.innerHTML = "";

      groups.forEach((g, groupIdx) => {
        const hidx = groupIdx + 1;

        const grupo = document.createElement("div");
        grupo.className = "grupo";
        grupo.dataset.slashes = String(g.slashes ?? 0);
        grupo.dataset.hidx = String(hidx);
        grupo.dataset.hnum = String(g.n);

        const { tag, cls } = headingTagForN(g.n);
        const h = document.createElement(tag);
        if (cls) h.className = cls;

        // header con ** y FECHA
        const headerFieldPrefix = `h${hidx}_hdr`;
        h.appendChild(renderTextWithFields(g.titleRaw, headerFieldPrefix));
        grupo.appendChild(h);

        // opciones
        g.options.forEach((rawOpt, optIdx) => {
          const { visible, link } = extractLinkCommand(rawOpt);

          const label = document.createElement("label");

          const cb = document.createElement("input");
          cb.type = "checkbox";
          cb.id = `h${hidx}_op${optIdx + 1}`;

          if (link){
            cb.dataset.linkPending = JSON.stringify(link);
          }

          cb.addEventListener("change", () => {
            // aplicar enlace si existe
            if (cb.dataset.link){
              const target = document.getElementById(cb.dataset.link);
              if (target) target.checked = cb.checked;
            }
            updateNarrativa();
          });

          label.appendChild(cb);
          label.appendChild(document.createTextNode(" "));

          const optFieldPrefix = `h${hidx}_op${optIdx + 1}`;
          label.appendChild(renderTextWithFields(visible, optFieldPrefix));

          grupo.appendChild(label);
        });

        app.appendChild(grupo);
      });

      // resolver data-link (si existieran comandos de conexión)
      const allCbs = Array.from(document.querySelectorAll('.grupo input[type="checkbox"][data-link-pending]'));
      allCbs.forEach(cb => {
        try{
          const link = JSON.parse(cb.dataset.linkPending);
          const targetId = resolveTargetId(link, groups);
          cb.dataset.link = targetId;
        } catch(e){
          // ignore
        } finally {
          delete cb.dataset.linkPending;
        }
      });

      // inicial
      updateNarrativa();
    }

    function updateNarrativa() {
      const checks = document.querySelectorAll("input[type=checkbox]");
      let narrativa = "";

      const grupos = Array.from(document.querySelectorAll(".grupo"));
      for (const grupo of grupos){
        const slashes = parseInt(grupo.dataset.slashes || "0", 10) || 0;
        const headerEl = grupo.querySelector("h1,h2,h3,h4,h5,h6");

        const anyChecked = !!grupo.querySelector('input[type="checkbox"]:checked');

        // inputs dentro del header con contenido (texto o fecha)
        let headerHasContent = false;
        if (headerEl){
          const headerInputs = Array.from(headerEl.querySelectorAll('input[type="text"], input[type="date"], select'));
          headerHasContent = headerInputs.some(el => (el.value || "").trim().length > 0);
        }

        const aportaTexto = anyChecked || headerHasContent;

        if (aportaTexto){
          const headerText = headerEl ? collectCompositeText(headerEl).replace(/\s+$/g, "") : "";

          const checkedBoxes = Array.from(grupo.querySelectorAll('label > input[type="checkbox"]:checked'));
          const optionTexts = checkedBoxes.map(cb => {
            const label = cb.closest("label");
            return label ? collectCompositeText(label).replace(/\s+$/g, "") : "";
          }).filter(Boolean);

          const opcionesMarcadas = optionTexts.join(" ");

          narrativa += `${headerText} ${opcionesMarcadas} `;

          for (let i = 0; i < slashes; i++){
            narrativa += "\n\n";
          }
        }
      }

      // Render en <p> manteniendo segmentos vacíos
      const partes = narrativa.split("\n\n"); // mantiene vacíos intermedios y finales
      let htmlDeParrafos = "";
      for (const seg of partes){
        if (seg === ""){
          htmlDeParrafos += "<p>&nbsp;</p>";
        } else {
          htmlDeParrafos += `<p>${escapeHtml(seg.replace(/\s+$/g, ""))}</p>`;
        }
      }

      document.getElementById("resultado").innerHTML = htmlDeParrafos;
    }

    // construir UI al cargar
    buildUI();
  </script>
</body>
</html>

