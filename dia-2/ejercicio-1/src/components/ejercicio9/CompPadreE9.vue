<script setup>
import { ref } from 'vue';
import CompHijo1E9 from './CompHijo1E9.vue';
import CompHijo2E9 from './CompHijo2E9.vue';

const mensaje = ref('');

const onEscribio = (text) => mensaje.value = text;

</script>
<template>
    <div class="demo">
        <div class="child-box">
            <span class="tag-comp">&lt;entrada-texto&gt; (Padre)</span>
            <input type="text" placeholder="Escribe aquí..." v-model="mensaje">
        </div>
        <CompHijo1E9 @escribio="onEscribio" />
        <CompHijo2E9 :contenido="mensaje" />
    </div>
</template>