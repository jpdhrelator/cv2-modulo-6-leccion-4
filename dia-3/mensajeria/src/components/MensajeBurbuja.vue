<script setup>
    defineProps({
        mensaje:{ type: Object, required: true}
    });
</script>
<template>
    <div class="ch-msg" :class="(mensaje.propio)? 'propio':'ajeno' ">
        {{ mensaje.texto }}
        <span class="hora"> {{ mensaje.hora }}</span>
    </div>
</template>



