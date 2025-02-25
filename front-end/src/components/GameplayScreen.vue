<script setup>
import { ref, onMounted } from 'vue';

const messages = [
    "Thor's throw! Dial back the thunder, we need accuracy not distance.",
    "Scenic detour! Aim a little left to hit your mark.",
    "Rocket arm! A little less 'blast off' and more 'gentle roll' please.",
    "Use the force! We need a bit more speed to reach those points.",
    "Jerky motion! Smooth out your release for a better roll.",
    "Too low of a roll! Raise your release for more lift.",
    "Are you the Hawkeye? Your aim is perfect!",
];
const randomMessage = ref("");

const pickRandomMessage = () => {
	const randomIndex = Math.floor(Math.random() * messages.length);
	randomMessage.value = messages[randomIndex];
}

onMounted(() => {
	pickRandomMessage();
});
</script>

<template>
    <div>
        <h3> {{ randomMessage }}</h3>
    </div>
</template>

<style scoped>

</style>