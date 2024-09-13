<template>
  <div class="container mt-5">
    <h1 class="text-center mb-4">Calculadora Aritmética</h1>
    <div class="card p-4">
      <div class="mb-3">
        <input
          v-model.number="numero1"
          type="number"
          class="form-control"
          placeholder="Número 1"
        />
      </div>
      <div class="mb-3">
        <select v-model="operacao" class="form-select">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="*">x</option>
          <option value="/">÷</option>
        </select>
      </div>
      <div class="mb-3">
        <input
          v-model.number="numero2"
          type="number"
          class="form-control"
          placeholder="Número 2"
        />
      </div>
      <div class="alert alert-primary" role="alert">
        Resultado: {{ resultado }}
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const numero1 = ref(0);
const numero2 = ref(0);
const operacao = ref('+');

const resultado = computed(() => {
  const num1 = numero1.value;
  const num2 = numero2.value;
  switch (operacao.value) {
    case '+':
      return num1 + num2;
    case '-':
      return num1 - num2;
    case '*':
      return num1 * num2;
    case '/':
      return num2 !== 0 ? num1 / num2 : 'Erro: Divisão por zero';
    default:
      return 'Operação inválida';
  }
});
</script>

<style scoped>
.card {
  max-width: 400px;
  margin: 0 auto;
}

.alert {
  font-size: 1.25rem;
}
</style>
