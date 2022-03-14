<script>
import { createEventDispatcher } from 'svelte';
export let todo, index;
const dispatch = new createEventDispatcher();

function removeTodo(index){
    dispatch('updateTodo', {
        index: index
    });
}

</script>

<li class:done={todo.done}>
    <input type="checkbox" bind:checked={todo.done}>
    <span>{todo.text}</span>
    <span class="remove" on:click={() => removeTodo(index)}>Ta bort!</span>
</li>

<style>
li span.remove {
	color: red;
	font-size: .8rem;
}

li.done {
	opacity: .5;
}

li.done span {
	text-decoration: line-through;
}

</style>