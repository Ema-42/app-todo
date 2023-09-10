<script setup>
import { ref } from "vue";
defineProps({
  lista: {
    type: Array,
    required: true,
  },
});

const agregarItem = (nuevoItem, lista) => {
  lista.push({ id: lista.length + 1, titulo: nuevoItem, estado: 1 });
  console.log(lista);
};
const nuevoItem = ref("");
</script>
<template>
  <h5>Añadir nueva tarea</h5>
  <div class="input-group mb-3">
    <span class="input-group-text" id="inputGroup-sizing-default">Nueva</span>
    <input
      v-model="nuevoItem"
      @keyup.enter="agregarItem(nuevoItem, lista)"
      placeholder="Ingresa una tarea"
      type="text"
      class="form-control form-control"
    />
  </div>
</template>
