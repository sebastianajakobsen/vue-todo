<template>
    <div class="m-auto w-2/3 shadow p-3 mt-16">

        <h1 class="text-2xl font-bold">Todo</h1>

        <label>
            <input @keyup.enter="addTodo" v-model="newTodo" type="text"
                   placeholder="New todo..."
                   class="shadow my-2 appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            />
        </label>

        <div v-for="todo in todos" class="flex items-center justify-between my-3">

            <div>
                <label>
                    <input :checked="todo.completed" type="checkbox" @click="toggleCompleted(todo.id)"/>
                </label>

                <span :key="todo.id" :class="{'line-through': todo.completed }" class="mx-2 text-xl">
               {{ todo.description }}
            </span>

            </div>

            <span @click="deleteTodo(todo.id)" class="text-red-700 mr-2 text-xl  cursor-pointer">x</span>
        </div>

        <hr class="my-3"/>

        <p class="text-sm">Items left: ({{itemsLeft}})</p>
    </div>
</template>

<script>
    import {v4 as uuidv4} from 'uuid';

    export default {
        name: 'Todo',

        data() {
            return {
                newTodo: '',
                todos: [
                    {
                        id: 1,
                        description: 'Finish Vue3 todo',
                        completed: false
                    },
                    {
                        id: 2,
                        description: 'Make food',
                        completed: false
                    },
                    {
                        id: 3,
                        description: 'Take a nap',
                        completed: true
                    }
                ]
            }
        },

        computed: {
            itemsLeft() {
                return this.todos.filter(todo => !todo.completed).length
            }
        },
        methods: {
            deleteTodo(id) {
                this.todos = this.todos.filter(todo => todo.id !== id);
            },

            addTodo(e) {
                e.preventDefault();

                if (this.newTodo.trim()) {
                    const newTodoObj = {
                        id: uuidv4(),
                        description: this.newTodo,
                        completed: false
                    }
                    this.todos = [...this.todos, newTodoObj];
                    this.newTodo = '';
                }

            },

            toggleCompleted(id) {
                this.todos = this.todos.map(todo => {
                    if (todo.id === id) {
                        return {
                            ...todo,
                            completed: !todo.completed
                        }
                    }
                    return todo;
                })
            }
        }


    }
</script>

