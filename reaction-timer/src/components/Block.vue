<template>
	<div class="block" v-if="showBlock" @click="stopTimer">Click Me!</div>
</template>
<script>
export default {
	name: "Block",
	props: ["delay"],
	data() {
		return {
			showBlock: false,
			timer: null,
			reactionTime: 0,
		};
	},
	// Lifecyle hooks
	mounted() {
		// setTimeout function, using the delay prop for its second argument
		setTimeout(() => {
			this.showBlock = true;
			this.startTimer();
		}, this.delay);
	},
	updated() {
		console.log(`Component updated with a delay of: ${this.delay}`);
	},
	methods: {
		// Function that adds 10 to the timer data propety every 10 miliseconds
		startTimer() {
			this.timer = setInterval(() => {
				this.reactionTime += 10;
			}, 10);
		},
		stopTimer() {
			// Stop the timer and clear the interval that was setup in the startTimer function above.
			clearInterval(this.timer);
			console.log(this.reactionTime);
			// Emit a custom event after the game is done, with the reaction time data
			this.$emit("gameFinished", this.reactionTime);
		},
	},
};
</script>

<style>
.block {
	width: 400px;
	border-radius: 20px;
	background: #0faf87;
	font-size: 1.5em;
	color: #fff;
	text-align: center;
	padding: 100px 0;
	margin: 40px auto;
	border: 3px solid rgb(52, 73, 94);
	font-weight: bold;
}
</style>
