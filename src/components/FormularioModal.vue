<template>
    <div>
        <v-form>
            <v-text-field
                v-model="characters.name"
                label="Diguite nombre"
                required>
            </v-text-field>
            <v-text-field
            v-model="characters.dni"
                label="Diguite dni"
                required>
            </v-text-field>
            <v-btn @click="submitForm">Agregar</v-btn>
        </v-form>
    </div>
</template>
<script setup>
import Swal from 'sweetalert2';
import { ref,defineEmits } from 'vue'

const emit = defineEmits(['add-person']);

const characters = ref({
    name:"",
    dni: "",
})

const submitForm = () => {
    if(characters.valuue.name === "" || characters.value.dni === ""){
        Swal.fire({
            title:'Agregar persona',
            text:'Los campos se encuentran vacios',
            icon:'warning'
        })
    } else {
        emit('add-person',{
            name:characters.valuue.name,
            dni:characters.value.dni,
        });
        characters.value.name = "",
        characters.value.dni = ""
    }
}

</script>

<style>
    
</style>