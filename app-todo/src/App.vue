<script setup>
import { ref } from "vue";

import Search from "./components/Search.vue";
import TodoAdd from "./components/TodoAdd.vue";
import Todos from "./components/Todos.vue";
import TodoItem from "./components/TodoItem.vue";

const lista = ref([
  {
    id: 1,
    titulo: "comprar comida",
    estado: 1,
  },
  {
    id: 2,
    titulo: "Cocinar comida",
    estado: 1,
  },
  {
    id: 3,
    titulo: "Ir a la facultad",
    estado: 1,
  },
  {
    id: 4,
    titulo: "comprar ropa",
    estado: 2,
  },
  {
    id: 5,
    titulo: "comprar medias",
    estado: 0,
  },
]);
//0 eliminado 1 activo   2 completado
</script>

<template>
  <div class="card">
    <div class="card-header">
      <h1>Tareas</h1>
    </div>
    <div class="contenedor">
      <Search :lista="lista"></Search>
      <TodoAdd :lista="lista"></TodoAdd>
      <h5>Tareas activas</h5>
      <Todos :lista="lista" :estado="1"></Todos>
      <h5>Tareas completadas</h5>
      <Todos :lista="lista" :estado="2"></Todos>
      <h5>Tareas eliminadas</h5>
      <Todos :lista="lista" :estado="0"></Todos>
    </div>
  </div>
</template>

<style scoped>
.contenedor {
  padding: 2rem;
}
.card {
  margin: 1rem;
  border: 1px solid rgb(106, 79, 226);
}
.card-header{
  background-color: rgb(106, 79, 226);
  color: rgb(233, 233, 233);
}
</style>
