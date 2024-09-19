---
layout: page
title: Calculator
permalink: /calculator/
---
<!-- Calculator HTML Structure -->
<div id="calculator">
  <input type="text" id="display" disabled />
  <div class="buttons">
    <button onclick="clearDisplay()">C</button>
    <button onclick="appendCharacter('(')">(</button>
    <button onclick="appendCharacter(')')">)</button>
    <button onclick="deleteCharacter()">Del</button>
    <button onclick="appendCharacter('7')">7</button>
    <button onclick="appendCharacter('8')">8</button>
    <button onclick="appendCharacter('9')">9</button>
    <button onclick="appendCharacter('÷')">÷</button>
    <button onclick="appendCharacter('4')">4</button>
    <button onclick="appendCharacter('5')">5</button>
    <button onclick="appendCharacter('6')">6</button>
    <button onclick="appendCharacter('*')">x</button>
    <button onclick="appendCharacter('1')">1</button>
    <button onclick="appendCharacter('2')">2</button>
    <button onclick="appendCharacter('3')">3</button>
    <button onclick="appendCharacter('-')">-</button>
    <button onclick="appendCharacter('0')">0</button>
    <button onclick="appendCharacter('.')">.</button>
    <button onclick="calculate()">=</button>
    <button onclick="appendCharacter('+')">+</button>
  </div>
</div>
<!-- Calculator CSS -->
<style>
  #calculator {
    width: 200px;
    margin: 20px auto;
    padding: 20px;
    border: 2px solid #ccc;
    border-radius: 10px;
    background-color: #F9F9F9;
  }
  #display {
    width: 100%;
    height: 40px;
    font-size: 20px;
    text-align: right;
    margin-bottom: 10px;
  }
  .buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
  }
  button {
    width: 100%;
    padding: 10px;
    font-size: 18px;
    border: none;
    border-radius: 5px;
    background-color: #ddd;
    cursor: pointer;
  }
  button:hover {
    background-color: #ccc;
  }
</style>
<!-- Calculator JavaScript -->
<script>
  function appendCharacter(character) {
    document.getElementById('display').value += character;
  }
  function clearDisplay() {
    document.getElementById('display').value = '';
  }
  function deleteCharacter() {
    let current = document.getElementById('display').value;
    document.getElementById('display').value = current.slice(0, -1);
  }
  function calculate() {
    try {
      let result = eval(document.getElementById('display').value);
      document.getElementById('display').value = result;
    } catch (e) {
      document.getElementById('display').value = 'Error';
    }
  }
</script>