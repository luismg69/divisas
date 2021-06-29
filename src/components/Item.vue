<template>
  <li>{{ datos.nombre }}: {{ datos.valor }}</li>
</template>

<script>
export default {
  name: "Item",
  props: {
    datos: Object,
  },
};
</script>

<style>
</style>