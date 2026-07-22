<script setup>
import { ref } from 'vue';
import Ejercicio1Hijo from './Ejercicio1Hijo.vue';



const nombreRef=ref('Grace');

setTimeout(()=>nombreRef .value="Alberto" ,3500);

</script>
<template>
    <div>
       <Ejercicio1Hijo nombre="Juan"/>
       <Ejercicio1Hijo nombre="Marta"/>
       <Ejercicio1Hijo :nombre="nombreRef"/>
    </div>
</template>

