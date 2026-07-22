<script setup>


defineProps({
    nombre: String
})
</script>
<template>
    <div>
        <p>👋 ¡Hola, <strong>{{ nombre }}</strong>!</p>
    </div>
</template>

