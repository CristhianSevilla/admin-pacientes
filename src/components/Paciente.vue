<script setup>
defineProps({
  paciente: {
    type: Object,
    required: true,
  },
});

defineEmits(["actualizar-paciente", "eliminar-paciente"]);
</script>

<template>
  <div
    class="py-7 px-5 md:px-7 mb-7 last-of-type:mb-0 bg-indigo-100 bg-opacity-70 rounded-lg"
  >
    <p class="font-bold mb-3 text-gray-700 uppercase">
      ID:
      <span class="font-normal normal-case">{{ paciente.id }}</span>
    </p>

    <p class="font-bold mb-3 text-gray-700 uppercase">
      Nombre:
      <span class="font-normal normal-case">{{ paciente.nombre }}</span>
    </p>

    <p class="font-bold mb-3 text-gray-700 uppercase">
      Email:
      <span class="font-normal normal-case">{{ paciente.email }}</span>
    </p>

    <p class="font-bold mb-3 text-gray-700 uppercase">
      Teléfono:
      <span class="font-normal normal-case">{{ paciente.telefono }}</span>
    </p>

    <p class="font-bold mb-3 text-gray-700 uppercase">
      Fecha de Alta:
      <span class="font-normal normal-case">{{ paciente.alta }}</span>
    </p>

    <p class="font-bold mb-3 text-gray-700 uppercase">
      Tratamiento:
      <span class="font-normal normal-case">{{ paciente.tratamiento }}</span>
    </p>

    <div class="grid md:grid-cols-2 gap-5 mt-10">
      <button
        type="button"
        class="block w-full py-2 px-7 bg-indigo-600 hover:bg-indigo-800 text-white font-bold uppercase"
        @click="$emit('actualizar-paciente', paciente.id)"
      >
        Editar
      </button>

      <button
        type="button"
        class="block w-full py-2 px-7 bg-red-600 hover:bg-red-700 text-white font-bold uppercase"
        @click="$emit('eliminar-paciente', paciente.id)"
      >
        Eliminar
      </button>
    </div>
  </div>
</template>
