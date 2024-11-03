<script>
    let todos = [];
    let newTodo = '';

    function addTodo() {
        if (newTodo.trim() !== '') {
            const id = Date.now();
            const randomTime = Math.floor(Math.random() * 5 + 1) * 60; // Random time between 1 and 10 minutes in seconds
            todos = [...todos, { id, text: newTodo, completed: false, timeLeft: randomTime }];
            newTodo = '';

            // Start the countdown timer for each task
            const interval = setInterval(() => {
                const todo = todos.find(t => t.id === id);
                if (todo) {
                    todo.timeLeft -= 1;
                    todos = [...todos]; // Trigger reactivity
                    if (todo.timeLeft <= 0) {
                        removeTodoById(id);
                        clearInterval(interval); // Stop the timer when time runs out
                    }
                }
            }, 1000); // Update every second
        }
    }

    function removeTodoById(id) {
        todos = todos.filter(todo => todo.id !== id);
    }

    function toggleTodoCompletion(id) {
        todos = todos.map(todo => todo.id === id ? { ...todo, completed: !todo.completed } : todo);
    }
</script>

<style>
    .todo-list {
        max-width: 400px;
        width: 100%;
        margin: auto;
        padding: 20px;
        background: #fff;
        border-radius: 8px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        border: 1px solid #ddd;
    }
    .todo-item {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 8px 0;
        border-bottom: 1px solid #eee;
    }
    .todo-item.completed {
        text-decoration: line-through;
        color: #aaa;
    }
    .todo-input {
        width: 100%;
        padding: 8px;
        margin-bottom: 12px;
        font-size: 16px;
    }
    .todo-button {
        padding: 8px;
        cursor: pointer;
    }
    .countdown {
        color: red;
        font-weight: bold;
        margin-right: 8px;
    }
</style>

<div class="todo-list">
    <h2>  Totally Usefull To-Do List</h2>

    <input
        type="text"
        bind:value={newTodo}
        class="todo-input"
        placeholder="Add a new task..."
        on:keydown={(e) => e.key === 'Enter' && addTodo()}
    />

    <button on:click={addTodo} class="todo-button">Add</button>

    {#each todos as { id, text, completed, timeLeft }}
        <div class="todo-item {completed ? 'completed' : ''}">

            <span class="countdown">
                {Math.floor(timeLeft / 60)}:{String(timeLeft % 60).padStart(2, '0')}
            </span>
            <span on:click={() => toggleTodoCompletion(id)}>{text}</span>
            <button on:click={() => removeTodoById(id)}>Remove</button>
        </div>
    {/each}
</div>


