<template>
<div class="container">
  <div class="calculator">
    <h2>Calculadora Aritmética</h2>

    <div class="input-group">
      <input type="number" v-model.number="num1" placeholder="Digite um número">
      <select v-model="operacao">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">x</option>
        <option value="/">÷</option>
      </select>

      <input type="number" v-model.number="num2" placeholder="Digite um número">
    </div>

    <div class="result">
      <h3>Resultado: <span>{{ resultado() }}</span></h3>
    </div>
  </div>
</div>
</template>

<script>
  export default {
    data(){
      return {
        num1: 0,
        num2: 0,
        operacao: '+'
      }
    },
    computed: {
      resultado(){
        if(isNaN(this.num1) || isNaN(this.num2)) return 'Inválido';
        switch (this.operacao) {
          case '+': return this.num1 + this.num2;
          case '-': return this.num1 - this.num2;
          case '*': return this.num1 * this.num2;
          case '/': return this.num2 !== 0 ? (this.num1 / this.num2).toFixed(2) : 'Erro';
          default: return 0;
        }
      }
    }
  }
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(135deg, #89f7fe, #66a6ff);
}

/* Estilização da calculadora */
.calculator {
  max-width: 400px;
  padding: 10px 100px;
  border-radius: 12px;
  text-align: center;
  background: #ffffff;
  box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.2);
  transition: transform 0.2s ease-in-out;
}

.calculator:hover {
  transform: scale(1.02);
}

/* Título */
h2 {
  color: #333;
  margin-bottom: 15px;
}

/* Estilização dos inputs e do select */
.input-group {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin: 20px 0;
}

input, select {
  padding: 10px;
  font-size: 18px;
  border: 2px solid #ccc;
  border-radius: 8px;
  text-align: center;
  transition: border-color 0.3s, box-shadow 0.3s;
}

input:focus, select:focus {
  border-color: #007bff;
  box-shadow: 0px 0px 8px rgba(0, 123, 255, 0.5);
  outline: none;
}

/* Resultado */
.result {
  margin-top: 20px;
  font-size: 22px;
}

.result span {
  font-weight: bold;
  color: #007bff;
  font-size: 24px;
}
</style>
