<script setup lang="ts">
import type { Team } from '@/types/Team'
import { onMounted, ref } from 'vue'
import TeamCard from './TeamCard.vue'

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
  <div v-for="team in teams" :key="team.ID">
    <TeamCard :team />
  </div>
</template>

<style lang="css" scoped>
li {
  color: white;
}
</style>
