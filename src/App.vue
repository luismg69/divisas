<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <Listadivisas titulo="Componente lista de divisas"></Listadivisas>
  </div>
</template>

<script>
import Listadivisas from "./components/ListaDivisas";

export default {
  name: "App",
  components: {
    Listadivisas,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
