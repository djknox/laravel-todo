<template>
  <div>
    <div v-show="!isEditing">
      <div>
          {{ todo.title }}
      </div>
      <div>
          {{ todo.description }}
      </div>
      <div>
            <span v-on:click="showForm">
                edit
            </span>
            <span v-on:click="deleteTodo(todo)">
                delete
            </span>
      </div>
    </div>
    <div v-show="isEditing">
      <div>
        <div>
          <input type='text' v-model="todo.title" placeholder="Title">
        </div>
        <div>
          <input type='text' v-model="todo.description" placeholder="Description">
        </div>
        <div>
          <button v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>
    <div v-show="!isEditing && todo.done" disabled>
        Completed
    </div>
    <div v-show="!isEditing && !todo.done" v-on:click="completeTodo(todo)">
        Pending
    </div>
  </div>
</template>

<script>
export default {
  props: ['todo'],
  data() {
    return {
      isEditing: false,
    };
  },
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
    deleteTodo(todo) {
      this.$emit('delete-todo', todo);
    },
    completeTodo(todo) {
      this.$emit('complete-todo', todo);
    }
  },
};
</script>