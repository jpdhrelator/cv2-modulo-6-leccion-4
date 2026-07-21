<script setup>
import { computed, ref } from 'vue';

const nuevo= ref('');
const seleccionado= ref(null);
let nextId=3;
const productos = ref([
        { id: 1, nombre: 'Teclado mecánico', likes: 2 },
        { id: 2, nombre: 'Mouse gamer', likes: 5 },
      ]);
function agregar() {
  if(nuevo.value.trim()==='') return;
  productos.value.push({ id: ++nextId, nombre: nuevo.value.trim(), likes: 0 })
  nuevo.value = '';

}

function quitar(id) {
  productos.value = productos.value.filter(p=> p.id !== id);
  if (seleccionado.value === id) seleccionado.value = null;
}

const seleccionar= (id)=> seleccionado.value = id;

const nombreSeleccionado=computed(()=>{
  const p= productos.value.find(p => p.id === seleccionado.value);
  return p? p.nombre : 'ninguno';
});



</script>
<template>
  <div class="demo" id="app-reto">
    <h4>▶ Demo en vivo</h4>
    <form @submit.prevent="agregar"
          class="form-e10">
      <input type="text" v-model="nuevo" 
                         @keydown.enter="agregar" 
                         placeholder="Producto nuevo + Enter"
        style="flex:1;" />
      <button class="btn" type="submit">Agregar</button>
    </form>
    <div v-for="p in productos" :key="p.id" @click="seleccionar(p.id)" 
    :style="{
      background: seleccionado === p.id ? '#dcfce7' : '#fff',
      border: '2px solid ' + (seleccionado === p.id ? '#22c55e' : '#cbd5e1'),
      borderRadius: '8px', padding: '.6rem .8rem', marginBottom: '.5rem',
      cursor: 'pointer', display: 'flex', justifyContent: 'space-between', alignItems: 'center'
    }">
      <span><b>{{ p.nombre }}</b> — ❤️ {{ p.likes }}</span>
      <span style="display:flex; gap:.4rem;">
        <button class="btn" style="padding:.2rem .6rem;" @click.stop="p.likes++">👍 Like</button>
        <button class="btn" style="padding:.2rem .6rem; background:#ef4444; color:#fff;"
          @click.stop="quitar(p.id)">✕</button>
      </span>
    </div>
    <div class="out">
      Seleccionado: <b>{{ seleccionado ? nombreSeleccionado : 'ninguno' }}</b> ·
      Total productos: <b>{{ productos.length }}</b>
    </div>
  </div>
</template>
<style scoped>
  .form-e10{
    display:flex; gap:.6rem; margin-bottom:1rem;
  }
</style>