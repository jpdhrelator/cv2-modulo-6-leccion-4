<script setup>
import { ref } from 'vue';

const mensaje= ref("Aún no me saludas");
const event=ref('click')

function saludar() {
    mensaje.value='¡Hola! Evento capturado 👋';
}

setTimeout(()=>{event.value='dbclick'},2500)

</script>
<template>
    <div>
        <button v-on:click="saludar"> Salurdar Usando v-on</button>
        <br/>
        <button @click="saludar"> Salurdar Usando @</button>
        <br/>
        <button @[event]="saludar"> Salurdar Usando @[]</button>
        <button @dblclick="saludar"> Salurdar Usando @[]</button>
        <br/>

        <p>{{ mensaje }}</p>
        <small> ele evento del boton:{{ event }}</small>
    </div>
</template>
