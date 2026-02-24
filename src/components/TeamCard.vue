<script setup lang="ts">
import type { Team } from '@/types/Team'

interface Props {
  team: Team
}

const { team } = defineProps<Props>()
</script>

<template>
  <div class="container">
    <h3>{{ team.Name }}</h3>
  </div>
</template>

<style lang="css" scoped{>
.container {
  display: flex;
  flex-direction: row;
  padding-left: 15px;
  border: solid white 1px;
  width: 10vw;
  height: 10vh;
  align-items: center;
  justify-content: center;
}

.row {
  display: flex;
  display: row;
  gap: 15px;
  align-items: start;
  justify-content: center;
  margin: 0;
  padding-top: 5px;
  padding-bottom: 5px;
}

h2,
h3,
h4 {
  color: white;
  margin: 0;
}
</style>
