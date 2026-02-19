<script setup lang="ts">
import PlayerList from './components/PlayerList.vue'
import TeamList from './components/TeamList.vue'
</script>

<template>
  <h1>You did it!</h1>
  <p>
    Visit <a href="https://vuejs.org/" target="_blank" rel="noopener">vuejs.org</a> to read the
    documentation
  </p>
  <PlayerList />
  <TeamList />
</template>

<style scoped>
h1,
p {
  color: white;
}
</style>
