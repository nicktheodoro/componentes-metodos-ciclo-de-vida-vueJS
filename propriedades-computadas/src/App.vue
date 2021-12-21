
<template>
	<div id="app">
		<button @click="fullName = 'Alvo Dumbledore'">Click</button>
		{{ fullName }}
	</div>
</template>

<script>
	export default {
		name: "App",
		data() {
			return {
				firstName: "Hary",
				lastName: "Potter",
			};
		},
		computed: {
			fullName: {
				get() {
					return `${this.firstName} ${this.lastName}`;
				},
				set(value) {
					const [first, last] = value.split(" ");
					this.firstName = first;
					this.lastName = last;
				},
			},
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
