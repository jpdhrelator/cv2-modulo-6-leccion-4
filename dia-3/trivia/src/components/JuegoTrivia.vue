<script setup>
import { ref, computed, watch } from 'vue';
import PantallaResultado from './PantallaResultado.vue';
import Pregunta from './Pregunta.vue';

const preguntas = [
    { enunciado: '¿Qué directiva enlaza un input en dos vías?', opciones: ['v-bind', 'v-model', 'v-for', 'v-if'], correcta: 1 },
    { enunciado: '¿Cómo baja un dato de padre a hijo?', opciones: ['emit', 'props', 'watch', 'ref'], correcta: 1 },
    { enunciado: '¿Qué macro declara eventos en script setup?', opciones: ['defineEmits', 'defineData', 'useEmit', 'onEmit'], correcta: 0 },
    { enunciado: '¿Qué cachea un valor derivado?', opciones: ['method', 'watch', 'computed', 'props'], correcta: 2 }
]
const estado = ref('inicio')   // inicio | jugando | fin
const indice = ref(0)
const puntaje = ref(0)
const seleccion = ref(null)
const respondida = ref(false)
const tiempo = ref(15)
let timer = null

const preguntaActual = computed(() => preguntas[indice.value]);
const progreso = computed(() => (indice.value / preguntas.length) * 100);


function iniciar() {
    estado.value = 'jugando';
    indice.value = 0;
    puntaje.value = 0;
    cargarPregunta();
}

function cargarPregunta() {
    seleccion.value = null;
    respondida.value = false;
    tiempo.value = 15;
    clearInterval(timer);
    timer = setInterval(() => {
        tiempo.value--;
        if (tiempo.value <= 0) responder(null);
    }, 1000)
}
function responder(i) {
    if (respondida.value) return;

    respondida.value = i;
    clearInterval(timer);
    if (i === preguntaActual.value.correcta) puntaje.value++;
    setTimeout(siguiente, 1200);// muestra el feedback y avanza
}

function siguiente() {
    if (indice.value + 1 >= preguntas.length) {
        estado.value = 'fin';
        return;
    }
    indice.value++;
    cargarPregunta();
}
function reiniciar() {
    iniciar();
}

// watch: avisa cuando el tiempo entra en zona crítica
watch(tiempo, (t) => { if (t === 5) console.log('¡Quedan 5 segundos!') })

</script>

<template>
    <div class="tv-game">

        <div v-if="estado === 'inicio'" class="tv-center">
            <div class="tv-big">❓</div>
            <h3>Trivia Vue</h3>
            <p>{{ preguntas.length }} preguntas · 15s cada una</p>
            <button class="tv-btn" @click="iniciar">Empezar</button>
        </div>
        <div v-else-if="estado === 'jugando'">
            <div class="tv-hud">
                <span>Pregunta <b>{{ indice + 1 }}</b>/{{ preguntas.length }}</span>
                <span>Puntaje: <b>{{ puntaje }}</b></span>
            </div>
            <div class="tv-progress"><i :style="{ width: progreso + '%' }"></i></div>
            <div class="tv-timer" :class="{ urgente: tiempo <= 5 }">⏱ {{ tiempo }}s</div>
            <Pregunta 
            :pregunta="preguntaActual" 
            :seleccion="seleccion" 
            :respondida="respondida"
            @responder="responder" />
        </div>
        <PantallaResultado v-else :puntaje="puntaje" :total="preguntas.length" @reiniciar="reiniciar" />

    </div>
</template>
