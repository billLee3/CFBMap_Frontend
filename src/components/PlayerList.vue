<script setup lang="ts">
import type { Player } from '@/types/Player'
import { onMounted, ref } from 'vue'
import PlayerCard from './PlayerCard.vue'

const players = ref<Player[]>([])
const loading = ref(true)
const error = ref<string | null>(null)

const fetchPlayers = async (): Promise<void> => {
  try {
    const response = await fetch('http://localhost:8080/players')
    if (!response.ok) {
      throw new Error(`HTTP Error: Unable to fetch.`)
    }
    const data: Player[] = await response.json()
    players.value = data
  } catch (err) {
    error.value = err instanceof Error ? err.message : 'An unknown error has occured'
  } finally {
    loading.value = false
  }
}

//Fetches the players everytime the component is loaded
onMounted(() => {
  fetchPlayers()
})
</script>

<template>
  <div class="container" v-for="player in players" :key="player.PlayerID">
    <!-- {{ player.FirstName }} {{ player.LastName }} -->
    <PlayerCard :player="player" />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  direction: column;
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
}

li {
  color: white;
}
</style>
