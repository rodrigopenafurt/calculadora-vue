<template>
  <div id="app">
    <h1>Calculadora <strong>Web</strong></h1>

    <div class="input-container">
      <label for="num1">Primeiro valor:</label>
      <input v-model="num1" id="num1" type="number" @input="calcularResultado" />
    </div>

    <div class="input-container">
      <label for="num2">Segundo valor:</label>
      <input v-model="num2" id="num2" type="number" @input="calcularResultado" />
    </div>

    <div class="input-container">
      <label for="operacao">Operação:</label>
      <select v-model="operacao" id="operacao" @change="calcularResultado">
        <option value="+">Soma</option>
        <option value="-">Subtração</option>
        <option value="*">Multiplicação</option>
        <option value="/">Divisão</option>
      </select>
    </div>

    <div class="button-container">
      <button @click="calcularResultado" class="calcular-btn">Calcular</button>
      <button @click="limparResultado" class="limpar-btn">Limpar</button>
    </div>

    <p class="resultado">Resultado: {{ resultado }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num1: 0,
      operacao: "+",
      num2: 0,
      resultado: 0,
    };
  },
  methods: {
    calcularResultado() {
      switch (this.operacao) {
        case "+":
          this.resultado = this.num1 + this.num2;
          break;
        case "-":
          this.resultado = this.num1 - this.num2;
          break;
        case "*":
          this.resultado = this.num1 * this.num2;
          break;
        case "/":
          this.resultado = this.num1 / this.num2;
          break;
        default:
          this.resultado = 0;
      }
    },
    limparResultado() {
      this.num1 = 0;
      this.num2 = 0;
      this.resultado = 0;
    },
  },
};
</script>

<style>

body {
  background-color: #333;
}

#app {
  font-family: sans-serif;
  color: #333;
  margin: 30px auto;
  max-width: 400px;
  background-color: #0a2e37; 
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
  font-size: 2em;
  margin-bottom: 20px;
  text-align: center;
  color: #3498db; 
}

strong {
  font-weight: bold;
  color: #f80707;
}

.input-container {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
  color: #3498db;
}

input, select {
  width: 100%;
  padding: 8px;
  font-size: 1em;
  min-width: 100%;
  box-sizing: border-box;
  margin-top: 5px;
  border: 1px solid #bdc3c7;
  border-radius: 4px;
}

.button-container {
  display: flex;
  justify-content: flex-start;
  margin-bottom: 20px;
}

.calcular-btn {
  padding: 10px;
  font-size: 1em;
  background-color: #2ecc71;
  color: #fff;
  border: none;
  cursor: pointer;
  margin-right: 10px;
  border-radius: 4px;
}

.limpar-btn {
  padding: 10px;
  font-size: 1em;
  background-color: #e74c3c; 
  color: #fff;
  border: none;
  cursor: pointer;
  border-radius: 4px;
}

.calcular-btn:hover, .limpar-btn:hover {
  filter: brightness(110%);
}

.resultado {
  font-size: 1.2em;
  font-weight: bold;
  color: #3498db;
}
</style>
