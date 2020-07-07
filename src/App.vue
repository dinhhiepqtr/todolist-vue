<template>
  <div class="all" align="center"  id="app">
    <todo-list v-bind:todos="todos" ></todo-list>
    <br/>
    <br/>
    <create-todo v-on:create-todo="createTodo"></create-todo>
  </div>
</template>

<script>
import TodoList from './components/TodoList'
import CreateTodo from './components/CreateTodo'
export default {
  name: 'App',
  components: {
    TodoList,
    CreateTodo
  },
  data () {
    return {
      todos: [{
        title: 'Init data',
        content: 'Tạo ra cái data đầu tiên',
        done: true
      },
      {
        title: 'Card',
        content: 'Nhét dữ liệu vào trong các thẻ',
        done: true
      }]
    }
  },
  methods: {
    createTodo (newTodo) {
      this.todos.push(newTodo)
    }
  }
}
</script>

<style>
  .all{
    padding : 3%;
  }
</style>
