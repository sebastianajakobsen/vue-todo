<template>
    <div class="text-2xl">
        Todo {{isCompleted}}
    </div>
</template>

<script>

    export default {
        name: 'Todo',
        data() {
            return {
                todos: [
                    {
                        id:1,
                        description:'Finish Vue todo',
                        isCompleted:false
                    },
                    {
                        id:2,
                        description:'Make food',
                        isCompleted:false
                    },
                    {
                        id:3,
                        description:'Take a nap',
                        isCompleted:true
                    }
                ]
            }
        },

        computed: {
            isCompleted() {
                return this.todos.filter(todo => todo.isCompleted).length
            }
        }

    }
</script>
