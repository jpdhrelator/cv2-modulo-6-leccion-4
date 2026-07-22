<script setup>
import { ref } from 'vue';

const texto= ref('');

const emit= defineEmits(['guardar','cancelar']);

function guardar() {
    emit('guardar',texto.value);
    texto.value='';
}
function cancelar() {
    emit('cancelar');
    texto.value='';
}

</script>
<template>   
    <textarea v-model="texto" placeholder="Escribe algo...">¡Buen curso!</textarea>
      <div style="margin-top:.5rem">
        <button class="btn-mini" @click="guardar">Guardar</button>
        <button class="btn-mini ghost" @click="cancelar">Cancelar</button>
      </div>
</template>



