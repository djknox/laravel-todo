<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">My Todo List</div>

                    <div class="card-body">
                        <todo-item
                            v-for="todo in todos"
                            v-bind:todo="todo"
                            v-on:delete-todo="deleteTodo"
                            v-on:complete-todo="completeTodo"></todo-item>
                        <create-todo v-on:add-todo="addTodo"></create-todo>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        mounted() {
            console.log('Component mounted.')
        },
        data() {
            return {
                todos: [],
            }
        },
        methods: {
            addTodo(todo) {
                this.todos.push(todo);
            },
            deleteTodo(todo) {
                const todoIndex = this.todos.indexOf(todo);
                this.todos.splice(todoIndex, 1);
            },
            completeTodo(todo) {
                const todoIndex = this.todos.indexOf(todo);
                this.todos[todoIndex].done = true;
            }
        },
    }
</script>
