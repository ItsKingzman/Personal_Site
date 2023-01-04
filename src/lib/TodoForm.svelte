<script>
	import { addTodo, loadTodos } from '$lib/todoStore';
	import { onMount } from 'svelte';

	onMount(() => {
		loadTodos();
	});
	let todo = '';
	const handleSubmit = () => {
		addTodo(todo);
		todo = '';
		console.log('Submitting');
		loadTodos();
	};
</script>

<form class="my-6" on:submit|preventDefault={handleSubmit}>
	<div class="flex flex-col text-sm text-center mb-2">
		<label class="font-bold mb-2 text-gray-800" for="todo">ToDo</label>
		<input
			type="text"
			bind:value={todo}
			name="todo"
			placeholder="What do you have to do?"
			class="appearance-none text-center shadow-sm border
        border-gray-200 p-2 focus:outline-none focus:border-gray-500 rounded-lg"
		/>
	</div>
	<button
		type="submit"
		class="w-full shadow-sm rounded bg-blue-400 hover:bg-blue-600 text-white py-2 px-4"
		>Submit</button
	>
</form>
