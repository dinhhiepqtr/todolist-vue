<template>
  <div>
    <div style="margin: 35px;">
        <a-row>
        <a-col :span="2">
          <p ><a-checkbox  v-model="todo.done">Done </a-checkbox> </p>
        </a-col>

        <a-col :span="13">
          <a-row>
            <a-col :span="7">
              <h4 :class="{done : todo.done}">{{ todo.title }}</h4>
            </a-col>
            <a-col :span="17">
            <p :class="{done : todo.done}" >{{todo.content}}</p>
        </a-col>
          </a-row>
        </a-col>
        <a-col :span="8">
          <a-row>
            <a-col :span="15">
              <div class="edit" v-show="todo.isEdit">
                <a-form :label-col="{ span: 6 }" :wrapper-col="{ span: 18 }" @submit="sendForm">

                  <div>
                    <a-form-item label="Title">
                      <a-input v-model="titleText" placeholder="Input title" ></a-input>
                    </a-form-item>
                  </div>
                  <div>
                    <a-form-item label="Content">
                      <a-input v-model="contentText" placeholder="Input content"></a-input>
                    </a-form-item>
                  </div>
                  <a-button type="danger" v-on:click="closeForm">Cancel</a-button>
                  <a-button type="primary" v-on:click="(sendForm(titleText,contentText))">OK</a-button>
                </a-form>
              </div>
          </a-col>

          <a-col :span="9">
              <a-button type="primary"  v-show="!todo.isEdit" v-on:click="showForm">Edit</a-button>
              <a-button type="danger" style="margin : 1px" v-on:click="deleteTask(todo)" >Delete</a-button>
            </a-col>
        </a-row>

        </a-col>
      </a-row>
      <a-list-item-meta >
      </a-list-item-meta>

    </div>
  </div>
</template>

<script>
export default {
  props: ['todo'],
  data () {
    return {
      isEditing: false,
      titleText: this.todo.title,
      contentText: this.todo.content
    }
  },
  methods: {
    deleteTask (todo) {
      this.$emit('del-todo', todo)
    },
    showForm () {
      this.todo.isEdit = true
    },
    closeForm () {
      this.todo.isEdit = false
    },
    sendForm (titleText, contentText) {
      this.todo.title = titleText
      this.todo.content = contentText
      this.todo.isEdit = false
    }
  }
}
</script>

<style>
  .done{
    text-decoration: line-through;
  }
  .edit{
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }
</style>
