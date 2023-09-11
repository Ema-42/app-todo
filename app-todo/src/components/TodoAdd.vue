<script setup>
import { ref } from "vue";
defineProps({
  lista: {
    type: Array,
    required: true,
  },
});

const nuevoItem = ref("");

const agregarItem = (nuevaTarea, lista) => {
  lista.push({ id: lista.length + 1, titulo: nuevaTarea, estado: 1 });
  nuevoItem.value = "";
};
</script>
<template>
  <h5>Añadir nueva tarea</h5>
  <div class="input-group mb-3">
    <input
      v-model="nuevoItem"
      placeholder="Ingresa una tarea"
      type="text"
      class="form-control"
    />
    <button class="btn btn-primary" :disabled="nuevoItem===''" @click="agregarItem(nuevoItem, lista)">
      Añadir
    </button>
  </div>
</template>
