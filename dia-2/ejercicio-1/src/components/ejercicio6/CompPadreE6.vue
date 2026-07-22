
<script setup>
import { ref } from 'vue';
import CompHijoE6 from './CompHijoE6.vue';
const elegido = ref('');

function elegir(col) {
    elegido.value=col;
}

</script>
<template>
    <div class="demo">
        <p>Último color <strong>{{ elegido || '-' }}</strong></p>
        <CompHijoE6 @elegido="elegir"/>
    </div>
</template>