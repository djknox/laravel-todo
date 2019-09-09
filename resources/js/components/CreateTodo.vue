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
            <input v-model="descriptionText" type='text' ref='description' defaultValue="" placeholder="Description">
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
      descriptionText: '',
      isCreating: false,
    };
  },
  methods: {
    openForm() {
      this.titleText = '';
      this.descriptionText = '';
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (this.titleText.length > 0 && this.descriptionText.length > 0) {
        const title = this.titleText;
        const description = this.descriptionText;
        this.$emit('add-todo', {
          title,
          description,
          done: false,
        });
        this.newTodoText = '';
      }
      this.isCreating = false;
    },
  },
};
</script>