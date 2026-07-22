<script setup>

const emit= defineEmits(['sumar']);

function avisar() {
    emit('sumar');
}
</script>
<template>
    <div>
       <button class="btn" @click="avisar"> +1</button>
    </div>
</template>



