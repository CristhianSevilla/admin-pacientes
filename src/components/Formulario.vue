<script setup>
import { reactive } from "vue";
import Alerta from "./Alerta.vue";

const alerta = reactive({
  tipo: "",
  mensaje: "",
});

const paciente = reactive({
  nombre: "",
  email: "",
  telefono: "",
  alta: "",
  tratamiento: "",
});

const validar = () => {
  if (Object.values(paciente).includes("")) {
    alerta.mensaje = "Todos los campos son obliogatorios";
    alerta.tipo = "error";
    return;
  }

  console.log("Agregando...");
};
</script>
<template>
  <div class="md:w-1/2 xl:px-12">
    <h2
      class="text-xl md:text-2xl mt-5 text-center mb-10 font-semibold md:font-normal"
    >
      Agrega Pacientes y
      <span class="text-indigo-600 font-bold">Adminístralos</span>
    </h2>

    <form
      class="bg-indigo-100 bg-opacity-60 shadow-xl rounded-lg py-10 px-5 mb-10"
      @submit.prevent="validar"
    >
      <div class="mb-5">
        <label for="nombre" class="text-gray-800 uppercase font-bold"
          >Nombre:</label
        >
        <input
          id="nombre"
          type="text"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          placeholder="Nombre completo del paciente"
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
          >Fecha de Alta:</label
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
