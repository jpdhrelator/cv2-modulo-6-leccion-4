<script setup>
import TarjetaProducto from './TarjetaProducto.vue';


</script>
<template>
    <div class="demo">
        <div class="row">
            <TarjetaProducto :nombre="'Teclado'" :precio="29000" :stock="5"/>
            <TarjetaProducto nombre="Mouse" :precio="15990"/>
        </div>

    </div>
</template>
