<script setup>
import { reactive } from "vue";

const numeros = reactive({
  filtro: "somar",
  numA: 0,
  numB: 0,
});

function somar() {
  const { numA, numB } = numeros;
  return Number(numA) + Number(numB);
}

function subtrair() {
  const { numA, numB } = numeros;
  return Number(numA) - Number(numB);
}

function multiplicar() {
  const { numA, numB } = numeros;
  return Number(numA) * Number(numB);
}

function dividir() {
  const { numA, numB } = numeros;
  if (numA && numB > 0) {
    return numA / numB;
  } else {
    return 0;
  }
}

const resultado = () => {
  const { filtro } = numeros;

  switch (filtro) {
    case "subtrair":
      return subtrair();
    case "multiplicar":
      return multiplicar();
    case "dividir":
      return dividir();
    default:
      return somar();
  }
};
</script>

<template>
  <div class="container mt-5 pt-5 pb-5 rounded">
    <header class="header text-center pb-5 pt-5 mb-3">
      <h1 class="header__title fs-1">Calculadora Com VueJS</h1>
    </header>
    <section
      class="calculadora d-flex align-items-center justify-content-center pb-5"
    >
      <input
        class="calculadora__input me-3 ms-3 p-2 rounded border border-success"
        type="number"
        placeholder="Insira aqui um número"
        @keyup="(evento) => (numeros.numA = evento.target.value)"
      />
      <select
        class="calculadora__select border border-light rounded p-1"
        @change="(evento) => (numeros.filtro = evento.target.value)"
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
        @keyup="(evento) => (numeros.numB = evento.target.value)"
      />
      <span class="calculadora__resposta d-block fs-2 ps-4">
        {{ resultado() }}
      </span>
    </section>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.container {
  max-width: 960px;
  margin: 0 auto;
  background-color: rgb(242, 246, 241);
  font-family: sans-serif;
}

.header__title {
  color: rgb(42, 116, 8);
  font-weight: bold;
}

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
