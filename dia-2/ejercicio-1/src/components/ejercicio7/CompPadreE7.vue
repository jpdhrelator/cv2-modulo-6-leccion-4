<script setup>
import { ref } from 'vue';
import CompHijoE7 from './CompHijoE7.vue';

const estado=ref('Esperando Acción');

function onGuardar(text) {
    estado.value =`✅ Guardado: ${text || '(vacío)'} `;
}
function onCancelar() {
    estado.value = '❌ Cancelado';
}
</script>
<template>
    <div class="demo">
            <h4>👁 Vista previa </h4>
            <p class="out">{{ estado }}</p>
            <CompHijoE7 @guardar="onGuardar" @cancelar="onCancelar" />
        </div>
</template>