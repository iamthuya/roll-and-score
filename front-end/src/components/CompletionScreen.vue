<script setup>
import { onMounted, ref } from 'vue';

const messages = [
	"Excellent work!  Kindly proceed to the team to retrieve your detailed report",
	"Nice rolls! Want to know how you did? Pop over to the booth staff for your skill breakdown!",
	"Sweet moves!  Time to check the stats! Head to the booth staff and get the inside scoop on your game!",
	"What a roll! Wondering how you did?  Swing by the booth staff for your game report!",
	"Great job!  Ever wonder how your rolls were?  Head on over to the booth staff for your report!",
	"Great shots!  Are you ready to see your performance breakdown?  Just hop over to the booth staff!",
	"Fantastic throw! Eager to see your score analysis? The booth staff has your detailed breakdown ready!",
	"Impressive game! For a complete review of your performance, the booth staff is waiting with your report.",
	"You nailed it! Want to analyze your winning throws? Go see the booth staff for all your game stats!",
	"Top-notch playing! Your results are in! The booth staff will give you all the details on your game."
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
		<div>
			<h1>Your Score: 1,234</h1>
			<p> {{ randomMessage }}</p>
		</div>
	</div>
</template>

<style scoped>

</style>