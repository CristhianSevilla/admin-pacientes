<script setup>
const props = defineProps({
  alerta: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <div
    class="text-white uppercase p-3 bg-red-500 rounded-md text-center font-bold mb-2"
  >
    {{ alerta.mensaje }}
  </div>
</template>
