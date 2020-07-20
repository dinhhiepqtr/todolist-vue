<template>
  <div
    class="demo-infinite-container"
    :infinite-scroll-distance="10">

    <h3>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</h3>
    <h3>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</h3>
    <br/>
    <todo v-on:del-todo="del" slot="renderItem" v-for="todo in todos" v-bind:key="todo.id" v-bind:index="todos" :todo.sync="todo"></todo>

  </div>
</template>

<script>
import Todo from './Todo'
export default {
  props: ['todos'],
  components: {Todo},
  methods: {
    del (todo) {
      const indexOfTask = this.todos.indexOf(todo)
      this.todos.splice(indexOfTask, 1)
    }
  }
}
</script>

<style>

</style>
