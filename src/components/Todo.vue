<template>
    <div class="m-auto w-2/3 shadow p-3 mt-16">

        <h1 class="text-2xl font-bold">Todo</h1>

        <li v-for="todo in todos">
            <span :key="todo.id">
               {{ todo.description }}
            </span>

            <span @click="deleteTodo(todo.id)" class="mx-2 cursor-pointer">x</span>
        </li>

        <label>
            <input v-on:keyup.enter="addTodo"  v-model="newTodo"
                   placeholder="New todo..."
                   class="shadow my-2 appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            />
        </label>

        <p>Todo completed ({{isCompleted}})</p>
    </div>
</template>

<script>
    import { v4 as uuidv4 } from 'uuid';
    export default {
        name: 'Todo',
        data() {
            return {
                newTodo:'',
                todos: [
                    {
                        id:1,
                        description:'Finish Vue3 todo',
                        completed:false
                    },
                    {
                        id:2,
                        description:'Make food',
                        completed:false
                    },
                    {
                        id:3,
                        description:'Take a nap',
                        completed:true
                    }
                ]
            }
        },

        computed: {
            isCompleted() {
                return this.todos.filter(todo => todo.completed).length
            }
        },
        methods: {
            deleteTodo(id) {
                this.todos = this.todos.filter(todo => todo.id !== id);
            },

            addTodo(e) {
                e.preventDefault();

                const newTodoObj = {
                    id: uuidv4(),
                    description: this.newTodo,
                    completed: true
                }

                this.todos = [...this.todos, newTodoObj];

                this.newTodo = '';
            }
        }


    }
</script>

