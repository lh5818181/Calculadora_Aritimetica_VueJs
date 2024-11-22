<script setup>
import { reactive, watch } from 'vue';
import Cabecalho from './components/cabecalho.vue';
import Buttons from './components/buttons.vue';
import Inputs from './components/inputs.vue';
import Resultado from './components/resultado.vue';

// Estado reativo para os dados
const estado = reactive({
  num1: null,
  num2: null,
  operacao: null,
  resultado: null,
});

// Função para calcular automaticamente
const calcula = () => {
  const num1 = Number(estado.num1);
  const num2 = Number(estado.num2);

  // Verifica se os números são válidos antes de calcular
  if (isNaN(num1) || isNaN(num2)) {
    estado.resultado = 'Insira números válidos';
    return;
  }

  // Realiza a operação com base na escolha do usuário
  switch (estado.operacao) {
    case 'adicao':
      estado.resultado = num1 + num2;
      break;
    case 'subtracao':
      estado.resultado = num1 - num2;
      break;
    case 'divisao':
      estado.resultado = num2 !== 0 ? num1 / num2 : 'Erro: divisão por zero';
      break;
    case 'multiplicacao':
      estado.resultado = num1 * num2;
      break;
    default:
      estado.resultado = 'Escolha uma operação';
  }
};

// Observa mudanças nos valores e recalcula automaticamente
watch(() => [estado.num1, estado.num2, estado.operacao], calcula);
</script>

<template>
  <div class="container">
    <Cabecalho />
    <div class="calc">
      <Buttons :operacao="estado.operacao" @escolher-operacao="estado.operacao = $event" />
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

@media (max-width: 768px) {
  .container {
    padding: 15px;
  }

  .calc {
    gap: 15px;
  }
}
</style>
