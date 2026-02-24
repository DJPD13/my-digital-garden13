---
{"dg-publish":true,"permalink":"/digital-garden/1-ingreso/prueba-examen-fisico-2/","dgPassFrontmatter":true}
---

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Examen Físico · Narrativa Anidada</title>
    <style>
        body { font-family: 'Segoe UI', Roboto, system-ui, sans-serif; max-width: 1100px; margin: 2rem auto; padding: 0 20px; background: #f4f7fb; }
        h3 { margin: 1.5rem 0 0.5rem; border-bottom: 2px solid #b0c4de; padding-bottom: 0.2rem; color: #1e3a5f; display: flex; align-items: center; gap: 1rem; }
        .main-check { transform: scale(1.1); accent-color: #1e3a5f; width: 1.1rem; height: 1.1rem; }
        .var-container { background: white; border-radius: 16px; padding: 0.8rem 1.5rem 1.2rem; margin-bottom: 1.8rem; box-shadow: 0 8px 20px rgba(0,20,50,0.08); border: 1px solid #d9e6f2; }
        .sub-opciones { margin-left: 2rem; padding-left: 1rem; border-left: 3px solid #a3c0dd; margin-top: 0.8rem; display: none; }
        .sub-opciones.visible { display: block; }
        .opcion-item { margin: 0.7rem 0; display: flex; flex-wrap: wrap; align-items: baseline; gap: 0.5rem; }
        .opcion-item label { font-weight: 500; color: #0b2b44; min-width: 180px; }
        input[type="checkbox"] { margin-right: 8px; accent-color: #2b6a9e; transform: scale(1.05); }
        input[type="text"], select { padding: 6px 12px; border: 1px solid #bdc9d6; border-radius: 24px; font-size: 0.9rem; background: #f9fcff; transition: 0.15s; }
        input[type="text"]:focus, select:focus { border-color: #1e5a9b; outline: none; box-shadow: 0 0 0 3px rgba(30,90,155,0.15); }
        .sub-sub { margin-left: 2.2rem; padding-left: 1.2rem; border-left: 2px dashed #98b7d9; margin-top: 0.3rem; }
        .multi-text { display: block; margin: 0.5rem 1.5rem; padding: 0.8rem; background: #f0f5fb; border-radius: 12px; white-space: pre-wrap; font-family: 'Courier New', monospace; border: 1px solid #cdddec; color: #14471f; }
        button { background: #1e3a5f; color: white; border: none; font-size: 1.2rem; font-weight: 600; padding: 0.8rem 2.5rem; border-radius: 60px; cursor: pointer; margin: 25px 0 15px; box-shadow: 0 6px 14px rgba(0,40,80,0.25); transition: all 0.2s; border: 1px solid #326a9e; }
        button:hover { background: #143049; transform: translateY(-2px); box-shadow: 0 12px 22px rgba(0,55,100,0.3); }
        pre { background: #1a2634; color: #e3f0fd; padding: 1.5rem; border-radius: 24px; font-size: 0.95rem; line-height: 1.5; border: 1px solid #33495f; box-shadow: inset 0 0 10px #0f1a24; overflow-x: auto; white-space: pre-wrap; word-wrap: break-word; }
        .nota-pequeña { color: #4f6070; margin: -0.2rem 0 1rem 2rem; font-style: italic; font-size: 0.9rem; }
    </style>
</head>
<body>
    <h2 style="color:#10324e;">📋 Exploración física · generador anidado</h2>
    <p style="margin-top: -10px;">✔ Marca variable principal → aparecen subopciones. Anidamiento completo.</p>

    <!-- ################  CONTENEDORES DINÁMICOS (se llenan con JS)  ################ -->
    <div id="app-root"></div>

    <button onclick="updateNarrativa()">📄 Generar Narrativa</button>
    <pre id="resultado">- TENDENCIAS: NORMAL
- PIEL: NORMAL
- CABEZA: NORMAL
- CAVIDAD ORAL: NORMAL
- CUELLO: NORMAL
- TORAX: NORMAL
- ABDOMEN: NORMAL
- OSTEOMUSCULAR: NORMAL
- NEUROLOGICO: NORMAL</pre>

    <script>
        (function() {
            // -------------------------------------------------------------
            //  DATOS JERÁRQUICOS (extraídos de tu prompt)
            // -------------------------------------------------------------
            const variablesData = [
                {
                    nombre: "TENDENCIAS",
                    hijos: [
                        { texto: "HEMODINÁMICA:", hijos: [
                            { texto: "ESTABLE" },
                            { texto: "HIPOTENSIÓN **PRESIÓN: ** MMHG" }
                        ]},
                        { texto: "RESPIRATORIA:", hijos: [
                            { texto: "SIN ALTERACIONES" },
                            { texto: "TAQUIPNEA **FR: ** RPM" },
                            { texto: "USANDO OXÍGENO POR ***1.CANULA NASAL 2.MASCARILLA 3.VENTILACIÓN MECÁNICA" }
                        ]},
                        { texto: "HIDRATACIÓN:", hijos: [
                            { texto: "NORMOHIDRATADO" },
                            { texto: "SIGNOS DE DESHIDRATACIÓN (=>>>Mucosas orales secas, pliegue cutáneo persistente, ojos hundidos.<<<)" }
                        ]}
                    ]
                },
                {
                    nombre: "PIEL",
                    hijos: [
                        { texto: "COLORACIÓN:", hijos: [
                            { texto: "NORMOCÓRICA" },
                            { texto: "ICTÉRICA" },
                            { texto: "PALIDEZ **GRADO: **" },
                            { texto: "CIANÓTICA" }
                        ]},
                        { texto: "LESIONES:", hijos: [
                            { texto: "SIN LESIONES APARENTES" },
                            { texto: "MÁCULAS EN ***1.TÓRAX 2.ABDOMEN 3.EXTREMIDADES" },
                            { texto: "ERITEMA EN ZONA DE ***" },
                            { texto: "(CONECTAR CON OPCION ERITEMA EN ZONA DE DE HEADER PIEL)" }
                        ]}
                    ]
                },
                {
                    nombre: "CABEZA",
                    hijos: [
                        { texto: "FORMA:", hijos: [
                            { texto: "NORMOCÉFALA" },
                            { texto: "ASIMETRÍA **TIPO: **" }
                        ]},
                        { texto: "PALPACIÓN:", hijos: [
                            { texto: "SIN DOLOR" },
                            { texto: "DOLOR A LA PALPACIÓN EN ***1.REGIÓN FRONTAL 2.REGIÓN OCCIPITAL 3.REGIÓN TEMPORAL" }
                        ]}
                    ]
                },
                {
                    nombre: "CAVIDAD ORAL",
                    hijos: [
                        { texto: "MUCOSA:", hijos: [
                            { texto: "HÚMEDA" }, { texto: "SECA" }
                        ]},
                        { texto: "DIENTES:", hijos: [
                            { texto: "EN BUEN ESTADO" }, { texto: "EDÉNTULO PARCIAL" }, { texto: "EDÉNTULO TOTAL" }, { texto: "CARIES MÚLTIPLES" }
                        ]},
                        { texto: "FARINGE:", hijos: [
                            { texto: "SIN ERITEMA" }, { texto: "ERITEMATOSA" }, { texto: "CON EXUDADO (=>>>Amígdalas hipertróficas con exudado blanquecino.<<<)" }
                        ]}
                    ]
                },
                {
                    nombre: "CUELLO",
                    hijos: [
                        { texto: "MOVILIDAD:", hijos: [
                            { texto: "CONSERVADA" },
                            { texto: "DOLOROSA A LA ***1.FLEXIÓN 2.EXTENSIÓN 3.ROTACIÓN" }
                        ]},
                        { texto: "PALPACIÓN:", hijos: [
                            { texto: "SIN MASAS" },
                            { texto: "ADENOPATÍAS **LOCALIZACIÓN: **" },
                            { texto: "TIROIDES ***1.PALPABLE NO VISIBLE 2.AUMENTADO DE TAMAÑO 3.NÓDULOS" }
                        ]}
                    ]
                },
                {
                    nombre: "TORAX",
                    hijos: [
                        { texto: "INSPECCIÓN:", hijos: [
                            { texto: "SIMÉTRICO" }, { texto: "ASIMETRÍA **DESCRIPCIÓN: **" }
                        ]},
                        { texto: "PALPACIÓN:", hijos: [
                            { texto: "SIN DOLOR" }, { texto: "DOLOR A LA PALPACIÓN EN ***1.REGIÓN COSTAL 2.ESTERNÓN 3.COLUMNA DORSAL" }
                        ]},
                        { texto: "AUSCULTACIÓN:", hijos: [
                            { texto: "VENTILACIÓN CONSERVADA" }, { texto: "ESTERTORES EN ***1.BASALES 2.APICALES 3.GENERALIZADOS" }, { texto: "SIBILANCIAS ESPIRATORIAS" }
                        ]}
                    ]
                },
                {
                    nombre: "ABDOMEN",
                    hijos: [
                        { texto: "FORMA:", hijos: [
                            { texto: "PLANO" }, { texto: "DISTENDIDO" }, { texto: "GLOBOSO" }
                        ]},
                        { texto: "PALPACIÓN:", hijos: [
                            { texto: "BLANDO, DEPRESIBLE" }, { texto: "DOLOROSO EN ***1.HIPOCONDRIO DERECHO 2.HIPOCONDRIO IZQUIERDO 3.FOSA ILÍACA DERECHA 4.FOSA ILÍACA IZQUIERDA" }, { texto: "CON MASA PALPABLE **DESCRIPCIÓN: **" }
                        ]},
                        { texto: "RUIDOS HIDROAÉREOS:", hijos: [
                            { texto: "PRESENTES" }, { texto: "AUMENTADOS" }, { texto: "DISMINUIDOS" }
                        ]}
                    ]
                },
                {
                    nombre: "OSTEOMUSCULAR",
                    hijos: [
                        { texto: "EXTREMIDADES SUPERIORES:", hijos: [
                            { texto: "SIN LESIONES EXTERNAS" }, { texto: "ESTADO NEUROVASCULAR CONSERVADO" }, { texto: "NORMOTÉRMICO" }, { texto: "SIN DEFORMIDAD" }, { texto: "DEFORMIDAD EN ***1.VALGO 2.VARO 3.FLEXIÓN" }
                        ]},
                        { texto: "COLUMNA:", hijos: [
                            { texto: "SIN DOLOR A LA PALPACIÓN" }, { texto: "CIFOSIS" }, { texto: "ESCOLIOSIS **ÁNGULO DE ** GRADOS" }
                        ]},
                        { texto: "ARTICULACIÓN COXOFEMORAL:", hijos: [
                            { texto: "SIN ALTERACIONES" }, { texto: "DOLOR A LA MOVILIZACIÓN ***1.LEVE 2.MODERADO 3.SEVERO" }
                        ]},
                        { texto: "EXTREMIDADES INFERIORES:", hijos: [
                            { texto: "(CONECTAR CON OPCION EXTREMIDADES SUPERIORES DE HEADER OSTEOMUSCULAR)" },
                            { texto: "EDEMA + (CONECTAR CON OPCION TENDENCIAS DE HEADER TORAX)" },
                            { texto: "PULSOS PEDIOS PALPABLES" },
                            { texto: "VARICES (=>>>Várices de gran tamaño en miembro inferior izquierdo, con edema asociado. Piel circundante con signos de estasis.<<<)" }
                        ]}
                    ]
                },
                {
                    nombre: "NEUROLOGICO",
                    hijos: [
                        { texto: "ESTADO DE CONCIENCIA:", hijos: [
                            { texto: "ALERTA" }, { texto: "SOMNOLIENTO" }, { texto: "CONFUSO" }, { texto: "INCONSCIENTE **GLASGOW: **" }
                        ]},
                        { texto: "MOTILIDAD:", hijos: [
                            { texto: "CONSERVADA" }, { texto: "DEBILIDAD EN ***1.HEMICUE尔PO DERECHO 2.HEMICUE尔PO IZQUIERDO 3.MIEMBRO SUPERIOR 4.MIEMBRO INFERIOR" }
                        ]},
                        { texto: "SENSIBILIDAD:", hijos: [
                            { texto: "CONSERVADA" }, { texto: "PARESTESIAS EN **LOCALIZACIÓN: **" }
                        ]},
                        { texto: "REFLEJOS:", hijos: [
                            { texto: "NORMORREFLEXIA" }, { texto: "HIPORREFLEXIA" }, { texto: "HIPERRREFLEXIA" }
                        ]}
                    ]
                }
            ];

            // -------------------------------------------------------------
            //  GENERAR HTML DE TODA LA ESTRUCTURA (anidada)
            // -------------------------------------------------------------
            let globalIdCounter = 1;  // para generar ids únicos tipo hX_opY (Y único)
            const headerNombres = variablesData.map(v => v.nombre);

            function buildOptionHTML(opcion, path = [], nivel = 1) {
                if (!opcion.hijos || opcion.hijos.length === 0) {
                    // es hoja (último nivel) → puede tener **, ***, =>>>
                    return generarItemHoja(opcion.texto, path, nivel);
                } else {
                    // Es un "header" intermedio: ej "HEMODINÁMICA:"  → con checkbox que despliega sus hijos
                    const idUnico = `ch_${globalIdCounter++}`;
                    const safeText = opcion.texto.replace(/:/g, ''); // mostrar sin dos puntos extra
                    let html = `<div class="opcion-item" style="align-items: flex-start;">`;
                    html += `<input type="checkbox" class="subgroup-toggle" id="${idUnico}" data-path="${path.join('|')}|${opcion.texto}">`;
                    html += `<label for="${idUnico}" style="font-weight:600; color:#004070;"><strong>${opcion.texto}</strong></label>`;
                    html += `</div>`;
                    html += `<div class="sub-sub sub-opciones" id="sub_${idUnico}">`;
                    opcion.hijos.forEach(hijo => {
                        html += buildOptionHTML(hijo, [...path, opcion.texto], nivel + 1);
                    });
                    html += `</div>`;
                    // lógica con js para mostrar/ocultar (se añadirá al final)
                    return html;
                }
            }

            function generarItemHoja(textoCrudo, path, nivel) {
                const idUnico = `opt_${globalIdCounter++}`;
                // Detectar conectores (CONECTAR CON)
                let textoLabel = textoCrudo;
                let esConector = false;
                let linkTarget = null;
                const matchConector = textoCrudo.match(/\(CONECTAR CON OPCION (.*?) DE HEADER (.*?)\)/);
                if (matchConector) {
                    esConector = true;
                    // No mostramos el paréntesis en el label
                    textoLabel = textoCrudo.replace(/\s*\(CONECTAR CON OPCION .*? DE HEADER .*?\)/, '').trim();
                    linkTarget = { opcion: matchConector[1].trim(), header: matchConector[2].trim() };
                }

                // Detectar si contiene **, ***, =>>>
                // Prioridad: =>>> (multilínea) luego *** y ** (no deberían combinarse, pero priorizamos)
                let inputHTML = '';
                let tipo = 'simple';
                let prefijo = textoLabel, sufijo = '', dropdownOps = [], multilineaTexto = '';

                if (textoLabel.includes('=>>>') && textoLabel.includes('<<<')) {
                    tipo = 'multiline';
                    const parts = textoLabel.split('=>>>');
                    prefijo = parts[0].trim();
                    const resto = parts[1];
                    multilineaTexto = resto.split('<<<')[0].trim();
                    // el sufijo después de <<< (si existe)
                    sufijo = resto.includes('<<<') ? resto.split('<<<')[1] || '' : '';
                } else if (textoLabel.includes('***')) {
                    tipo = 'dropdown';
                    const partes = textoLabel.split('***');
                    prefijo = partes[0];
                    const resto = partes[1];
                    // formato: "1.OPCION 2.OPCION2 3.OPCION3"
                    const opcionesRaw = resto.split(/\s+\d+\./); // separador por " nº."
                    // la primera parte tiene el 1. incluido, lo procesamos
                    const matchOpts = resto.match(/(\d+\.[^\d]+)/g);
                    if (matchOpts) {
                        dropdownOps = matchOpts.map(opt => opt.replace(/^\d+\./, '').trim());
                    }
                    // sufijo puede ir después del último código? lo dejamos vacío
                } else if (textoLabel.includes('**')) {
                    tipo = 'input';
                    const partes = textoLabel.split('**');
                    prefijo = partes[0];
                    sufijo = partes[1] || '';
                }

                // construcción del label y elementos extra
                let html = `<div class="opcion-item" data-leaf="true">`;
                html += `<input type="checkbox" class="leaf-check" id="${idUnico}" data-tipo="${tipo}" data-prefijo="${prefijo.replace(/"/g, '&quot;')}" data-sufijo="${sufijo.replace(/"/g, '&quot;')}"`;
                if (esConector && linkTarget) {
                    html += ` data-link-header="${linkTarget.header}" data-link-opcion="${linkTarget.opcion}"`;
                }
                html += `> `;
                html += `<label for="${idUnico}">${prefijo || '(opción)'}`;

                if (tipo === 'input') {
                    html += `</label> <input type="text" class="dinamic-input" data-for="${idUnico}" placeholder="___" style="width:110px;"> <label>${sufijo}</label>`;
                } else if (tipo === 'dropdown') {
                    html += `</label> <select class="dinamic-select" data-for="${idUnico}">`;
                    dropdownOps.forEach((opt, idx) => { html += `<option value="${opt}">${opt}</option>`; });
                    html += `</select> <label>${sufijo}</label>`;
                } else if (tipo === 'multiline') {
                    html += `</label> <span style="display:none;" class="multiline-store" data-for="${idUnico}" data-multitext="${multilineTexto.replace(/"/g, '&quot;')}"></span>`;
                } else {
                    html += `</label>`;
                }

                html += `</div>`;
                return html;
            }

            // Montar HTML completo en #app-root
            function renderCompleto() {
                let htmlFinal = '';
                variablesData.forEach((varPrinc, idx) => {
                    const varName = varPrinc.nombre;
                    const mainId = `main_${varName.replace(/\s/g,'')}`;
                    htmlFinal += `<div class="var-container">`;
                    htmlFinal += `<h3><input type="checkbox" class="main-check" id="${mainId}" data-var="${varName}"> <label for="${mainId}"><strong>${varName}</strong></label></h3>`;
                    htmlFinal += `<div class="sub-opciones" id="sub_${mainId}">`;
                    // hijos de primer nivel (HEMODINÁMICA:, COLORACIÓN:, etc)
                    varPrinc.hijos.forEach(hijo => {
                        htmlFinal += buildOptionHTML(hijo, [varName]);
                    });
                    htmlFinal += `</div>`;
                    htmlFinal += `</div>`;
                });
                document.getElementById('app-root').innerHTML = htmlFinal;

                // ----- Lógica de visibilidad anidada (toggle subgroups) -----
                document.querySelectorAll('.subgroup-toggle').forEach(cb => {
                    const subDiv = document.getElementById('sub_'+cb.id);
                    if (subDiv) {
                        cb.addEventListener('change', function(e) {
                            subDiv.classList.toggle('visible', this.checked);
                        });
                        // estado inicial
                        subDiv.classList.toggle('visible', cb.checked);
                    }
                });

                // Mostrar/ocultar hijos de la variable principal
                document.querySelectorAll('.main-check').forEach(mainCb => {
                    const container = document.getElementById('sub_'+mainCb.id);
                    if (container) {
                        mainCb.addEventListener('change', function(e) {
                            container.classList.toggle('visible', this.checked);
                        });
                        container.classList.toggle('visible', mainCb.checked);
                    }
                });

                // conectores (data-link)
                document.querySelectorAll('.leaf-check[data-link-header]').forEach(leaf => {
                    leaf.addEventListener('change', function(e) {
                        const targetHeader = this.dataset.linkHeader;
                        const targetOpcion = this.dataset.linkOpcion;
                        // Buscamos el checkbox hoja cuyo label contenga targetOpcion y esté bajo el header targetHeader
                        const allLeaves = document.querySelectorAll('.leaf-check');
                        for (let ch of allLeaves) {
                            const label = document.querySelector(`label[for="${ch.id}"]`);
                            if (label && label.innerText.includes(targetOpcion)) {
                                // Verificar que esté dentro del header correcto (sencillo: contenedor)
                                if (ch.closest('.var-container')?.querySelector(`.main-check[data-var="${targetHeader}"]`)) {
                                    ch.checked = this.checked; // sincronizar
                                }
                            }
                        }
                    });
                });
            }

            renderCompleto();

            // -------------------------------------------------------------
            //  NARRATIVA FINAL (updateNarrativa)
            // -------------------------------------------------------------
            window.updateNarrativa = function() {
                let narrativa = '';
                const mains = document.querySelectorAll('.main-check');
                mains.forEach(main => {
                    const varName = main.dataset.var;
                    const container = document.getElementById('sub_'+main.id);
                    const marcado = main.checked;
                    if (!marcado) {
                        narrativa += `- ${varName}: NORMAL\n`;
                        return;
                    }
                    // variable marcada: buscamos todas las hojas marcadas dentro de container
                    narrativa += `- ${varName}`;
                    const leaves = container.querySelectorAll('.leaf-check:checked');
                    if (leaves.length === 0) {
                        narrativa += `: (marcado sin opciones)\n`; // apenas
                    } else {
                        narrativa += `\n`; // nueva línea
                        leaves.forEach(leaf => {
                            const tipo = leaf.dataset.tipo || 'simple';
                            const prefijo = leaf.dataset.prefijo || '';
                            const sufijo = leaf.dataset.sufijo || '';
                            const labelFor = document.querySelector(`label[for="${leaf.id}"]`);
                            const textoBase = labelFor ? labelFor.innerText : prefijo;

                            let linea = `  - ${prefijo || textoBase}`;

                            if (tipo === 'input') {
                                const input = document.querySelector(`input.dinamic-input[data-for="${leaf.id}"]`);
                                const valor = input ? input.value : '';
                                linea = `  - ${prefijo}${valor}${sufijo}`;
                            } else if (tipo === 'dropdown') {
                                const select = document.querySelector(`select.dinamic-select[data-for="${leaf.id}"]`);
                                const valor = select ? select.value : '';
                                linea = `  - ${prefijo}${valor}${sufijo}`;
                            } else if (tipo === 'multiline') {
                                const store = document.querySelector(`.multiline-store[data-for="${leaf.id}"]`);
                                const multiline = store ? store.dataset.multitext : '';
                                linea = `  - ${prefijo}\n${multiline.split('\n').map(l => '    '+l).join('\n')}`;
                            } else {
                                linea = `  - ${textoBase}`;
                            }
                            narrativa += linea + '\n';
                        });
                    }
                });
                document.getElementById('resultado').innerText = narrativa.trim() || 'No hay elementos seleccionados';
            };
        })();
    </script>
    <!-- pequeño fix para mostrar toggles iniciales -->
    <style>
        .sub-opciones { display: none; }
        .sub-opciones.visible { display: block; }
        .sub-sub { display: none; }
        .subgroup-toggle:checked ~ .sub-sub { display: block; }
        /* ajuste para que funcione la regla con hermano general */
        .subgroup-toggle + label + .sub-sub { display: none; }
        .subgroup-toggle:checked + label + .sub-sub { display: block; }
    </style>
</body>
</html>