<script setup>

    defineProps({
        cancion: { type: Object , required: true },
        activa: { type: Boolean, default: false}
    });

    const emit= defineEmits(['seleccionar']);

    // helper local: segundos → "m:ss"
    const formatear= (seg)=> `${Math.floor(seg/60)}:${String(seg%60).padStart(2,'0')}`

    const onClick=(id)=> emit('seleccionar',id);
</script>
<template>
    <div class="mp-song" :class="{activa}" @click="onClick(cancion.id)">
        <span>{{ (activa) ? '🔊' : cancion.emoji }} </span>
        <span> {{ cancion.titulo }} </span>
        <span class="dur"> {{ formatear(cancion.duracion) }}  </span>
    </div>
</template>



