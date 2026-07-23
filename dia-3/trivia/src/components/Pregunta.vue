<script setup>
import OpcionRespuesta from './OpcionRespuesta.vue'

const props = defineProps({
  pregunta:   { type: Object,  required: true },   // { enunciado, opciones, correcta }
  seleccion:  { type: Number,  default: null },
  respondida: { type: Boolean, default: false }
})
const emit = defineEmits(['responder'])
function estadoDe(indice) {
  if (!props.respondida) return 'normal'
  if (indice === props.pregunta.correcta) return 'correcta'
  if (indice === props.seleccion)         return 'incorrecta'
  return 'normal'
}

</script>

<template>
    <p class="tv-question">{{ pregunta.enunciado }}</p>
    <div class="tv-options">
        <OpcionRespuesta
        v-for="(preg,i) in pregunta.opciones"
        :key="preg"
        :texto="preg"
        :indice="i"
        :estado="estadoDe(i)"
        :bloqueada="respondida"
        @elegir="emit('responder',$event)"
        />
    </div>
</template>

