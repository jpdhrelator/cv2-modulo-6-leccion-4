<script setup>
import { computed, ref } from 'vue';

const colores =['#ef4444', '#f59e0b', '#22c55e'];// rojo, ámbar, verde
const indice= ref(0);
const color= computed(()=> colores[indice.value]);

const siguiente= ()=>{
  indice.value= (indice.value +1)% colores.length;
}

</script>
<template>
   <div class="demo" id="app-metodo">
      <h4>▶ Demo en vivo</h4>
      <div style="display:flex; align-items:center; gap:1rem;">
        <div :style="{ background: color, width:'70px', height:'70px', borderRadius:'50%', transition:'all .3s', boxShadow:'0 0 20px ' + color }"></div>
        <button class="btn" @click="siguiente">Cambiar luz</button>
      </div>
      <div class="out">Color actual: <b>{{ color }}</b></div>
    </div>
</template>
