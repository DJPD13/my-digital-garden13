---
{"dg-publish":true,"permalink":"/digital-garden/calculos/lev-ped-calc/","dgPassFrontmatter":true}
---

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Calculadora de Velocidad de Infusión</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f4f6f8;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .card {
            background: white;
            padding: 25px;
            border-radius: 10px;
            width: 360px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }

        h2 {
            text-align: center;
        }

        .rules {
            font-size: 14px;
            background: #eef3f7;
            padding: 12px;
            border-radius: 6px;
            margin-bottom: 15px;
        }

        input {
            width: 100%;
            padding: 10px;
            font-size: 16px;
            margin: 10px 0;
        }

        button {
            padding: 10px;
            width: 100%;
            font-size: 16px;
            background: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        button:hover {
            background: #0056b3;
        }

        .result {
            margin-top: 15px;
            font-size: 18px;
            font-weight: bold;
            text-align: center;
        }
    </style>
</head>
<body>

<div class="card">
    <h2>Velocidad de Infusión</h2>

    <div class="rules">
        <strong>Reglas de cálculo:</strong><br>
        • 4 mL/kg/h para los primeros 10 kg<br>
        • 2 mL/kg/h para los siguientes 10 kg<br>
        • 1 mL/kg/h para todos los kg adicionales
    </div>

    <label for="peso">Peso (kg):</label>
    <input type="number" id="peso" min="0" step="0.1" placeholder="Ej. 18">

    <button onclick="calcular()">Calcular</button>

    <div class="result" id="resultado"></div>
</div>

<script>
    function calcular() {
        const peso = parseFloat(document.getElementById("peso").value);
        let velocidad = 0;

        if (isNaN(peso) || peso <= 0) {
            document.getElementById("resultado").innerText = "Ingrese un peso válido";
            return;
        }

        if (peso <= 10) {
            velocidad = peso * 4;
        } else if (peso <= 20) {
            velocidad = (10 * 4) + ((peso - 10) * 2);
        } else {
            velocidad = (10 * 4) + (10 * 2) + ((peso - 20) * 1);
        }

        document.getElementById("resultado").innerText =
            `Velocidad: ${velocidad.toFixed(1)} mL/h`;
    }
</script>

</body>
</html>
