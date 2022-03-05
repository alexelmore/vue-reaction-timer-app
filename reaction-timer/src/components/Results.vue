<template>
	<div class="results">
		<h1>Results</h1>
		<h2>Reaction Time: {{ gameResults }}</h2>
		<h2>{{ message }}</h2>
	</div>
</template>
<script>
export default {
	name: "Results",
	props: ["gameResults"],
	data() {
		return {
			message: "",
		};
	},
	created() {
		if (this.gameResults <= 150) {
			this.message = "Amazing! You have super human reactions!";
		}
		if (this.gameResults > 150 && this.gameResults < 200) {
			this.message = "Nice! You have good reactions!";
		}
		if (this.gameResults > 200 && this.gameResults < 300) {
			this.message = "Decent Reactions...";
		}
		if (this.gameResults > 300 && this.gameResults < 350) {
			this.message = "Your reactions are average at best...";
		}
		if (this.gameResults > 350) {
			this.message =
				"SLOW! Vladimir Ilʹich Lenin has better reactions than you!";
		}
	},
};
</script>

<style>
.results {
	color: #2c3e50;
	margin-top: 60px;
}
.results {
	width: fit-content;
	border-radius: 20px;
	background: #0faf87;
	font-size: 1.5em;
	color: #fff;
	text-align: center;
	padding: 50px;
	margin: 40px auto;
	border: 3px solid rgb(52, 73, 94);
	font-weight: bold;
}
</style>
