<template>
	<h1>Vue.js</h1>

</template>

<script>
	export default {
		name: "Title",
		data() {
			return {};
		},
		beforeDestroy() {
			console.log("Before Destroy title");
		},
		destroyed() {
			console.log("Destroyed title");
		},
	};
</script>
