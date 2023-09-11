<script setup>
import { ref } from "vue";
import TodoItem from "./TodoItem.vue";
const props = defineProps({
  lista: {
    type: Array,
    required: true,
  },
});

const inputTareaBuscar = ref("");
const listaCoincidencias = ref([]);
const buscarTarea = () => {
  listaCoincidencias.value = [];
  if (inputTareaBuscar.value != "") {
    const inputTareaAux = inputTareaBuscar.value.split(" ");
    props.lista.forEach((tarea) => {
      inputTareaAux.forEach((palabra) => {
        if (tarea.titulo.includes(palabra)) {
          listaCoincidencias.value.push(tarea);
        }
      });
    });
  }
};
const limpiarListaConincidencias = () => {
  listaCoincidencias.value = [];
  inputTareaBuscar.value = "";
};
</script>
<template>
  <h5>Buscar</h5>
  <div>
    <nav class="navbar bg-body-tertiary">
      <form class="d-flex col-md-12">
        <a class="navbar-brand">
          <img
            src="https://cdn-icons-png.flaticon.com/512/1180/1180928.png"
            width="25"
            height="25"
          />
        </a>
        <input
          class="form-control me-2"
          placeholder="Buscar tarea"
          v-model="inputTareaBuscar"
        />
        <div class="btn-group" role="group" aria-label="Basic example">
          <button class="btn btn-primary px-1" @click="buscarTarea()">
            Buscar
          </button>
          <button
            class="btn btn-secondary px-1"
            @click="limpiarListaConincidencias()"
          >
            Limpiar
          </button>
        </div>
      </form>
    </nav>
  </div>

  <div>
    <div v-for="(item, index) in listaCoincidencias" :key="index">
      <TodoItem :item="item" :estado="3"></TodoItem>
    </div>
  </div>
</template>
<style></style>
