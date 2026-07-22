
<script setup>
import { computed, ref } from 'vue';
import NuevaTarea from './NuevaTarea.vue';
import TareasItem from './TareasItem.vue';

let idActual = 3
const tareas = ref([
  { id: 1, texto: 'Entender props', hecha: true  },
  { id: 2, texto: 'Entender emits', hecha: false }
])

function agregarTarea(texto) {
    tareas.value.push({id:++idActual, texto, hecha:false})
}
function toogleTarea(id) {
  const t = tareas.value.find(x => x.id === id);
  if (t) t.hecha = !t.hecha;
}
function eliminarTarea(id) {
  tareas.value = tareas.value.filter(x => x.id !== id)
}
const pendientes = computed(() =>
  tareas.value.filter(t => !t.hecha).length
)

</script>
<template>
    <div class="demo">
        <h3 style="margin:.2rem 0">Mis tareas ({{ pendientes }} pendientes)</h3>
        <NuevaTarea @agregar="agregarTarea"/>

        <TareasItem
        v-for="tarea in tareas"
        :key="tarea.id"
        :tarea="tarea"
        @toogle="toogleTarea"
        @eliminar="eliminarTarea"
        />
    </div>
</template>
