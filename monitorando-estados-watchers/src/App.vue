
<template>
	<div id="app">
		<input
			type="text"
			v-model="text"
		>
		<span>Text: {{ text }}</span>
		<span>Api: {{ apiResponse }}</span>
	</div>
</template>

<script>
	export default {
		name: "App",
		data() {
			return {
				apiResponse: "Start",
				text: "",
			};
		},
		methods: {
			simulateApi(response, time) {
				return new Promise(() => {
					setTimeout(() => {
						this.apiResponse = response;
					}, 1000 * time);
				});
			},
			async fetchApi(value, time) {
				await this.simulateApi(value, time);
			},
			callApi(newValue, oldValue) {
				console.log("Call:", newValue, oldValue);
				if (newValue.length > 3) {
					this.fetchApi("Call", 2);
				}
			},
		},
		watch: {
			text: [
				"callApi",
				function handler2(val, old) {
					console.log("Hanlder2: ", val, old);

					this.fetchApi("Hanlder 2", 3);
				},
				{
					handler: function handler3(val, old) {
						console.log("Hanlder3: ", val, old);
						this.fetchApi("Hanlder 3", 5);
					},
				},
			],
		},
	};
</script>

<style>
	#app {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		height: 100vh;
	}
</style>
