<script setup>
import { reactive, computed } from "vue";
import Alerta from "./Alerta.vue";

const alerta = reactive({
  tipo: "",
  mensaje: "",
});

const emit = defineEmits([
  "update:nombre",
  "update:email",
  "update:telefono",
  "update:alta",
  "update:tratamiento",
  "guardar-paciente",
]);

const props = defineProps({
  id: {
    type: [String, null],
    required: true,
  },
  nombre: {
    type: String,
    required: true,
  },
  email: {
    type: String,
    required: true,
  },
  telefono: {
    type: String,
    required: true,
  },
  alta: {
    type: String,
    required: true,
  },
  tratamiento: {
    type: String,
    required: true,
  },
});

const validar = () => {
  if (Object.values(props).includes("")) {
    alerta.mensaje = "Todos los campos son obliogatorios";
    alerta.tipo = "error";
    setTimeout(() => {
      Object.assign(alerta, {
        tipo: "",
        mensaje: "",
      });
    }, 3000);
    return;
  }

  emit("guardar-paciente");

  if (props.id) {
    alerta.mensaje = "Paciente Editado Correctamente";
    alerta.tipo = "exito";
  } else {
    alerta.mensaje = "Paciente Agregado Correctamente";
    alerta.tipo = "exito";
  }

  setTimeout(() => {
    Object.assign(alerta, {
      tipo: "",
      mensaje: "",
    });
  }, 3000);
};

const editando = computed(() => {
  return props.id;
});
</script>
<template>
  <div class="md:w-1/2 xl:px-12">
    <h2
      class="text-xl md:text-2xl mt-5 text-center mb-10 font-semibold md:font-normal"
    >
      <span class="text-indigo-700 font-bold">Agrega </span>Pacientes
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
          :value="nombre"
          @input="$emit('update:nombre', $event.target.value)"
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
          :value="email"
          @input="$emit('update:email', $event.target.value)"
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
          :value="telefono"
          @input="$emit('update:telefono', $event.target.value)"
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
          :value="alta"
          @input="$emit('update:alta', $event.target.value)"
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
          :value="tratamiento"
          @input="$emit('update:tratamiento', $event.target.value)"
        />
      </div>

      <Alerta v-if="alerta.mensaje" :alerta="alerta" />

      <input
        type="submit"
        class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-800 hover:cursor-pointer"
        :value="[editando ? 'Guardar Cambios' : 'Registrar Paciente']"
      />
    </form>
  </div>
</template>
