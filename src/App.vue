<script setup>
import { reactive } from 'vue';

const estado = reactive({
  num1: null,
  num2: null,
  resultado: null,
});

</script>

<template>
  <div class="container">
    <header class="header p-5 mb-3 mt-4">
      <h1>Calculadora Aritmética</h1>
      <p>
        Por favor escolha a função desejada.
      </p>
    </header>
    <div class="calc">
      <div class="btns">
        <button class="btn btn-primary">Soma</button>
        <button class="btn btn-primary">Subtração</button>
        <button class="btn btn-primary">Divisão</button>
        <button class="btn btn-primary">Multiplicação</button>
      </div>
      <form>
        <div class="row">
          <div class="col">
            <label>Digite o <b>primeiro</b> numero no campo abaixo:</label> <br>
            <input type="number" placeholder="Digite um número" class="form-control mb-2">
            <label>Digite o <b>segundo</b> numero no campo abaixo:</label> <br>
            <input type="number" placeholder="Digite um número" class="form-control mb-5">
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<style scoped>

.container {
  background-color: #000;
  color: #fff;
}

.btns {
  margin: 8px 0;
  display: flex;
  justify-content: center;
}

.btn {
  margin: 8px;
}

</style>
