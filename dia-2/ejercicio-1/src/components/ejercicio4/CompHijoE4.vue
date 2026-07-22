<script setup>

defineProps({
    nombre:{type: String, required:true},
    rol:{type: String, default: 'Sin rol'},
});
</script>
<template>
    <div class="user">
        <div class="avatar"> {{ nombre.charAt(0) }}</div>
        <div>
            <strong>{{ nombre }}</strong>
            <span class="muted-text"> {{ rol }}</span>
        </div>
    </div>
</template>



