
<script setup>

defineProps({
    valor: {type: Number, required:true}
});
</script>

<template>
    <div class="counter-big">
        {{ valor }}
    </div>
</template>

