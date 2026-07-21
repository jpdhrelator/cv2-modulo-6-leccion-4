<script setup>
import {  ref } from 'vue';

const contador=ref(0);
const encendido= ref(false);

</script>
<template>
 <div class="demo" id="app-inline">
      <h4>▶ Demo en vivo</h4>
      <div class="counter-big">{{ contador }}</div>
      <div class="grid-btns">
        <button class="btn" @click="contador++">+1</button>
        <button class="btn ghost" @click="contador--">-1</button>
        <button class="btn ghost" @click="contador = 0">Reset</button>
        <button class="btn" @click="encendido = !encendido">
          {{ encendido ? '💡 Apagar' : '🌑 Encender' }}
        </button>
      </div>
      <div class="out">Luz: <b>{{ encendido ? 'ON' : 'OFF' }}</b></div>
    </div>
</template>
