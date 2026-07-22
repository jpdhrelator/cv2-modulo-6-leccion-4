<script setup>
defineProps({
    nombre: {type: String, required: true},
    precio: {type: Number, required: true},
    stock: {type: Number, default: 0}
});

</script>
<template>
    <div class="tarjeta">
        <h4>{{ nombre }}</h4>
        <p class="price"> ${{ precio.toLocaleString("es-CL") }}</p>
        <p v-if="stock > 0">{{ stock }} en stock</p>
        <p v-else>❌ Sin stock</p>
    </div>
</template>