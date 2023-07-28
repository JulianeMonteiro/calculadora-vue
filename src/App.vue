<script setup>
import { reactive } from "vue";
import Header from "./components/Header.vue";
import Calculator from "./components/Calculator.vue";
// import Caculator from "./components/Caculator.vue";

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
    <Header></Header>
    <Calculator
      :trocar-filtro="(evento) => (numeros.filtro = evento.target.value)"
      :num-a="(evento) => (numeros.numA = evento.target.value)"
      :num-b="(evento) => (numeros.numB = evento.target.value)"
      :numero-a="numeros.numA"
      :numero-b="numeros.numB"
      :resultado="resultado()"
    ></Calculator>
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
</style>
