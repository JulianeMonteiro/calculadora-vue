<script setup>
const props = defineProps([
  "trocarFiltro",
  "numA",
  "numB",
  "numeroA",
  "numeroB",
  "resultado",
]);
</script>

<template>
  <section
    class="calculadora d-flex align-items-center justify-content-center pb-5"
  >
    <input
      class="calculadora__input me-3 ms-3 p-2 rounded border border-success"
      type="number"
      placeholder="Insira aqui um número"
      :value="numeroA"
      @keyup="props.numA"
    />
    <select
      class="calculadora__select border border-light rounded p-1"
      @change="props.trocarFiltro"
    >
      <option value="somar">+</option>
      <option value="subtrair">-</option>
      <option value="multiplicar">x</option>
      <option value="dividir">/</option>
    </select>
    <input
      class="calculadora__input me-3 ms-3 p-2 rounded border border-success"
      type="number"
      placeholder="Insira aqui outro número"
      :value="numeroB"
      @keyup="props.numB"
    />
    <span class="calculadora__resposta d-block fs-2 ps-4">
      {{ props.resultado }}
    </span>
  </section>
</template>

<style scoped>
.calculadora__input::-webkit-inner-spin-button {
  -webkit-appearance: none;
}

.calculadora__select {
  font-size: 16px;
  font-weight: bold;
  height: 40px;
  background-color: #a9dfa9;
}

.calculadora__resposta {
  font-weight: bold;
  color: rgb(35, 97, 6);
}
</style>
