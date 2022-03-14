<script>
const title = 'Super Awesome Todo App 2.0';

let todos = [
	{ text: 'Köp äpplen', done: false },
	{ text: 'Köp bananer', done: false }
];

let newTodo = '';

function addTodo(){
	todos = [...todos, { text: newTodo, done: false }];
	newTodo = '';
}

</script>

<main class="app">
	<header>
		<h1>{title}</h1>
		<p>Du har <b>{todos.length}</b> todos kvar att göra.</p>
	</header>
	<section>
		<input type="text" bind:value={newTodo}>
		<button on:click={addTodo}>Add todo!</button>
	</section>
	<ul class="todos">
		{#each todos as todo}
		<li class:done={todo.done}>
			<input type="checkbox" bind:checked={todo.done}>{todo.text}
		</li>
		{/each}
	</ul>
</main>

<style>

</style>