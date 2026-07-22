<script setup>
import { ref } from 'vue';

const emit = defineEmits(['escribio']);
const onInput= (e)=>emit('escribio',e.target.value)

</script>
<template>
    <div class="child-box">
        <span class="tag-comp">&lt;entrada-texto&gt; (hermano A)</span>
        <input type="text" placeholder="Escribe aquí..." @input="onInput">
    </div>
</template>
