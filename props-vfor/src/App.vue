
<template>
	<div id="app">
		<Title
			titulo="Vuejs"
			style="background: red"
			atr1="atributo 1"
			:tipo="2"
		/>
		<Title
			class="red"
			titulo="Vuejs"
		/>
		<ul>
			<li
				v-for="(item, index) in todosArray"
				:key="index"
			>
				{{ item }} - {{ index }}
			</li>
		</ul>
		<ul>
			<li
				v-for="(valor, chave, index) in todosObj"
				:key="index"
			>
				{{ chave }} : {{ valor }} - {{ index }}
			</li>
		</ul>
		<ul>
			<li
				v-for="(char, index) in strings"
				:key="index"
			>
				{{ char }} - {{ index }}
			</li>
		</ul>
		<ul>
			<li
				v-for="number in 5"
				:key="number"
			>
				{{ number }}
			</li>
		</ul>
		<ul>
			<li
				v-for="(todo, index) in filteredTodos"
				:key="index"
			>
				{{ todo }}
			</li>
		</ul>
		<ul>
			<template v-if="todos.lenght > 0">
				<li
					v-for="(todo, index) in filteredTodos"
					:key="index"
				>
					{{ todo }}
				</li>
			</template>
			<li v-else>No item</li>
		</ul>
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
				testando: 1,
				strings: "Hello world Vue.js",
				todosArray: ["Item 1", "Item 2", "Item 3", "Item 4"],
				todosObj: {
					item1: "Item 1",
					item2: "Item 2",
					item3: "Item 3",
					item4: "Item 4",
				},
				todosArrayObj: [
					{ label: "Todo1", isCompleted: true },
					{ label: "Todo2", isCompleted: true },
					{ label: "Todo3", isCompleted: false },
					{ label: "Todo4", isCompleted: false },
				],
				todos: [],
			};
		},
		computed: {
			filteredTodos() {
				return this.todosArrayObj.filter((t) => !t.isCompleted);
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
