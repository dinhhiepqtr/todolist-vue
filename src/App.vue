<template>
  <div id="app" align="center">
    <todo-list v-bind:todos="todos"></todo-list>
    <br/>
    <create v-on:create-todo="createTodo"></create>
  </div>
</template>

<script>
import TodoList from './components/TodoList'
import Create from './components/Create'
export default {
  name: 'App',
  components: {TodoList, Create},
  data () {
    return {
      todos: [
        {
          id: 1,
          title: 'Init data',
          content: 'Khởi tạo data',
          done: false,
          isEdit: false
        },
        {
          id: 2,
          title: 'Tạo form create',
          content: 'thêm phần add item',
          done: true,
          isEdit: false
        },
        {
          id: 3,
          title: 'đỗ đình hiệp',
          content: 'blo blo',
          done: false,
          isEdit: false
        },
        {
          id: 4,
          title: 'Bệt bụng bự',
          content: 'blo blo',
          done: true,
          isEdit: false
        }
      ],
      count: 4
    }
  },
  methods: {
    createTodo (newTodo) {
      newTodo.id = this.count + 1
      this.count += 1
      this.todos.push(newTodo)
      console.log(this.todos)
    }
  }
}
</script>

<style>

</style>
