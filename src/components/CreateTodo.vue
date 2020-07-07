<template>
    <div>
      <a-button type="default" v-on:click="openForm" v-show="!isCreating"> Creat </a-button>
      <div class="create" v-show="isCreating">
        <h3>Create task</h3>
        <a-form :form="form" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }" @submit="sendForm">
          <div>
            <a-form-item label="Title">
              <a-input v-model="titleText" placeholder="Input title"></a-input>
            </a-form-item>
          </div>
          <div>
            <a-form-item label="Content">
              <a-input v-model="contentText" placeholder="Input content"></a-input>
            </a-form-item>
          </div>
          <a-button type="danger" v-on:click="closeForm">Cancel</a-button>
          <a-button type="primary" v-on:click="sendForm">Create</a-button>
        </a-form>
      </div>
    </div>
</template>

<script>
export default {
  data () {
    return {
      titleText: '',
      contentText: '',
      isCreating: false
    }
  },
  methods: {
    openForm () {
      this.isCreating = true
    },
    closeForm () {
      this.isCreating = false
    },
    sendForm () {
      if (this.titleText.length > 0 && this.contentText.length > 0) {
        const title = this.titleText
        const content = this.contentText
        this.$emit('create-todo', {
          title,
          content,
          done: false
        })
        this.titleText = ''
        this.contentText = ''
        this.isCreating = false
      }
    }
  }
}
</script>

<style>
  .create{
    width: 40% ;
    padding-bottom: 5%;
  }
</style>
