<script setup>
import Pokedex from './components/Pokedex.vue';


</script>

<template>
  <Pokedex/>
</template>

<style>
.pk-toolbar { display:flex; gap:.5rem; flex-wrap:wrap; align-items:center; margin-bottom:.7rem; }
.pk-count { color:#64748b; font-size:.85rem; margin:0 0 .6rem; }
.pk-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(140px,1fr)); gap:.7rem; }
.pk-card { background:#fff; border:1px solid #e2e8f0; border-radius:12px; padding:.9rem; text-align:center; position:relative; }
.pk-img { width:82px; height:82px; object-fit:contain; }
.pk-name { font-weight:800; color:#1e293b; text-transform:capitalize; margin:.2rem 0; }
.pk-id { position:absolute; top:.5rem; left:.6rem; color:#cbd5e1; font-weight:800; font-size:.8rem; }
.pk-fav { position:absolute; top:.35rem; right:.5rem; cursor:pointer; font-size:1.05rem; background:none; border:none; }
.pk-types { display:flex; gap:.3rem; justify-content:center; flex-wrap:wrap; margin-top:.3rem; }
.pk-type { font-size:.68rem; padding:.1rem .5rem; border-radius:999px; color:#fff; font-weight:700; text-transform:capitalize; }
.pk-type.fuego { background:#f87171; }
.pk-type.agua { background:#38bdf8; }
.pk-type.planta { background:#42b883; }
.pk-type.electrico { background:#fbbf24; color:#1e293b; }
.pk-type.normal { background:#94a3b8; }
.pk-type.veneno { background:#a855f7; }
.pk-type.bicho { background:#a8b820; }
.pk-type.volador { background:#a5b4fc; color:#1e293b; }
</style>