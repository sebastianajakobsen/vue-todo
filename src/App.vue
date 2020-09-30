<template>

  <Todo title="Todo App"/>
  <Test/>
</template>

<script>


import Todo from "./components/Todo.vue";
import Test from "./components/Test.vue";
export default {
  name: 'App',
  components: {
    Test,
    Todo
  }
}
</script>
