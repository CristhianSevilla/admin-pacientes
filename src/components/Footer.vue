<script setup>
// Crear una instancia de Date
const fechaActual = new Date();
// Obtener el año actual
const añoActual = fechaActual.getFullYear();
</script>
<template>
  <div class="bg-indigo-100 bg-opacity-60 mt-14 p-5">
    <p class="text-center text-xl">
      Desarrollado por
      <span class="text-indigo-700 font-bold"
        >Cristhian Sevilla {{ añoActual }}&copy;
      </span>
    </p>
  </div>
</template>
