<script>
import Header from './components/Header.svelte';
import TodoItem from './components/TodoItem.svelte';

let todos = [
	{ text: 'Köp äpplen', done: false },
	{ text: 'Köp bananer', done: false }
];

let newTodo = '';

function addTodo(){
	todos = [...todos, { text: newTodo, done: false }];
	newTodo = '';
}

function updateTodo(e){
	todos.splice(e.detail.index, 1);
	todos = [...todos];
}

</script>

<main class="app">
	<Header todos={todos} />
	<section>
		<input type="text" bind:value={newTodo}>
		<button on:click={addTodo}>Add todo!</button>
	</section>
	<ul class="todos">
		{#each todos as todo, index}
		<TodoItem todo={todo} index={index} on:updateTodo={updateTodo} />
		{/each}
	</ul>
</main>

<style>

</style>