<script setup>
import { ref } from 'vue';

const evento=ref('click');
const veces=ref(0);
const disparar= ()=>{ veces.value++}


</script>
<template>
   <div class="demo" id="app-dinamico">
      <h4>▶ Demo en vivo — cambia el tipo de evento en caliente</h4>
      <label>¿Qué evento debe escuchar el botón?</label>
      <select v-model="evento" style="max-width:220px;">
        <option value="click">click</option>
        <option value="mouseenter">mouseenter</option>
        <option value="mouseleave">mouseleave</option>
        <option value="dblclick">dblclick</option>
      </select>
      <div class="grid-btns" style="margin-top:1rem;">
        <button class="btn" @[evento]="disparar">Reacciono a: <b>@{{ evento }}</b></button>
      </div>
      <div class="out">Veces disparado: <b>{{ veces }}</b></div>
    </div>
</template>
