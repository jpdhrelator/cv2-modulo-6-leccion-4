<script setup>
import { ref, computed } from 'vue';
import CancionItem from './CancionItem.vue';

const canciones = ref([
    { id: 1, titulo: 'Bohemian Rhapsody', artista: 'Queen', duracion: 354, emoji: '👑' },
    { id: 2, titulo: 'Billie Jean', artista: 'Michael Jackson', duracion: 294, emoji: '🕺' },
    { id: 3, titulo: 'Smells Like Teen Spirit', artista: 'Nirvana', duracion: 301, emoji: '🎸' },
    { id: 4, titulo: 'Take on Me', artista: 'a-ha', duracion: 225, emoji: '🎹' }
]);

const indiceActual = ref(0);
const reproduciendo = ref(false);
const volumen = ref(70);

const cancionActual = computed(() => canciones.value[indiceActual.value]);
const formatear = (seg) => `${Math.floor(seg / 60)}:${String(seg % 60).padStart(2, '0')}`

function togglePlay() {
    reproduciendo.value = !reproduciendo.value;
}
function siguiente() {
    indiceActual.value = (indiceActual.value + 1) % canciones.value.length
}
function anterior() {
    indiceActual.value = (indiceActual.value - 1 + canciones.value.length) % canciones.value.length
}
function seleccionar(id) {
    indiceActual.value = canciones.value.findIndex((c) => c.id === id);
    reproduciendo.value = true;
}

console.log(cancionActual.value);

</script>
<template>
    <div class="mp-player">
        <div class="mp-now">
            <div class="mp-cover">
                {{ cancionActual?.emoji }}
            </div>
            <div>
                <p class="mp-title"> {{ cancionActual.titulo }}</p>
                <p class="mp-artist">{{ cancionActual.artista }}</p>
            </div>
        </div>

        <div class="mp-bar"><i style="width:35%"></i></div>
        <div class="mp-time">
            <span>1:42</span> <span>{{ formatear(cancionActual.duracion) }}</span>
        </div>

        <div class="mp-controls">
            <button class="mp-btn" @click="anterior">⏮</button>
            <button class="mp-btn play" @click="togglePlay">{{ reproduciendo ? '⏸' : '▶' }}</button>
            <button class="mp-btn" @click="siguiente">⏭</button>
        </div>
        <div class="mp-vol">
            🔈 <input type="range" min="0" max="100" v-model="volumen"> {{ volumen }}%
        </div>
        <div class="mp-list">
            <CancionItem
                v-for="cancion in canciones"
                :key="cancion.id"
                :cancion="cancion"
                :activa=" cancion.id === cancionActual.id"
                @seleccionar="seleccionar"
            />
        </div>
    </div>
</template>