<script setup lang="ts">
import type { Player } from '@/types/Player'

interface Props {
  player: Player
}

const { player } = defineProps<Props>()
</script>

<template>
  <div class="card">
    <div class="row">
      <h3>{{ player.Position }}</h3>
      <h3>{{ player.FirstName }} {{ player.LastName }}</h3>
    </div>
    <div class="row">
      <h4>Hometown: {{ player.City }}, {{ player.State }}</h4>
    </div>
  </div>
</template>

<style lang="css" scoped>
.card {
  display: flex;
  flex-direction: column;
  border: solid white 1px;
  width: 100%;
  height: 100px;
  align-items: start;
  justify-content: center;
  margin-bottom: 10px;
}

.row {
  display: flex;
  display: row;
  gap: 15px;
  align-items: start;
  justify-content: center;
  margin: 0;
  padding-left: 5px;
  padding-right: 5px;
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
