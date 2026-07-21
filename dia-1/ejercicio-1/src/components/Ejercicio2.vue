<script setup>
import { ref } from 'vue';

const showMessage = () => alert('¡Hola!');


</script>
<template>
    <div>
        <button onclick="showMessage()">Click js Nativo</button>
        <button @click="showMessage()">Click @</button>
    </div>
</template>
