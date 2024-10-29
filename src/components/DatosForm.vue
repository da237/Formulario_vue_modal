<template lang="">
  <div>
    <v-btn @click="showModal = true">Agregar Persona</v-btn>
    <!-- Modal -->
    <v-dialog v-model="showModal" max-width="500px">
      <v-card>
        <v-card-title>Agregar Nueva Persona</v-card-title>
        <v-card-text>
          <!-- Componente del formulario -->
          <FormularioModal />
        </v-card-text>
        <v-card-actions>
          <v-btn @click="showModal = false">Cerrar</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>

    <!-- Lista de datos -->
    <v-data-table class="elevation-1">
      <template v-slot:top>
        <thead>
          <tr>
            <th class="text-left">Id</th>
            <th class="text-left">Nombre</th>
            <th class="text-left">Dni</th>
            <th class="text-left">Acciones</th>
          </tr>
        </thead>
      </template>
    </v-data-table>
  </div>
</template>
<script setup>
import Swal from "sweetalert2";
import { ref, onMounted } from "vue";
import FormularioModal from "./FormularioModal.vue";

const showModal = ref(false);
const people = ref([]);

onMounted(() => {
  try {
    const storageItems = localStorage.gettem("ListPeople");
    if (storageItems) {
      people.value = json.parse(storageItems);
    }
  } catch (error) {
    console.log("Error", error);
  }
});

const addpeople = (person) => {
  people.value.push(person);
  localStorage.setItem("ListPeople", JSON.stringify(people.value));
  Swal.fire({
    title: "Agregar Persona",
    text: "Persona Creada con éxito",
    icon: "success",
    ConfirmButton: "Aceptar",
  });
  showModal.value = false;
};
</script>
<style lang=""></style>
