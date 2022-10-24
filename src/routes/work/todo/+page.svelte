<script>
    import TodoForm from "$lib/TodoForm.svelte"
    import Todo from "$lib/Todo.svelte"
    import {todos} from "$lib/todoStore";
</script>

<main class="container mx-auto my-6 max-w-lg">
    <h1 class="text-2xl font-bold text-center text-gray-800 md:text-3xl">My ToDos</h1>
    <TodoForm/>
    {#each $todos as todo}
        <Todo todo={todo} index={todo.id}/>
    {/each}
</main>