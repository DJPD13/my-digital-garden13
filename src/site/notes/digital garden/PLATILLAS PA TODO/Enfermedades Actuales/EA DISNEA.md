---
{"dg-publish":true,"permalink":"/digital-garden/platillas-pa-todo/enfermedades-actuales/ea-disnea/","dgPassFrontmatter":true}
---


## Síntomas
- [ ] Fiebre > El paciente presenta fiebre.
- [ ] Dolor abdominal > Se reporta dolor abdominal.
- [ ] Erupción cutánea > Se observa erupción cutánea.

---

## Narrativa generada
```dataviewjs
let inicio = "Resumen clínico: ";
let cierre = " Fin del reporte.";

let texto = "";
for (let line of dv.current().file.tasks) {
    if (line.completed) {
        let parts = line.text.split(">");
        if (parts.length > 1) {
            texto += parts[1].trim() + " ";
        }
    }
}

dv.paragraph(inicio + texto.trim() + cierre);

