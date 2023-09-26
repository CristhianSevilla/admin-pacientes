<script setup>
import { reactive } from "vue";

const paciente = reactive({
  nombre: "",
  email: "",
  telefono: "",
  alta: "",
  tratamiento: "",
});
</script>
<template>
  <div class="md:w-1/2 xl:px-10">
    <h2 class="text-2xl mt-5 text-center mb-10 font-bold md:font-normal">
      Agrega Pacientes y
      <span class="text-indigo-600 font-bold">Adminístralos</span>
    </h2>

    <form
      class="bg-indigo-100 bg-opacity-60 shadow-md rounded-lg py-10 px-5 mb-10"
    >
      <div class="mb-5">
        <label for="nombre" class="text-gray-800 uppercase font-bold"
          >Nombre:</label
        >
        <input
          id="nombre"
          type="text"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          placeholder="Nombre del paciente"
          v-model="paciente.nombre"
        />
      </div>
      <div class="mb-5">
        <label for="email" class="text-gray-800 uppercase font-bold"
          >Email:</label
        >
        <input
          id="email"
          type="email"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          placeholder="Email del paciente"
          v-model="paciente.email"
        />
      </div>
      <div class="mb-5">
        <label for="telefono" class="text-gray-800 uppercase font-bold"
          >Teléfono:</label
        >
        <input
          id="telefono"
          type="number"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          placeholder="Teléfono del paciente"
          v-model="paciente.telefono"
        />
      </div>
      <div class="mb-5">
        <label for="alta" class="text-gray-800 uppercase font-bold"
          >Alta:</label
        >
        <input
          id="alta"
          type="date"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          v-model="paciente.alta"
        />
      </div>
      <div class="mb-5">
        <label for="tratamiento" class="text-gray-800 uppercase font-bold"
          >Tratamiento:</label
        >
        <textarea
          id="tratamiento"
          placeholder="Descríbe el tratamiento del paciente"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-40"
          v-model="paciente.tratamiento"
        />
      </div>

      <input
        type="submit"
        class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-800 hover:cursor-pointer"
        value="Registrar Paciente"
      />
    </form>
  </div>
</template>
