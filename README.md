<!DOCTYPE html>
<html lang="ro">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ToolBoxRO - Instrumente gratuite</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: Arial, sans-serif;
      background: #f4f6f8;
      color: #222;
    }

    header {
      background: #111827;
      color: white;
      text-align: center;
      padding: 35px 20px;
    }

    header h1 {
      font-size: 38px;
      margin-bottom: 10px;
    }

    header p {
      color: #cbd5e1;
      font-size: 17px;
    }

    .container {
      max-width: 1000px;
      margin: 30px auto;
      padding: 0 15px;
    }

    .tools {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 20px;
    }

    .card {
      background: white;
      border-radius: 15px;
      padding: 25px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.08);
    }

    .card h2 {
      margin-bottom: 10px;
      font-size: 22px;
    }

    .card p {
      color: #666;
      margin-bottom: 18px;
    }

    input {
      width: 100%;
      padding: 12px;
      margin-bottom: 10px;
      border: 1px solid #ddd;
      border-radius: 8px;
      font-size: 16px;
    }

    button {
      width: 100%;
      padding: 12px;
      border: none;
      border-radius: 8px;
      background: #2563eb;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }

    button:hover {
      background: #1d4ed8;
    }

    .result {
      margin-top: 15px;
      padding: 12px;
      background: #eef2ff;
      border-radius: 8px;
      font-weight: bold;
      min-height: 20px;
    }

    footer {
      text-align: center;
      padding: 30px;
      margin-top: 30px;
      color: #777;
    }

    @media (max-width: 600px) {
      header h1 {
        font-size: 30px;
      }

      .container {
        margin-top: 20px;
      }
    }
  </style>
</head>

<body>

<header>
  <h1>🧰 ToolBoxRO</h1>
  <p>Instrumente online gratuite și ușor de folosit</p>
</header>

<div class="container">

  <div class="tools">

    <!-- PROCENTAJ -->
    <div class="card">
      <h2>📊 Calculator procentaj</h2>
      <p>Calculează cât reprezintă un procent dintr-un număr.</p>

      <input type="number" id="percent" placeholder="Procent (%)">
      <input type="number" id="number" placeholder="Număr">

      <button onclick="calculatePercent()">Calculează</button>

      <div class="result" id="percentResult"></div>
    </div>

    <!-- TVA -->
    <div class="card">
      <h2>💰 Calculator TVA</h2>
      <p>Calculează prețul cu TVA inclus.</p>

      <input type="number" id="price" placeholder="Preț fără TVA">
      <input type="number" id="vat" placeholder="TVA (%)" value="20">

      <button onclick="calculateVAT()">Calculează</button>

      <div class="result" id="vatResult"></div>
    </div>

    <!-- MEDIE -->
    <div class="card">
      <h2>🎓 Calculator medie</h2>
      <p>Introdu notele separate prin virgulă.</p>

      <input type="text" id="grades" placeholder="Ex: 8, 9, 10, 7">

      <button onclick="calculateAverage()">Calculează</button>

      <div class="result" id="averageResult"></div>
    </div>

    <!-- CONVERSIE -->
    <div class="card">
      <h2>⚖️ Kg → Livre</h2>
      <p>Convertește kilograme în livre.</p>

      <input type="number" id="kg" placeholder="Kilograme">

      <button onclick="convertKg()">Convertește</button>

      <div class="result" id="kgResult"></div>
    </div>

    <!-- GENERATOR PAROLE -->
    <div class="card">
      <h2>🔐 Generator de parole</h2>
      <p>Generează o parolă aleatorie.</p>

      <button onclick="generatePassword()">Generează parola</button>

      <div class="result" id="passwordResult"></div>
    </div>

    <!-- CALCULATOR -->
    <div class="card">
      <h2>🧮 Calculator simplu</h2>
      <p>Adună două numere.</p>

      <input type="number" id="num1" placeholder="Primul număr">
      <input type="number" id="num2" placeholder="Al doilea număr">

      <button onclick="addNumbers()">Calculează</button>

      <div class="result" id="calculatorResult"></div>
    </div>

  </div>

</div>

<footer>
  © 2026 ToolBoxRO — Instrumente online gratuite
</footer>

<script>

function calculatePercent() {
  let percent = Number(document.getElementById("percent").value);
  let number = Number(document.getElementById("number").value);

  let result = (percent / 100) * number;

  document.getElementById("percentResult").innerText =
    "Rezultat: " + result;
}

function calculateVAT() {
  let price = Number(document.getElementById("price").value);
  let vat = Number(document.getElementById("vat").value);

  let result = price + (price * vat / 100);

  document.getElementById("vatResult").innerText =
    "Preț cu TVA: " + result.toFixed(2);
}

function calculateAverage() {
  let input = document.getElementById("grades").value;

  let grades = input
    .split(",")
    .map(Number)
    .filter(n => !isNaN(n));

  if (grades.length === 0) {
    document.getElementById("averageResult").innerText =
      "Introdu cel puțin o notă.";
    return;
  }

  let sum = grades.reduce((a, b) => a + b, 0);
  let average = sum / grades.length;

  document.getElementById("averageResult").innerText =
    "Media: " + average.toFixed(2);
}

function convertKg() {
  let kg = Number(document.getElementById("kg").value);

  let pounds = kg * 2.20462;

  document.getElementById("kgResult").innerText =
    "Rezultat: " + pounds.toFixed(2) + " lb";
}

function generatePassword() {
  let characters =
    "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%^&*";

  let password = "";

  for (let i = 0; i < 12; i++) {
    password += characters.charAt(
      Math.floor(Math.random() * characters.length)
    );
  }

  document.getElementById("passwordResult").innerText =
    password;
}

function addNumbers() {
  let num1 = Number(document.getElementById("num1").value);
  let num2 = Number(document.getElementById("num2").value);

  document.getElementById("calculatorResult").innerText =
    "Rezultat: " + (num1 + num2);
}

</script>

</body>
</html>