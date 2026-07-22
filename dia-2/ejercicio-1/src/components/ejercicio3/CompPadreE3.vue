<script setup>
import { ref } from 'vue';
import CompHijoE3 from './CompHijoE3.vue';


const contador= ref(0);
</script>

<template>
    <div class="demo">
        <button class="btn" @click="contador++">+1</button>
        <CompHijoE3 :valor="contador"/>
    </div>
</template>