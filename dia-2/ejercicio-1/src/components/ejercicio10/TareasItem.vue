<script setup>
const props= defineProps({
    tarea:{ type: Object, required:true}
});

const emit= defineEmits(['toogle','eliminar']);

const onToogle =()=> emit('toogle', props.tarea.id);
const onBorrar =()=> emit('eliminar', props.tarea.id);

</script>
<template>
    <div class="task-item" :class="{ done: tarea.hecha }">
        <input type="checkbox" :checked="tarea.hecha" @change="onToogle">
        <span class="txt">{{ tarea.texto }}</span>
        <button class="btn-mini danger" @click="onBorrar">🗑</button>
    </div>
</template>
