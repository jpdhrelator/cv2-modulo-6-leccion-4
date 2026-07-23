<script setup>

    defineProps({
        poke:{type: Object, required:true} // { id, nombre, tipos, sprite, favorito }
    });

    const emit= defineEmits(['favorito'])

</script>
<template>
    <div class="pk-card">
        <span class="pk-id">{{ poke.id }}</span>
        <button class="pk-fav"  @click="emit('favorito',poke.id)">
            {{ poke.favorito ? '❤️' : '🤍' }}
        </button>
        <img class="pk-img" :src="poke.sprite" :alt="poke.nombre">
        <p class="pk-name"> {{ poke.nombre }}</p>
        <div class="pk-types">
            <span v-for="t in poke.tipos"
                :key="t"
                class="pk-type"
                :class="t"
            >{{ t }}</span>
        </div>
    </div>
</template>



