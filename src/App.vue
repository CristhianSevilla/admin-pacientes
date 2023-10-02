<script setup>
import { ref, reactive, watch, onMounted } from "vue";
import { uid } from "uid";
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Formulario from "./components/Formulario.vue";
import Paciente from "./components/Paciente.vue";

const pacientes = ref([]);

const paciente = reactive({
  id: null,
  nombre: "",
  email: "",
  telefono: "",
  alta: "",
  tratamiento: "",
});

//Llamar la funcion para guardarLocalStorage cada que ocurra un cambio en elarreglo de pacientes
watch(
  pacientes,
  () => {
    guardarLocalStorage();
  },
  {
    deep: true,
  }
);

//Poner en localStorage el arreglo de pacientes, convertido en un objeto JSON
const guardarLocalStorage = () => {
  localStorage.setItem("pacientes", JSON.stringify(pacientes.value));
};

//Colocar los pacientes del Storage en el State
onMounted(() => {
  const pacientesStorage = localStorage.getItem("pacientes");

  if (pacientesStorage) {
    pacientes.value = JSON.parse(pacientesStorage);
  }
});

const guardarPaciente = () => {
  //Detectar si es un registro nuevo o si es un paciente que se va a editar, dependiendo si hay un id
  if (paciente.id) {
    //Aplicamos destructuring al id del paciente a editar
    const { id } = paciente;
    //Buscamos la posicion en el arreglo de los pacientes, del paciente al que vamos a editar, ocupando el id para buscarlo
    const i = pacientes.value.findIndex(
      (pacienteState) => pacienteState.id === id
    );
    //Reescribimos al paciente editado en el arreglo de pacientes
    pacientes.value[i] = { ...paciente };
  } else {
    //Hacemos un nuevo registro
    pacientes.value.push({ ...paciente, id: uid() });
  }

  //Reiniciar el objeto de paciente
  Object.assign(paciente, {
    nombre: "",
    email: "",
    telefono: "",
    alta: "",
    tratamiento: "",
    id: null,
  });
};

const actualizarPaciente = (id) => {
  //Filtrar el paciente que queremos editar
  const pacienteEditar = pacientes.value.filter(
    (paciente) => paciente.id === id
  )[0];
  //LLenar el objeto de paciente con los datos del paciente a editar para que se muestren en el formulario
  Object.assign(paciente, pacienteEditar);
};

const eliminarPaciente = (id) => {
  // Filtrar los pacientes restantes
  const pacientesRestantes = pacientes.value.filter(
    (paciente) => paciente.id !== id
  );

  // Asignar los pacientes restantes al arreglo de pacientes
  pacientes.value = pacientesRestantes;
};
</script>

<template>
  <Header />
  <div class="container mx-auto px-5 xl:px-10">
    <div class="mt-6 md:mt-10 md:flex gap-4">
      <formulario
        v-model:nombre="paciente.nombre"
        v-model:email="paciente.email"
        v-model:telefono="paciente.telefono"
        v-model:alta="paciente.alta"
        v-model:tratamiento="paciente.tratamiento"
        @guardar-paciente="guardarPaciente"
        :id="paciente.id"
      />
      <div class="md:w-1/2 md:h-screen md:overflow-y-scroll">
        <h3
          class="text-xl md:text-2xl mt-5 text-center font-semibold md:font-normal"
        >
          <span class="text-indigo-700 font-bold">Administra </span>
          Pacientes
        </h3>
        <div v-if="pacientes.length">
          <Paciente
            v-for="paciente in pacientes"
            key="paciente.id"
            :paciente="paciente"
            @actualizar-paciente="actualizarPaciente"
            @eliminar-paciente="eliminarPaciente"
          />
        </div>
        <p v-else class="mt-12 text-2xl text-center">No hay pacientes</p>
      </div>
    </div>
  </div>
  <Footer />
</template>
