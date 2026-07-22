
<script setup>
import { ref } from 'vue';
import CompHijoE5 from './CompHijoE5.vue';

const total= ref(0);

</script>
<template>
    <div class="demo">
        <p>Total en el padre: <strong>{{ total }}</strong></p>
        <CompHijoE5 @sumar="total++"/>
    </div>
</template>