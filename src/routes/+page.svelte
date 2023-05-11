<script>
    let todos = [];
    let task = '';

    const addTodo = () => {
        let todo = {
            task: task,
            isComplete: false,
            createdAt: new Date(),
        };
        todos = [todo, ...todos];
        task = "";
    };
        
    const markTodoAsComplete = (index) => {
        todos[index].isComplete = !todos[index].isComplete;
    };

    const deleteTodo = (index) => {
        let deleteItem = todos[index]
        todos = todos.filter((item) => item !== deleteItem);
    };
        $ : console.table(todos);
    </script>

    <input type="text" placeholder="Add a task" bind:value={task} />
    <button on:click={addTodo}>Add</button>

    <ol>
        {#each todos as item, index}
            <li class:complete={item.isComplete}>
                <div class="todoitem">
                <span> 
                    {item.task}
                </span>
                </div>
                <span>
                    <button on:click={() => markTodoAsComplete(index)}>✔</button>
                    <button on:click={() => deleteTodo(index)}>❌</button>
                </span>
            </li>
        {/each}
    </ol>

    <style>
        .complete .todoitem {
            text-decoration: line-through;
        }

        .todoitem {
            display: inline-block;
        }
    </style>
