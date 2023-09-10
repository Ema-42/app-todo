<script setup>
import TodoItem from "./TodoItem.vue";
defineProps({
  lista: {
    type: Array,
    required: true
  },
  estado:{
    type: Number,
    required:true
  }
})
</script>
<template>
  <div>
    <div v-for="(item, index) in lista" :key="index">
        <TodoItem :item="item" :estado="estado"></TodoItem>
    </div>
  </div>
</template>

<script></script>
