<script setup>
import { reactive, watch } from 'vue';
import Cabecalho from './components/cabecalho.vue';
import Inputs from './components/inputs.vue';
import Resultado from './components/resultado.vue';

const estado = reactive({
  num1: null,
  num2: null,
  operacao: null,
  resultado: null,
});

const calcula = () => {
  const num1 = Number(estado.num1);
  const num2 = Number(estado.num2);

  if (isNaN(num1) || isNaN(num2)) {
    estado.resultado = 'Insira números válidos';
    return;
  }

  let resultado;
  switch (estado.operacao) {
    case 'adicao':
      resultado = num1 + num2;
      break;
    case 'subtracao':
      resultado = num1 - num2;
      break;
    case 'divisao':
      resultado = num2 !== 0 ? num1 / num2 : 'Erro: divisão por zero';
      break;
    case 'multiplicacao':
      resultado = num1 * num2;
      break;
    default:
      resultado = 'Escolha uma operação';
  }

  if (typeof resultado === 'number' && !isNaN(resultado)) {
    estado.resultado = Math.round(resultado); // Arredonda para o número inteiro mais próximo
  } else {
    estado.resultado = resultado;
  }
};

// Observa mudanças nos valores ou operação e recalcula automaticamente
watch(() => [estado.num1, estado.num2, estado.operacao], calcula);
</script>

<template>
  <div class="container">
    <Cabecalho />
    <div class="calc">
      <div class="select-container">
        <label for="operacao">Escolha uma operação:</label>
        <select id="operacao" v-model="estado.operacao" class="select-operacao">
          <option disabled value="">Selecione</option>
          <option value="adicao">Adição</option>
          <option value="subtracao">Subtração</option>
          <option value="divisao">Divisão</option>
          <option value="multiplicacao">Multiplicação</option>
        </select>
      </div>
      <Inputs :valores="estado" />
      <Resultado :resultado="estado.resultado" />
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 600px;
  margin: 20px auto;
  padding: 20px;
  background: #186c73;
  color: white;
  border-radius: 10px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
}

.calc {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.select-container {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.select-operacao {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border-radius: 5px;
  border: 1px solid #ccc;
  background: #005f5f;
  color: white;
}

.select-operacao:focus {
  outline: none;
  border-color: #00ffbf;
}

@media (max-width: 768px) {
  .container {
    padding: 15px;
  }

  .select-operacao {
    font-size: 14px;
    padding: 8px;
  }
}
</style>
