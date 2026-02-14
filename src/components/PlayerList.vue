<script setup lang="ts">
import type { Player } from '@/types/Player'
import { onMounted, ref } from 'vue'

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
  <ul>
    <li v-for="player in players" :key="player.PlayerID">
      {{ player.FirstName }} {{ player.LastName }}
    </li>
  </ul>
</template>

<style scoped>
li {
  color: white;
}
</style>
