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

function removeTodo(index){
	todos.splice(index, 1);
	todos = [...todos];
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
		{#each todos as todo, index}
		<li class:done={todo.done}>
			<input type="checkbox" bind:checked={todo.done}>
			<span>{todo.text}</span>
			<span class="remove" on:click={() => removeTodo(index)}>Ta bort!</span>
		</li>
		{/each}
	</ul>
</main>

<style>

ul li span.remove {
	color: red;
	font-size: .8rem;
}

ul li.done {
	opacity: .5;
}

li.done span {
	text-decoration: line-through;
}

</style>