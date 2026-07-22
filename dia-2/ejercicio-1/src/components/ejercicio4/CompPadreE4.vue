
<script setup>
import { ref } from 'vue';
import CompHijoE4 from './CompHijoE4.vue';


const usuarios= ref([
    { id: 1, nombre:"Ada" ,rol: "Frontend"},
    { id: 2, nombre:"Luis" ,rol: "Backend"},
    { id: 3, nombre:"Grace" ,rol: "DevOps"},
]);

</script>
<template>
    <div class="demo">
        <CompHijoE4 
         v-for="usu in usuarios"
        :key="usu.id"
        :nombre="usu.nombre"
        :rol="usu.rol"
        />
    </div>
</template>