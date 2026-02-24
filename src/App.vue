<script setup lang="ts">
import PlayerList from './components/PlayerList.vue'
import TeamList from './components/TeamList.vue'
</script>

<template>
  <!-- NavBar -->

  <div class="container">
    <div class="player-column">
      <PlayerList />
    </div>
    <div class="team-map-column">
      <div class="row"><TeamList /></div>
    </div>
  </div>

  <!-- Footer -->
</template>

<style scoped>
h1,
p {
  color: white;
}

.container {
  display: flex;
  flex-direction: row;
  width: 98vw;
  height: 98vh;
  justify-content: start;
  border: solid white 1px;
  margin: 0;
  padding: 0;
}

.player-column {
  display: flex;
  flex-direction: column;
  border: solid red 1px;
  height: 90%;
  width: 20%;
  overflow-y: scroll;

  overflow-x: hidden;
}

.team-map-column {
  display: flex;
  flex-direction: column;
  border: solid green 1px;
  height: 90%;
  width: 80%;
}
.row {
  display: flex;
  flex-direction: row;
  border: solid blue 1px;
  height: 10%;
  width: 100%;
}
</style>
