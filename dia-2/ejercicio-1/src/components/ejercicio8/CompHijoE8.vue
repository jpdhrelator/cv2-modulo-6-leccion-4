<script setup>
import { ref } from 'vue';

const cantidad= defineModel({type: Number})

function mas() {
    cantidad.value++;
}
function menos() {
    cantidad.value --;
}

</script>
<template>   
    <div class="qty-ctrl">
        <button class="btn-mini" @click="menos">−</button>
        <b>{{ cantidad }}</b>
        <button class="btn-mini" @click="mas">+</button>
      </div>
</template>



