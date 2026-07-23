<script setup>
defineProps({
  texto:     { type: String,  required: true },
  indice:    { type: Number,  required: true },
  estado:    { type: String,  default: 'normal' },   // normal | correcta | incorrecta
  bloqueada: { type: Boolean, default: false }
})
const emit = defineEmits(['elegir'])
</script>
<template>
    <button class="tv-option" :class="estado"
          :disabled="bloqueada" @click="emit('elegir', indice)">
    {{ texto }}
  </button>
</template>


