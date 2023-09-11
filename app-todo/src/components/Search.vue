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
        if (tarea.titulo.toLowerCase().includes(palabra.toLowerCase())) {
          listaCoincidencias.value.push(tarea);
        }
      });
    });
  }
};
const limpiarListaConincidencias = () => {
  listaCoincidencias.value = [];
  inputTareaBuscar.value = "";
  const fechaActual = new Date();
  console.log(fechaActual);
};
</script>
<template>
  <h5>Buscar</h5>
  <div>
    <div class="mb-3 input-group">
      <input
        class="form-control"
        placeholder="Buscar tarea"
        v-model="inputTareaBuscar"
      />
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
  </div>

  <div>
    <div v-for="(item, index) in listaCoincidencias" :key="index">
      <TodoItem :item="item" :estado="3"></TodoItem>
    </div>
  </div>
</template>
<style></style>
