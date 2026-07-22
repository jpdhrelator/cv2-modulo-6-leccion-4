<script setup>
import { ref } from 'vue';


const emit= defineEmits(['agregar']);
const texto= ref('');

function enviar() {
    const limpio= texto.value.trim();
    if(!limpio) return;

    emit('agregar',limpio);
    texto.value='';
}

</script>
<template>
    <div style="display:flex;gap:.5rem;margin:.5rem 0">
        <input v-model="texto" type="text" placeholder="Nueva tarea..." style="flex:1" @keyup.enter="enviar">
        <button class="btn" @click="enviar">Agregar</button>
    </div>
</template>
