
<!DOCTYPE html>
<html lang="bn">
<head>
  <meta charset="UTF-8">
  <title>SGPA & Advanced Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #e0f0ff;
      color: #222;
      max-width: 700px;
      margin: auto;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 0 15px rgba(0,0,0,0.2);
    }
    h1, h2, h3 {
      text-align: center;
    }
    h1 {
      color: #800000;
    }
    h2 {
      color: #004080;
    }
    h3 {
      color: #006699;
      font-size: 24px; /* Increased font size */
      font-weight: bold; /* Make it bold */
    }
    input, button {
      padding: 10px;
      margin: 10px 0;
      width: 100%;
      font-size: 16px;
    }
    button {
      background-color: #0077cc;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }
    button:hover {
      background-color: #005fa3;
    }
    .result {
      font-weight: bold;
      margin-top: 15px;
      white-space: pre-line;
    }
    .formula, .section {
      margin-top: 25px;
      padding: 15px;
      background-color: #d1ecf1;
      border-left: 5px solid #0c5460;
      font-size: 16px;
    }

    .adv-calc {
      background: #f8f9fa;
      border-radius: 12px;
      padding: 20px;
      margin-top: 30px;
      box-shadow: inset 0 0 10px #ccc;
    }
    .adv-display {
      width: 100%;
      height: 50px;
      font-size: 22px;
      text-align: right;
      padding: 10px;
      margin-bottom: 15px;
      border-radius: 8px;
      border: 1px solid #aaa;
      background: white;
    }
    .adv-buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }
    .adv-buttons button {
      padding: 15px;
      font-size: 18px;
      border-radius: 8px;
      background-color: #007bff;
      color: white;
      border: none;
    }
    .adv-buttons button:hover {
      background-color: #0056b3;
    }
    .adv-buttons .equal {
      background-color: #28a745;
    }
    .adv-buttons .equal:hover {
      background-color: #1e7e34;
    }
    .adv-buttons .clear {
      background-color: #dc3545;
    }
    .adv-buttons .clear:hover {
      background-color: #c82333;
    }
  </style>
</head>
<body>
  <h1>THE UNIVERSITY OF BURDWAN</h1>
  <h2>SGPA থেকে শতাংশ ও নম্বর ক্যালকুলেটর</h2>
  <h3>Created by SAGAR😄</h3> <!-- Increased font size and made it bold -->

  <div class="section">
    <label>SGPA দিন:</label>
    <input type="number" id="sgpa" step="0.01" placeholder="যেমন: 7.8">
    <label>মোট নম্বর (ঐচ্ছিক):</label>
    <input type="number" id="totalMarks" placeholder="যেমন: 275">
    <button onclick="calculate()">হিসাব করুন</button>
    <div class="result" id="result"></div>
  </div>

  <div class="formula">
    <strong>ফর্মুলা সমূহ:</strong><br><br>
    শতাংশ বের করার ফর্মুলা:<br>
    <code>Percentage = (SGPA × 10) – 5</code><br><br>
    মোট প্রাপ্ত নম্বর বের করার ফর্মুলা:<br>
    <code>Marks = (Percentage ÷ 100) × Total Marks</code>
  </div>

  <div class="section adv-calc">
    <h2>স্মার্ট ক্যালকুলেটর</h2>
    <input type="text" id="advDisplay" class="adv-display" readonly>
    <div class="adv-buttons">
      <button onclick="appendAdv('7')">7</button>
      <button onclick="appendAdv('8')">8</button>
      <button onclick="appendAdv('9')">9</button>
      <button onclick="appendAdv('/')">/</button>
      <button onclick="appendAdv('4')">4</button>
      <button onclick="appendAdv('5')">5</button>
      <button onclick="appendAdv('6')">6</button>
      <button onclick="appendAdv('*')">*</button>
      <button onclick="appendAdv('1')">1</button>
      <button onclick="appendAdv('2')">2</button>
      <button onclick="appendAdv('3')">3</button>
      <button onclick="appendAdv('-')">-</button>
      <button onclick="appendAdv('0')">0</button>
      <button onclick="appendAdv('.')">.</button>
      <button class="clear" onclick="clearAdv()">C</button>
      <button onclick="appendAdv('+')">+</button>
      <button class="equal" onclick="calculateAdv()" style="grid-column: span 4;">=</button>
    </div>
  </div>

  <script>
    function calculate() {
      const sgpa = parseFloat(document.getElementById("sgpa").value);
      const totalMarks = parseFloat(document.getElementById("totalMarks").value);
      const resultDiv = document.getElementById("result");
      if (isNaN(sgpa)) {
        resultDiv.innerText = "SGPA সঠিকভাবে লিখুন।";
        return;
      }
      const percentage = (sgpa * 10) - 5;
      let resultText = `তোমার শতাংশ: ${percentage.toFixed(2)}%`;
      if (!isNaN(totalMarks)) {
        const obtainedMarks = (percentage / 100) * totalMarks;
        resultText += `\nমোট ${totalMarks} এর মধ্যে তুমি পেয়েছো: ${obtainedMarks.toFixed(2)} নম্বর`;
      }
      resultDiv.innerText = resultText;
    }
    function appendAdv(val) {
      document.getElementById("advDisplay").value += val;
    }
    function clearAdv() {
      document.getElementById("advDisplay").value = "";
    }
    function calculateAdv() {
      try {
        const result = eval(document.getElementById("advDisplay").value);
        document.getElementById("advDisplay").value = result;
      } catch (e) {
        document.getElementById("advDisplay").value = "Error";
      }
    }
  </script>
</body>
</html>

<a href="https://sagar1204754.github.io/Marks-to-percentage-calculator/" target="_blank">
  Marks to Percentage Calculator
</a>

<a href="mailto:sagar8649885208@gmail.com">contact us</a>



<a href="https://sagar1204754.github.io/AGE-calculator/" target="_blank">AGE Calculator</a>
