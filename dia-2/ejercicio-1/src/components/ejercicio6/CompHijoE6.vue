<script setup>
import { ref } from 'vue';


const emit= defineEmits(['elegido']);
const colores= ref(['Rojo', 'Verde', 'Azul','Amarillo']);

function pick(color) {
    emit('elegido',color);
}
</script>
<template>
    <div>      
        <button class="btn" v-for="c in colores" @click="pick(c)"> {{ c }}</button>
    </div>
</template>



