<script setup>
import { ref } from 'vue';

const eventos= ref([]);
const log=(txt)=>{
    eventos.value.unshift(txt)
    if (eventos.value.length > 8) eventos.value.pop()
}


</script>
<template>
    <section class="card">
    <div class="event-box"
        @click="log('click')"
        @dbclick="log('dbclick')"
        @mouseenter="log('mouseenter')"
        @mouseleave="log('mouseleave')"
        @mousedown="log('mousedown')"
        @mouseup="log('mouseup')"
    > 
    Interactua conmigo

    </div>

    <div class="row" style="margin-top:1rem;">
        <div>
          <label>Escribe algo (evento <b>input</b>)</label>
          <input type="text" @input="log('input → ' + $event.target.value)" placeholder="Escribe..." />
        </div>
        <div>
          <label>Elige (evento <b>change</b>)</label>
          <select @change="log('change → ' + $event.target.value)">
            <option value="">— selecciona —</option>
            <option value="Vue">Vue</option>
            <option value="React">React</option>
            <option value="Angular">Angular</option>
          </select>
        </div>
      </div>


    <div class="log">
        <div v-if="eventos.length === 0" class="empty">Aún no hay eventos. Interactúa arriba ☝️</div>
        <div v-for="(e, i) in eventos" :key="i" class="line">▸ {{ e }}</div>
      </div>
    </section>
</template>
