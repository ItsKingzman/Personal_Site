<script>
	import { deleteTodo, toggleTodoCompleted } from '$lib/todoStore';
	export let todo;
</script>

<li class="bg-white flex-items-center shadow-sm border border-gray-200 rounded-lg my-2 py-2 px-4">
	<input
		name="completed"
		type="checkbox"
        on:change={() => toggleTodoCompleted(todo.id, null)}
		checked={todo.completed}
		class="mr-2 form-checkbox h5 w-5"
	/>

	<span class={`flex-1 text-gray-800 ${todo.completed ? 'line-through' : ''}`}>{todo.text}</span>

	<button
		type="button"
		class="text-sm bg-red-500 hover:bg-red-700 text-white py-1 px-2 rounded float-right focus:outline-none focus:shadow-outline"
		on:click={() => deleteTodo(todo.id)}>Delete</button
	>
</li>
