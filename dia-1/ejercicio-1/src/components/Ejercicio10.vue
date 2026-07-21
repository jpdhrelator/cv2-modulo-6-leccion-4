<script setup>
import { ref } from 'vue';
const bonos = ref(0)
const reclamar = () => { bonos.value++ }

</script>
<template>
<div class="demo" id="app-once">
      <h4>▶ Demo en vivo</h4>
      <button class="btn" @click.once="reclamar">🎁 Reclamar bono (solo 1 vez)</button>
      <div class="out">Bonos reclamados: <b>{{ bonos }}</b> — {{ bonos > 0 ? 'ya no suma más' : 'aún disponible' }}</div>
    </div>
</template>

<style scoped></style>