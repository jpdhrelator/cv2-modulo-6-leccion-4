<script setup>
import { computed } from 'vue'
const props = defineProps({
    puntaje: { type: Number, required: true },
    total: { type: Number, required: true }
})
const emit = defineEmits(['reiniciar'])
const mensaje = computed(() => {
    const pct = props.puntaje / props.total
    if (pct === 1) return '¡Perfecto! 🏆'
    if (pct >= 0.6) return '¡Bien jugado! 🎉'
    return 'Sigue practicando 💪'
});
</script>

<template>
    <div class="tv-center">
        <div class="tv-big">{{ puntaje }}/{{ total }}</div>
        <p>{{ mensaje }}</p>
        <button class="tv-btn" @click="emit('reiniciar')">Jugar de nuevo</button>
    </div>
</template>
