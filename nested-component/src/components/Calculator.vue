<template>
    <h1>Calculator</h1>
    <div class="calculator">
      <div class="display">{{ current }}</div>
      <div class="buttons">
        <button class="button-clear" @click="clear">C</button>
        <button @click="append('7')">7</button>
        <button @click="append('8')">8</button>
        <button @click="append('9')">9</button>
        <button @click="append('/')">/</button>
        <button @click="append('4')">4</button>
        <button @click="append('5')">5</button>
        <button @click="append('6')">6</button>
        <button @click="append('*')">*</button>
        <button @click="append('1')">1</button>
        <button @click="append('2')">2</button>
        <button @click="append('3')">3</button>
        <button @click="append('-')">-</button>
        <button @click="append('0')">0</button>
        <button @click="append('.')">.</button>
        <button class="button-equal" @click="calculate">=</button>
        <button @click="append('+')">+</button>
      </div>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    name: 'Calculator',
    setup() {
      const current = ref('');
  
      const append = (char) => {
        current.value += char;
      };
  
      const clear = () => {
        current.value = '';
      };
  
      const calculate = () => {
        try {
          current.value = eval(current.value).toString();
        } catch (e) {
          current.value = 'Error';
        }
      };
  
      return {
        current,
        append,
        clear,
        calculate,
      };
    },
  };
  </script>
  
  <style scoped>
  .calculator {
    width: 250px;
    margin: 50px auto;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
    background-color: #008558;
  }
  
  .display {
    grid-column: span 4;
    background: #333;
    color: #ffffff;
    padding: 15px;
    text-align: right;
    font-size: 2em;
    border-radius: 5px;
    margin-bottom: 10px;
    box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.1);
  }
  
  .buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
  }
  
  .buttons button {
    padding: 20px;
    font-size: 1.2em;
    cursor: pointer;
    border: none;
    border-radius: 5px;
    background: #585858;
    transition: background 0.2s;
  }
  
  .buttons button:hover {
    background: #ddd;
  }
  
  .buttons button:active {
    background: #ccc;
  }
  
  .button-clear {
    background-color: #f44336;
    color: white;
  }
  
  .button-clear:hover {
    background-color: #d32f2f;
  }
  
  .button-equal {
    background-color: #4caf50;
    color: white;
  }
  
  .button-equal:hover {
    background-color: #388e3c;
  }
  </style>
  