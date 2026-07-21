<script setup>
import { ref } from 'vue';
const tareas = ref([
  { id: 1, texto: 'Estudiar eventos en Vue' },
  { id: 2, texto: 'Hacer la práctica' },
  { id: 3, texto: 'Tomar café ☕' },
]);

const eliminar= (id, eventoNativo)=>{
  console.log(eventoNativo);
  
  tareas.value= tareas.value.filter(t => t.id!=id);
}


</script>
<template>
  <div class="demo" id="app-args">
    <h4>▶ Demo en vivo</h4>
    <ul style="list-style:none; padding:0;">
      <li v-for="t in tareas" :key="t.id" class="li-obj">
        <span>{{ t.texto }}</span>
        <button class="btn btn-ejer7" 
          @click="eliminar(t.id, $event)">✕</button>
      </li>
    </ul>
    <div v-if="tareas.length === 0" class="out">🎉 ¡No quedan tareas! Recarga para reiniciar.</div>
  </div>
</template>

<style scoped>
.btn-ejer7{
  background:#ef4444; color:#fff; padding:.2rem .6rem;
}
.li-obj {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #fff;
  border: 1px solid #cbd5e1;
  border-radius: 8px;
  padding: .5rem .8rem;
  margin-bottom: .5rem;
}
</style>