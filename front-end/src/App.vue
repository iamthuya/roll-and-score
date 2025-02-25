<script setup>
import WelcomeScreen from './components/WelcomeScreen.vue';
import GameplayScreen from './components/GameplayScreen.vue';
import CompletionScreen from './components/CompletionScreen.vue';

import { ref, computed } from 'vue';
import StartScreen from './components/StartScreen.vue';

const gameState = ref("idling");
const currentScore = ref(0);
const ballCount = ref(0);

const possibleScores = [10, 20, 30, 40, 50, 100];

const currentComponent = computed(() => {
  if (gameState.value === "idling") {
    return WelcomeScreen;

  } else if (gameState.value === "starting") {
    return StartScreen;

  } else if (gameState.value === "playing") {
    return GameplayScreen;

  } else {
    return CompletionScreen;
  }

});

const getRandomScore = () => {
  const randomIndex = Math.floor(Math.random() * possibleScores.length);
  return possibleScores[randomIndex];
}

const increaseCount = () => {
  if (ballCount.value < 9) {
    if (ballCount.value === 0) {
      gameState.value = "playing";
    
    } else if (ballCount.value === 8) {
      gameState.value = "ending";
    }

    currentScore.value += getRandomScore();
    ballCount.value++;
  } 
};

const startGame = () => {
  gameState.value = "starting";
};

const resetGame = () => {
  gameState.value = "idling";
  currentScore.value = 0;
  ballCount.value = 0;
};

</script>

<template>
  <component :is="currentComponent" />

  <div class="simulation">
    <h2>Simulation</h2>
    <button type="button" @click="startGame" v-if="gameState === 'idling'">Start Game</button>
    <button type="button" @click="increaseCount" v-if="gameState !== 'idling'">Roll Ball</button>
    <button type="button" @click="resetGame" v-if="gameState !== 'idling'">Reset Game</button>
		<p>Ball rolled: {{ ballCount }} | Score: {{ currentScore }}</p>
    <p>Game State: {{ gameState }}</p>
	</div>
</template>

<style scoped>
.simulation {
  position: absolute;
  bottom: 0;
}

.simulation>button {
  margin-left: 10px;
}
</style>
