<script setup>
import { ref } from 'vue';

defineProps({
    contenido:{type: String, default:''}
});

</script>
<template>   
   <div class="child-box">
        <span class="tag-comp">&lt;pantalla-texto&gt; (hermano B)</span>
        <p style="font-size:1.2rem;margin:.3rem 0">{{ contenido || 'Esperando texto...' }}</p>
      </div>
</template>



