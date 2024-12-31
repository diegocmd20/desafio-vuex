<script>
import { mapState, mapActions } from "vuex";

export default {
  computed: {
    ...mapState(["juegos"]),
  },
  methods: {
    ...mapActions(["actualizarStock"]),
    modificarStock(codigo, cantidad) {
      this.actualizarStock({ codigo, cantidad });
    },
  },
};
</script>

<template>
  <div id="app">
    <h1>Tienda 32 Bits</h1>
    <h2>Lista de juegos</h2>
    <table>
      <thead>
        <tr>
          <th>Código</th>
          <th>Nombre</th>
          <th>Stock</th>
          <th>Precio</th>
          <th>Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="juego in juegos" :key="juego.codigo">
          <td>{{ juego.codigo }}</td>
          <td>{{ juego.nombre }}</td>
          <td>{{ juego.stock }}</td>
          <td>${{ juego.precio.toLocaleString() }}</td>
          <td>
            <button @click="modificarStock(juego.codigo, 1)">+</button>
            <button @click="modificarStock(juego.codigo, -1)">-</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
h1,
h2 {
  text-align: center;
}

table {
  width: 80%;
  margin: 20px auto;
  border-collapse: collapse;
}

th,
td {
  border: 1px solid #ccc;
  padding: 10px;
  text-align: center;
}

th {
  background-color: #f9f9f9;
}

button {
  padding: 5px 10px;
  margin: 0 5px;
  cursor: pointer;
}
</style>
