# CDRPT1
Calculadora de Risco para Trade 
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Calculadora de Risco</title>
<style>
    body {
        font-family: Arial, sans-serif;
        background: #0f172a;
        color: white;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
    }

    .container {
        background: #1e293b;
        padding: 30px;
        border-radius: 15px;
        width: 320px;
        box-shadow: 0 0 20px rgba(0,0,0,0.5);
    }

    h2 {
        text-align: center;
        margin-bottom: 20px;
    }

    input {
        width: 100%;
        padding: 10px;
        margin: 8px 0;
        border-radius: 8px;
        border: none;
    }

    button {
        width: 100%;
        padding: 10px;
        margin-top: 10px;
        border-radius: 8px;
        border: none;
        background: #22c55e;
        color: white;
        font-weight: bold;
        cursor: pointer;
    }

    .result {
        margin-top: 15px;
        text-align: center;
        font-size: 18px;
        font-weight: bold;
    }
</style>
</head>
<body>

<div class="container">
    <h2>Calculadora de Risco</h2>

    <input type="number" id="capital" placeholder="Capital total (R$)">
    <input type="number" id="risco" placeholder="Risco por trade (%)">
    <input type="number" id="stop" placeholder="Stop em pontos">

    <button onclick="calcular()">Calcular</button>

    <div class="result" id="resultado"></div>
</div>

<script>
function calcular() {
    let capital = parseFloat(document.getElementById("capital").value);
    let riscoPercentual = parseFloat(document.getElementById("risco").value);
    let stop = parseFloat(document.getElementById("stop").value);

    if (!capital || !riscoPercentual || !stop) {
        document.getElementById("resultado").innerText = "Preencha todos os campos.";
        return;
    }

    let riscoReais = capital * (riscoPercentual / 100);
    let tamanhoPosicao = riscoReais / stop;

    document.getElementById("resultado").innerText =
        "Você pode perder até R$ " + riscoReais.toFixed(2) +
        "\nTamanho da posição: " + tamanhoPosicao.toFixed(2) + " contratos";
}
</script>

</body>
</html>
