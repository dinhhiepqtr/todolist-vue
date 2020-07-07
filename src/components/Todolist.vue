<template>
  <div>
    <h3>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</h3>
    <h3>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</h3>
    <br/>
    <div>
      <a-list :grid="{ gutter: 96, column: 4 }" :data-source="todos">
        <a-list-item slot="renderItem" slot-scope="item, todos" v-bind:index="todos">
            <a-card :title="item.title" >
              <p :class="{done : item.done}">{{item.content}}</p>
              <br/>
            </a-card>
            <br>
            <a-checkbox @change="onChange" v-model="item.done"> Done </a-checkbox>
            <a-button type="danger" v-on:click="deleteTask">Delete</a-button>
        </a-list-item>
      </a-list>
    </div>
  </div>
</template>

<script>
export default {
  props: ['todos'],
  methods: {
    deleteTask (todo) {
      const indexOfTask = this.todos.indexOf(todo)
      this.todos.splice(indexOfTask, 1)
    }
  }
}
</script>

<style scoped>
  .done{
    text-decoration: line-through;
  }
</style>
