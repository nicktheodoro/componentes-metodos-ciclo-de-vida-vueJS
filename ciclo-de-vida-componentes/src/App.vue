
<template>
	<div id="app">
		<Title v-if="shouldAppear" />
		<button @click="shouldAppear = false">Destroy title</button>
		<button @click="count++">Click</button>
		{{ count }}
	</div>
</template>

<script>
	import Title from "./Title.vue";
	export default {
		name: "App",
		components: {
			Title,
		},
		data() {
			return {
				hello: "wolrd",
				count: 0,
				shouldAppear: true,
			};
		},
		beforeCreate() {
			console.log("Before Create App");
			console.log(this.hello);
		},
		created() {
			console.log("Created App");
			console.log(this.hello);
		},
		beforeMount() {
			console.log("Before Mount App");
			console.log(this.$el);
		},
		mounted() {
			console.log("Mounted App");
			console.log(this.$el);
		},
		beforeUpdate() {
			console.log("Before Update App");
			console.log(this.count);
		},
		updated() {
			console.log("Updated App");
			console.log(this.count);
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
