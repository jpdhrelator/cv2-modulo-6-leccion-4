<script setup>
import { ref } from 'vue';

const eventos= ref([]);
const log=(txt)=>{
    eventos.value.unshift(txt)
    if (eventos.value.length > 8) eventos.value.pop()
}

</script>
<template>
  <div class="demo" id="app-stop">
    <h4>▶ Demo en vivo — compara con y sin .stop</h4>
    <p style="color:#334155; margin:.2rem 0;">Caja exterior = PADRE. Caja roja interior = HIJA.</p>
    <div class="event-box" @click="log('PADRE 🟦')">
      Soy el PADRE (haz clic en mí)
      <div class="event-box inner" @click.stop="log('HIJA con .stop 🟥')">
        HIJA con <b>.stop</b> — no molesto al padre
      </div>
      <div class="event-box inner" style="background:#fde68a; border-color:#b45309; color:#78350f;"
        @click="log('HIJA sin .stop 🟨 → burbujea')">
        HIJA sin .stop — el clic burbujea al padre
      </div>
    </div>
    <div class="log">
      <div v-if="eventos.length === 0" class="empty">Haz clic en las cajas y compara.</div>
      <div v-for="(e, i) in eventos" :key="i" class="line">▸ {{ e }}</div>
    </div>
  </div>
</template>

<style scoped></style>