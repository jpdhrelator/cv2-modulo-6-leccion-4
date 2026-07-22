<script setup>
import { ref } from 'vue';
import CompHijoE8 from './CompHijoE8.vue';

const cant= ref(0);
</script>
<template>
    <div class="demo">  
        <p>Cantidad: <strong>{{ cant }}</strong></p>          
            <CompHijoE8 v-model="cant" />
        </div>
</template>