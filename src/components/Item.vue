<template>
  <li v-on:click="funcionRecuperadoraClick(datos)">
    {{ datos.nombre }}: {{ datos.valor }}
  </li>
</template>

<script>
export default {
  name: "Item",
  props: {
    datos: Object,
    funcionRecuperadoraClick: Function,
  },
};
</script>

<style>
</style>