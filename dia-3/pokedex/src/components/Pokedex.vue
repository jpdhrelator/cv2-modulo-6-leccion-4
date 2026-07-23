<script setup>
import { ref, computed } from 'vue'
import { pokemon as datos } from '../pokemon-data.js'
import PokeCard from './PokeCard.vue';

const pokemon = ref(datos);

const busqueda = ref('');
const tipoSel = ref('todos');
const orden = ref('id'); // id | nombre
const soloFavoritos = ref(false);

const tipos = computed(() => ['todos', ...new Set(pokemon.value.flatMap(p => p.tipos))])

// PIPELINE: filtra por texto → tipo → favoritos → ordena
const resultado = computed(() =>
    pokemon.value
        .filter(p => p.nombre.includes(busqueda.value.toLowerCase()))
        .filter(p => tipoSel.value === 'todos' || p.tipos.includes(tipoSel.value))
        .filter(p => !soloFavoritos.value || p.favorito)
        .sort((a, b) => orden.value === 'nombre' ? a.nombre.localeCompare(b.nombre) : a.id - b.id)
);

function toogleFavorito(id) {
    
    
    const p = pokemon.value.find(pk => pk.id === id);
    
    if(p) p.favorito= !p.favorito 
}

</script>
<template>
    <div class="pk-toolbar">
        <input type="text" v-model="busqueda" placeholder="🔍 Buscar...">
        <select v-model="tipoSel">
            <option v-for="t in tipos" :key="t" :value="t">{{ t }}</option>
        </select>
        <select v-model="orden">
            <option value="id">Orden: N°</option>
            <option value="nombre">Orden: A-Z</option>
        </select>
        <label><input type="checkbox" v-model="soloFavoritos"> ❤️ Favoritos</label>
    </div>
    <p class="pk-count">{{ resultado.length }} de {{ pokemon.length }} pokémon</p>
    <div class="pk-grid">
        <PokeCard
            v-for="pk in resultado"
            :key="pk.id"
            :poke="pk"
            @favorito="toogleFavorito"
        />
    </div>
</template>
