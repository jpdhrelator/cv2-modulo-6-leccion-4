<script setup>
import { ref } from 'vue';

const nombre= ref('');
const enviado= ref(true);
function enviar(){ enviado.value = nombre.value; nombre.value = ''  }

</script>
<template>
 <div class="demo" id="app-prevent">
      <h4>▶ Demo en vivo — envía y la página NO se recarga</h4>
      <form @submit.prevent="enviar" style="display:flex; gap:.6rem; align-items:flex-end;">
        <div style="flex:1;">
          <label>Tu nombre</label>
          <input type="text" v-model="nombre" placeholder="Escribe y presiona Enviar" />
        </div>
        <button class="btn" type="submit">Enviar</button>
      </form>
      <div class="out" v-if="enviado">✅ Recibido sin recargar: <b>{{ enviado }}</b></div>
    </div>
</template>

<style scoped>

</style>