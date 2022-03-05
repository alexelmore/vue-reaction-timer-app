<template>
	<h1>Vue Reaction Timer Game</h1>

	<button class="btn" @click="startNewGame" :disabled="isPlaying">
		Start New Game
	</button>
	<Block @gameFinished="endGame" v-if="isPlaying" :delay="delay" />
	<Results v-if="gameResults" :gameResults="gameResults" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
	name: "App",
	components: {
		Block,
		Results,
	},
	data() {
		return {
			isPlaying: false,
			delay: null,
			gameResults: null,
		};
	},
	methods: {
		startNewGame() {
			this.delay = 2000 + Math.random() * 5000;
			this.isPlaying = true;
			this.gameResults = null;
		},
		endGame(results) {
			console.log("fired reset!", results);
			this.gameResults = results;
			this.isPlaying = false;
		},
	},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
.btn {
	display: block;
	width: fit-content;
	font-size: 1.5em;
	color: #fff;
	padding: 8px 20px;
	border-radius: 4px;
	background-color: rgb(65, 184, 131);
	cursor: pointer;
	text-decoration: none;
	margin: 20px auto;
	border: 3px solid rgb(52, 73, 94);
}
button[disabled] {
	opacity: 0.2;
	cursor: not-allowed;
}
</style>
