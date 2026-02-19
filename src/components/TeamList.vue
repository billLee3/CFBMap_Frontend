<script setup lang="ts">
import type { Team } from '@/types/Team'
import { onMounted, ref } from 'vue'

const teams = ref<Team[]>([])
const loading = ref(true)
const error = ref<string | null>(null)

const fetchTeams = async (): Promise<void> => {
  try {
    const response = await fetch('http://localhost:8080/teams')
    if (!response.ok) {
      throw new Error(`HTTP Error: Unable to fetch.`)
    }
    const data: Team[] = await response.json()
    teams.value = data
  } catch (err) {
    error.value = err instanceof Error ? err.message : 'An unknown error has occured'
  } finally {
    loading.value = false
  }
}

onMounted(() => {
  fetchTeams()
})
</script>

<template>
  <ul>
    <li v-for="team in teams" :key="team.ID">
      {{ team.Name }}
    </li>
  </ul>
</template>

<style lang="css" scoped>
li {
  color: white;
}
</style>
