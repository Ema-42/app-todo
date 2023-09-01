<script setup>
import { ref, reactive } from "vue";
const name = "Emanuel Cs ";
const colorred = "color: red";
const colorgreen = "color: green ";
const arrayColores = ["blue", "red", "black", "pink"];
const activo = true;
const directivas = "directivas";

const arrayFrutas = ["pera", "manzana", "uva", "banana"];
const items = ref([{ message: "Foo" }, { message: "Bar" }]);
const arrayFrutas2 = [
  {
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
  },
  {
    name: "Pera",
    price: "$2.00",
    description: "Una pera",
  },
  {
    name: "Naranja",
    price: "$3.00",
    description: "Una naranja",
  },
];
const myObject = reactive({
  title: "How to do lists in Vue",
  author: "Jane Doe",
  publishedAt: "2016-04-10",
});
const objetoNaranja = {
  name: "Naranja",
  price: "$3.00",
  description: "Una naranja",
};
const arrayFrutas3 = [
  {
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
    stock: 20,
  },
  {
    name: "Pera",
    price: "$2.00",
    description: "Una pera",
    stock: 21,
  },
  {
    name: "Naranja",
    price: "$3.00",
    description: "Una naranja",
    stock: 44,
  },
];

//metodo --methods
const handleClick = () => {
  console.log("me diste click, pana");
};
const handleClick2 = (name) => {
  console.log(`Hola ${name}`);
};
const clicAlert = (nombre) => {
  alert(`Hola ${nombre}`);
};

//reactividad
const contador = ref(0);
const aumentarContador = () => {
  contador.value++;
};

const disminuirContador = () => {
  contador.value--;
};

const resetearContador = () => {
  contador.value = 0;
};
</script>

<template>
  <h1>1 Hola {{ name }}</h1>
  <h1>2 Hola {{ name.toUpperCase() }}</h1>
  <h2>3 {{ arrayColores }}</h2>
  <h2 v-bind:style="colorred">4 Color azul</h2>
  <h2 :style="colorgreen">5 Color verde</h2>
  <h2 :style="`color: ${arrayColores[1]}`">6 Color del array</h2>
  <h2>
    7
    {{ activo ? "Estoy activo" : "Estoy inactivo" }}
  </h2>
  <h1 :style="`color: ${arrayColores[0]}`">8 {{ directivas.toUpperCase() }}</h1>
  <p v-if="!activo">9 Estoy inactivo</p>
  <p v-else="activo">10 Estoy activo</p>
  <h2 v-show="activo">11 Estoy activo con v - show</h2>
  <h2>
    12 el de arriba solo se pone display none con v-if directamente no se crea
  </h2>
  <h1>13 Hola emanuel</h1>
  <h1>14 v for</h1>
  <h2>{{ arrayFrutas }}</h2>
  <ul>
    <li v-for="(fruta, i) in arrayFrutas" :key="i">
      {{ i }}: {{ fruta.toUpperCase() }}
    </li>
  </ul>
  <h3>for cn un objeto:</h3>
  <li v-for="item of items">
    {{ item.message }}
  </li>
  <h2>ejercicio de {{ name }}</h2>
  <li v-for="(fruta2, i) in arrayFrutas2" :key="fruta2.name">
    {{ i + 1 }}: {{ fruta2.name }} - {{ fruta2.price }} $ ,
    {{ fruta2.description }}
  </li>
  <h3>ejem</h3>
  <li v-for="(value, key, index) in myObject">
    {{ index }}. {{ key }}: {{ value }}
  </li>
  <h3>naranja</h3>
  <h2>{{ objetoNaranja }}</h2>
  <li v-for="(value, key, index) in objetoNaranja" :key="value">
    {{ index }} - {{ key }} - {{ value }}
  </li>
  <h1>Vfor con range</h1>
  <span v-for="n in 10">{{ n }}</span>
  <li v-for="(i, index) in 10">{{ i }}</li>
  <h1>vfor con vif</h1>
  <p>{{ arrayFrutas3 }}</p>
  <ul>
    <template v-for="fruta3 in arrayFrutas3" :key="fruta3.name">
      <li v-if="fruta3.stock > 20">
        {{ fruta3.name }} - {{ fruta3.price }} - stock: {{ fruta3.stock }}
      </li>
    </template>
  </ul>

  <h1>Eventos</h1>
  <button v-on:click="handleClick">Activame</button>
  <button @click="handleClick">Activame 2</button>
  <button @click="handleClick2('Emanuel')">Activame 3</button>
  <button v-on:click.right="handleClick2('Right')">Activame rigt</button>
  <button v-on:click.left="handleClick2('Left')">Activame left</button>
  <button @click="clicAlert('Emanuel')">Activame ALERT</button>

  <h1>EJemplo del contador tipico</h1>
  <h2 class="contador" v-bind:style="{ color: contador < 0 ? 'red' : 'green' }">
    {{ contador }}
  </h2>
  <button class="btn" @click="aumentarContador()">Aumentar</button>
  <button class="btn btn-resetear" @click="resetearContador()">RESETEAR</button>
  <button class="btn" @click="disminuirContador()">Disminuir</button>
  //propiedades comuputadas
</template>

<style>
h1 {
  color: rgb(41, 9, 160);
}
.contador {
  font-weight: bold;
  font-style: oblique;
  display: flex;
  justify-content: center;
}
.btn-resetear {
  background-color: brown;
  color: aliceblue;
  font-weight: bold;
}
.btn {
  height: 30px;
  margin-left: 10px;
  padding: 5px 5px 5px 5px;
}
.btn:hover {
  background-color: rgba(52, 53, 51, 0.707);
  color: aliceblue;
}
</style>
