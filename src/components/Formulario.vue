<script setup></script>
<template>
  <div class="md:w-1/2 xl:px-10">
    <h2 class="text-2xl mt-5 text-center mb-10">
      Agrega Pacientes y
      <span class="text-indigo-700 font-bold">Adminístralos</span>
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
        />
      </div>

      <input
        type="submit"
        class="bg-indigo-600 w-full p-3 text-white uppercase font-bold"
        value="Registrar Paciente"
      />
    </form>
  </div>
</template>
