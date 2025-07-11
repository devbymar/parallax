<template>
  <div class="body">
  <div class="container">
    <form class="calculator">
      <input v-model="display" type="text" readonly class="value"  />
      <span class="num clear" @click="clearDisplay">c</span>
      <span class="num" @click="appendToDisplay('/')">/</span>
      <span class="num" @click="appendToDisplay('*')">*</span>
      <span class="num" @click="appendToDisplay('7')">7</span>
      <span class="num" @click="appendToDisplay('8')">8</span>
      <span class="num" @click="appendToDisplay('9')">9</span>
      <span class="num" @click="appendToDisplay('-')">-</span>
      <span class="num" @click="appendToDisplay('4')">4</span>
      <span class="num" @click="appendToDisplay('5')">5</span>
      <span class="num" @click="appendToDisplay('6')">6</span>
      <span class="num plus" @click="appendToDisplay('+')">+</span>
      <span class="num" @click="appendToDisplay('1')">1</span>
      <span class="num" @click="appendToDisplay('2')">2</span>
      <span class="num" @click="appendToDisplay('3')">3</span>
      <span class="num" @click="appendToDisplay('0')">0</span>
      <span class="num" @click="appendToDisplay('00')">00</span>
      <span class="num" @click="appendToDisplay('.')">.</span>
      <span class="num equal" @click="calculateResult">=</span>
    </form>
  </div>
</div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { VanillaTilt } from "../vanillatilt";

const display = ref('');

// Function to evaluate simple mathematical expressions
const evaluateExpression = (expr) => {
  // Remove whitespace
  expr = expr.replace(/\s+/g, '');

  // Handle division and multiplication first
  expr = expr.replace(/(\d+\.?\d*)\s*([*/])\s*(\d+\.?\d*)/g, (match, num1, op, num2) => {
    const n1 = parseFloat(num1);
    const n2 = parseFloat(num2);
    return op === '*' ? n1 * n2 : n1 / n2;
  });

  // Handle addition and subtraction
  expr = expr.replace(/(\d+\.?\d*)\s*([+-])\s*(\d+\.?\d*)/g, (match, num1, op, num2) => {
    const n1 = parseFloat(num1);
    const n2 = parseFloat(num2);
    return op === '+' ? n1 + n2 : n1 - n2;
  });

  return expr;
};

const appendToDisplay = (value) => {
  display.value += value;
};

const clearDisplay = () => {
  display.value = '';
};

const calculateResult = () => {
  try {
    display.value = evaluateExpression(display.value) || '';
  } catch (e) {
    display.value = 'Error';
  }
};

onMounted(() => {
  const calc = document.querySelector('.calculator');


      VanillaTilt.init(calc, {
        max: 25,
        speed: 400,
        glare: true,
        "max-glare": 1,
      });

})
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}
.body {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background: #091921;
}

.body::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(#e91e63, #ffc107);
  clip-path: circle(22% at 30% 20%);
}

.body::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(#ffffff, #da00ff);
  clip-path: circle(20% at 70% 90%);
}

.container {
  position: relative;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 6px;
  overflow: hidden;
  z-index: 10;
  backdrop-filter: blur(15px);
  border-top: 1px solid rgba(255, 255, 255, 0.02);
  border-left: 1px solid rgba(255, 255, 255, 0.02);
  box-shadow: 5px 5px 30px rgba(0, 0, 0, 0.02);

  width: 350px;
}

.container .calculator {
  position: relative;
  display: grid;


}

.container .calculator .value {
  grid-column: span 4;
  height: 140px;
  width: 300px;
  text-align: right;
  border: none;
  outline: none;
  padding: 10px;
  font-size: 30px;
  background: transparent;
  color: #fff;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  border-right: 1px solid rgba(255, 255, 255, 0.05);
}

.container .calculator span {
  display: grid;
  place-items: center;
  height: 75px;
  width: 75px;
  color: #fff;
  font-weight: 400;
  cursor: pointer;
  font-size: 20px;
  user-select: none;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  border-right: 1px solid rgba(255, 255, 255, 0.05);
}

.container .calculator span:hover {
  transition: 0s;
  background: rgba(255, 255, 255, 0.05);
}

.container .calculator span:active {
  background: #14ff47;
  color: #192f00;
  font-size: 24px;
  font-weight: 500;
}

.container .calculator .clear {
  grid-column: span 2;
  width: 150px;
  background: rgba(255, 255, 255, 0.05);
}

.plus {
  grid-row: span 2;
  width: 150px;
}

.equal {
  background: rgba(255, 255, 255, 0.05);
}
</style>
