<template>
	<h1>Vue Reaction Timer</h1>
	<Results />

	<button class="btn" @click="startNewGame" :disabled="isPlaying">
		Start New Game
	</button>
	<Block v-if="isPlaying" :delay="delay" />
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
		};
	},
	methods: {
		startNewGame() {
			this.delay = 2000 + Math.random() * 5000;
			this.isPlaying = true;
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
.btn:disabled {
	cursor: not-allowed;
	background-color: #cccccc;
	color: #666666;
}
</style>
