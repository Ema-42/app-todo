<script setup>

const name = 'Emanuel Cs '
const colorred = 'color: red'
const colorgreen = 'color: green '
const arrayColores = ['blue', 'red','black', 'pink']
const activo = true
const directivas = 'directivas'
</script>

<template>
  <h1>Hola {{ name }}</h1>
  <h1>Hola {{ name.toUpperCase() }}</h1>
  <h2>{{ arrayColores }}</h2>
  <h2 v-bind:style="colorred">Color azul</h2>
  <h2 :style="colorgreen">Color verde</h2>
  <h2 :style="`color: ${arrayColores[1]}`">Color del array</h2>
  <h2>
    {{ activo ? 'Estoy activo': 'Estoy inactivo' }}
  </h2>
  <h1 :style="`color: ${arrayColores[0]}`">{{directivas.toUpperCase()}}</h1>
  <p v-if="!activo">Estoy inactivo</p>
  <p v-else="activo">Estoy activo</p>
  <h2 v-show="activo">Estoy activo con v - show</h2>
  <h2>el de arriba solo se pone display none con v-if directamente no se crea </h2>
  
</template>

<style>
h1{
  color: rgb(41, 9, 160);
}
</style>