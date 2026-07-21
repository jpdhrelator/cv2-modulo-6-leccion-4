<script setup>
import { ref } from 'vue';
const texto= ref('');
const items= ref([]);
function agregar() {
  if(texto.value.trim()==='')return;
  items.value.push(texto.value.trim());
  texto.value='';
}

</script>
<template>
  <div class="demo" id="app-teclas">
      <h4>▶ Demo en vivo</h4>
      <label>Nuevo ítem</label>
      <input type="text" v-model="texto"
             @keydown.enter="agregar"
             @keydown.esc="texto = ''"
             placeholder="Escribe y presiona Enter (Esc limpia)" />
      <div style="margin-top:.4rem;">
        <span class="pill" v-for="(it, i) in items" :key="i">{{ it }}</span>
        <span v-if="items.length === 0" class="muted-txt">Aún no agregas nada. Escribe y presiona Enter.</span>
      </div>
    </div>
</template>

<style scoped></style>