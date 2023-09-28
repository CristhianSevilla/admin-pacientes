<script setup>
import { computed } from "vue";

const props = defineProps({
  alerta: {
    type: Object,
    required: true,
  },
});

const isError = computed(() => {
  return props.alerta.tipo === "error";
});
</script>

<template>
  <div
    :class="[isError ? 'bg-red-500' : 'bg-green-600']"
    class="text-white uppercase p-3 rounded-md text-center font-bold mb-2"
  >
    {{ alerta.mensaje }}
  </div>
</template>
