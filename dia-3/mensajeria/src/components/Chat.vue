<script setup>
import { ref, computed, watch } from 'vue'
import MensajeBurbuja from './MensajeBurbuja.vue';
const mensajes = ref([
  { id:1, texto:'¡Hola! ¿Cómo vas con Vue?', hora:'10:30', propio:false },
  { id:2, texto:'¡Genial! Ya entendí props y emits 🎉', hora:'10:31', propio:true },
  { id:3, texto:'Crack. ¿Y los componentes?', hora:'10:31', propio:false }
]);
const borrador= ref('');
let idActual=3;

const enviadosPorMi = computed(()=> mensajes.value.filter(m=> m.propio).length);

function enviar() {
    const texto= borrador.value.trim();
    if(!texto) return;

    mensajes.value.push({
        id: ++idActual,
        texto,
        hora: new Date().toLocaleTimeString('es-CL', { hour:'2-digit', minute:'2-digit' }),
        propio: true
    });

    borrador.value='';

}

watch(()=> mensajes.value.length, (nuevo,viejo)=>{
    console.log(`Mensajes: ${viejo} → ${nuevo}`);
    
});


</script>

<template>
    <div class="ch-app">
        <div class="ch-head">
            <div class="ava">🤖</div>
            <div>
                <strong>Profe Vue</strong>
                <small>en linea · {{ enviadosPorMi }} enviados por ti </small>
            </div>
        </div>
        <div class="ch-body">
            <MensajeBurbuja
            v-for="msg in mensajes"
            :key="msg.id"
            :mensaje="msg"
            />
        </div>
        <div class="ch-foot">
            <input type="text" v-model="borrador"
            placeholder="Escribe un mensaje..."
            @keyup.enter="enviar">
        <button class="btn" @click="enviar">➤</button>
        </div>
    </div>
</template>


