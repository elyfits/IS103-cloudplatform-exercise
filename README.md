# IS103-cloudplatform-exercise
<!DOCTYPE html>
<html lang="tl">
<head>
<meta charset="UTF-8">
<title>Simple Calculator</title>
<style>
  body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    background: #2c3e50;
    font-family: Arial, sans-serif;
  }

  .calculator {
    background: #34495e;
    padding: 20px;
    border-radius: 12px;
    box-shadow: 0 8px 20px rgba(0,0,0,0.4);
    width: 280px;
  }

  #display {
    width: 100%;
    height: 60px;
    font-size: 28px;
    text-align: right;
    margin-bottom: 15px;
    border: none;
    border-radius: 8px;
    padding: 0 10px;
    box-sizing: border-box;
    background: #ecf0f1;
  }

  .buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
  }

  button {
    padding: 18px;
    font-size: 18px;
    border: none;
    border-radius: 8px;
    background: #1abc9c;
    color: white;
    cursor: pointer;
    transition: background 0.2s;
  }

  button:hover {
    background: #16a085;
  }

  .operator {
    background: #e67e22;
  }

  .operator:hover {
    background: #d35400;
  }

  .equal {
    grid-column: span 2;
    background: #e74c3c;
  }

  .equal:hover {
    background: #c0392b;
  }

  .clear {
    background: #95a5a6;
  }

  .clear:hover {
    background: #7f8c8d;
  }
</style>
</head>
<body>

<div class="calculator">
  <input type="text" id="display" disabled>
  <div class="buttons">
    <button class="clear" onclick="clearDisplay()">C</button>
    <button onclick="deleteLast()">⌫</button>
    <button class="operator" onclick="appendValue('%')">%</button>
    <button class="operator" onclick="appendValue('/')">÷</button>

    <button onclick="appendValue('7')">7</button>
    <button onclick="appendValue('8')">8</button>
    <button onclick="appendValue('9')">9</button>
    <button class="operator" onclick="appendValue('*')">×</button>

    <button onclick="appendValue('4')">4</button>
    <button onclick="appendValue('5')">5</button>
    <button onclick="appendValue('6')">6</button>
    <button class="operator" onclick="appendValue('-')">−</button>

    <button onclick="appendValue('1')">1</button>
    <button onclick="appendValue('2')">2</button>
    <button onclick="appendValue('3')">3</button>
    <button class="operator" onclick="appendValue('+')">+</button>

    <button onclick="appendValue('0')">0</button>
    <button onclick="appendValue('.')">.</button>
    <button class="equal" onclick="calculate()">=</button>
  </div>
</div>

<script>
  const display = document.getElementById('display');

  function appendValue(value) {
    display.value += value;
  }

  function clearDisplay() {
    display.value = '';
  }

  function deleteLast() {
    display.value = display.value.slice(0, -1);
  }

  function calculate() {
    try {

      let expression = display.value.replace(/%/g, '/100');
      display.value = eval(expression);
    } catch (error) {
      display.value = 'Error';
    }
  }
</script>

</body>
</html>
