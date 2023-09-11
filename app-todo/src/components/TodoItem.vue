<script setup>
import { ref, computed } from "vue";
const props = defineProps({
  item: {
    type: Object,
    required: true,
  },
  estado: {
    type: Number,
    required: true,
  },
});
const cambiarColorFondoSegunEstado = computed(() => {
  if (props.item.estado === 0) {
    return "item-deleted";
  }
  if (props.item.estado === 2) {
    return "item-disable";
  } else {
    return "item-active";
  }
});
const checkEstadoInicial = computed(() => {
  if (props.item.estado === 2) {
    return true;
  } else {
    return false;
  }
});

const cambiarEstado = () => {
  props.item.estado == 1 ? (props.item.estado = 2) : (props.item.estado = 1);
  console.log(props.item.estado);
};
const modificarEstado = () => {
  if (props.item.estado != 0) {
    props.item.estado = 0;
  } else {
    props.item.estado = 1;
  }
};
const textoBotonItem = ref("");

const verificarEstadoBoton = computed(() => {
  if (props.item.estado != 0) {
    textoBotonItem.value = "Eliminar";
    return true;
  } else {
    textoBotonItem.value = "Restaurar";
    return true;
  }
});
const cambiarColorSegunEstado = computed(() => {
  if (props.item.estado === 0) {
    return "btn-deleted";
  }
  if (props.item.estado === 2) {
    return "btn-disable";
  }
  if (props.item.estado === 1) {
    return "btn-active";
  }
});

</script>
<template>
  <div>
    <div class="todo-body">
      <div class="input-group mb-3" v-if="item.estado == estado || estado == 3">
        <div
          :class="cambiarColorFondoSegunEstado"
          class="input-group-text"
          v-if="item.estado != 0"
        >
          <input
            class="form-check-input mt-0"
            type="checkbox"
            :checked="checkEstadoInicial"
            @click="cambiarEstado"
          />
        </div>
        <input
          type="text"
          v-model="item.titulo"
          :class="cambiarColorFondoSegunEstado"
          class="form-control"
        />
        <button
          @click="modificarEstado()"
          type="button"
          class="btn btn-action"
          :class="cambiarColorSegunEstado"
          v-if="verificarEstadoBoton"
        >
          {{ textoBotonItem }}
        </button>
      </div>
    </div>
  </div>
</template>

<style>
.item-active {
  background-color: rgb(154, 231, 186);
}
.item-deleted {
  background-color: rgb(255, 226, 164);
}
.item-disable {
  background-color: rgb(224, 222, 222);
}

.btn-active,
.btn-disable {
  background-color: rgb(219, 71, 66);
  color: white;
}
.btn-deleted {
  background-color: rgb(206, 119, 7);
  color: white;
}
.btn-editar {
  background-color: rgb(13, 130, 134);
  color: white;
}
.todo-body {
  margin-top: 1rem;
}
</style>
