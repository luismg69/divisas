<template>
  <div class="lista-divisas">
    <h1>{{ titulo }}</h1>
    <div>
      <input type="number" v-model="valorEscrito" />
    </div>
    <h1>{{ valorConvertido }}</h1>
    <h3 v-if="fecha !== ''">{{ convertirFecha }}</h3>
    <ul>
      <!-- bucle de carga de las divisas -->
      <Item
        v-for="(valor, nombre, index) of divisas"
        v-bind:key="index"
        v-bind:datos="{ nombre, valor }"
        v-bind:funcionRecuperadoraClick="convierteDivisa"
      />
    </ul>
  </div>
</template>


<script>
/*
     objeto con el vue
     */
import Item from "./Item";
export default {
  name: "Listadivisas",
  components: {
    Item,
  },
  props: {
    titulo: String,
  },
  data: function () {
    return {
      divisas: {},
      fecha: "",
      valorConvertido: 0,
      valorEscrito: 0,
    };
  },
  computed: {
    convertirFecha: function () {
      const fechaNumber = Date.parse(this.fecha);
      const fecha = new Date(fechaNumber);
      return (
        fecha.getDate() +
        "-" +
        (fecha.getMonth() + 1) +
        "-" +
        fecha.getFullYear()
      );
    },
  },
  created: function () {
    const url = "https://api.frankfurter.app/latest";
    fetch(url)
      .then((response) => response.json())
      .then((data) => {
        this.divisas = data.rates;
        this.fecha = data.date;
        console.log(this.divisas);
      });
  },

  methods: {
    convierteDivisa: function (datos) {
      this.valorConvertido = this.valorEscrito * datos.valor;
    },
  },
};
</script>


<style scoped>
.lista-divisas {
}
ul {
  padding: 0;
}
li {
  list-style: none;
}
</style>