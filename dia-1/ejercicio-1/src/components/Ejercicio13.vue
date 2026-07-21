<script setup>
import { computed, ref } from 'vue';

const TAM = 5
const jugador = ref({ x: 0, y: 0 })
const meta = ref({ x: 4, y: 4 })
const puntos = ref(0)
const pasos = ref(0)


 const nuevaMeta = () => {
        let x, y
        do {
          x = Math.floor(Math.random() * TAM)
          y = Math.floor(Math.random() * TAM)
        } while (x === jugador.value.x && y === jugador.value.y)
        meta.value = { x, y }
      }
 const mover = (dx, dy) => {
        const nx = jugador.value.x + dx
        const ny = jugador.value.y + dy
        if (nx < 0 || nx >= TAM || ny < 0 || ny >= TAM) return
        jugador.value = { x: nx, y: ny }
        pasos.value++
        if (nx === meta.value.x && ny === meta.value.y) {
          puntos.value++
          nuevaMeta()
        }
      }
const reiniciar = () => {
        jugador.value = { x: 0, y: 0 }
        meta.value = { x: 4, y: 4 }
        puntos.value = 0
        pasos.value = 0
      }

const celdas = computed(() => {
        const arr = []
        for (let y = 0; y < TAM; y++) {
          for (let x = 0; x < TAM; x++) {
            const esJugador = x === jugador.value.x && y === jugador.value.y
            const esMeta = x === meta.value.x && y === meta.value.y
            arr.push({
              i: y * TAM + x,
              esJugador,
              esMeta,
              contenido: esJugador ? '🚀' : (esMeta ? '🎯' : '')
            })
          }
        }
        return arr
      })

</script>
<template>
<div class="demo" id="app-juego">
      <h4>▶ Demo en vivo — haz clic en el tablero y usa las flechas ⬅️⬆️⬇️➡️</h4>
      <p style="color:#334155; margin:.2rem 0;">👉 Primero <b>haz clic en la grilla</b> para darle foco, luego mueve con las flechas. <b>Doble clic</b> para reiniciar.</p>

      <div class="board" tabindex="0"
        @keydown.up.prevent="mover(0, -1)"
        @keydown.down.prevent="mover(0, 1)"
        @keydown.left.prevent="mover(-1, 0)"
        @keydown.right.prevent="mover(1, 0)"
        @dblclick="reiniciar">
        <div v-for="c in celdas" :key="c.i"
             class="cell"
             :class="{ player: c.esJugador, goal: c.esMeta }">
          {{ c.contenido }}
        </div>
      </div>

      <div class="hud">
        <div class="stat">Puntos: <b>{{ puntos }}</b></div>
        <div class="stat">Pasos: <b>{{ pasos }}</b></div>
        <button class="btn" @click="reiniciar">🔄 Reiniciar</button>
        <span v-if="puntos >= 5" class="win-msg">🏆 ¡Llegaste a 5! ¿Y con menos pasos?</span>
      </div>
    </div>

</template>
<style scoped></style>