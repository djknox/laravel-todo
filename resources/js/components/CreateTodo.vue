<template>
  <div>
    <button v-on:click="openForm" v-show="!isCreating">
      + Add Item
    </button>
    <div v-show="isCreating">
      <div>
        <div>
          <div>
            <input v-model="titleText" type='text' ref='title' defaultValue="" placeholder="Title">
          </div>
          <div>
            <input v-model="projectText" type='text' ref='project' defaultValue="" placeholder="Project">
          </div>
          <div>
            <button v-on:click="sendForm()">
              Create
            </button>
            <button v-on:click="closeForm">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titleText: '',
      projectText: '',
      isCreating: false,
    };
  },
  methods: {
    openForm() {
      this.titleText = '';
      this.projectText = '';
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (this.titleText.length > 0 && this.projectText.length > 0) {
        const title = this.titleText;
        const project = this.projectText;
        this.$emit('add-todo', {
          title,
          project,
          done: false,
        });
        this.newTodoText = '';
      }
      this.isCreating = false;
    },
  },
};
</script>