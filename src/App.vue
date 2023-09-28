<script setup>
import { ref, reactive } from "vue";
import Header from "./components/Header.vue";
import Formulario from "./components/Formulario.vue";

const pacientes = ref([]);

const paciente = reactive({
  nombre: "",
  email: "",
  telefono: "",
  alta: "",
  tratamiento: "",
});

const guardarPaciente = () => {
  pacientes.value.push(paciente);
};
</script>

<template>
  <Header />
  <div class="container mx-auto px-5 xl:px-10">
    <div class="mt-6 md:mt-10 md:flex">
      <formulario
        v-model:nombre="paciente.nombre"
        v-model:email="paciente.email"
        v-model:telefono="paciente.telefono"
        v-model:alta="paciente.alta"
        v-model:tratamiento="paciente.tratamiento"
        @guardar-paciente="guardarPaciente"
      />
      <div class="md:w-1/2 md:h-screen md:overflow-y-scroll">
        <h3
          class="text-xl md:text-2xl mt-5 text-center mb-10 font-semibold md:font-normal"
        >
          <span class="text-indigo-700 font-bold">Administra </span>
          Pacientes
        </h3>
        <div v-if="pacientes.length"></div>
        <p v-else class="mt-20 text-2xl text-center">No hay pacientes</p>
      </div>
    </div>
  </div>
</template>
