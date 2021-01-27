<template>
  <div class="container">
    <div class="row">
      <div class="col-12 py-5">
        <h1>{{ listName }}</h1>
      </div>
    </div>
    <div class="row ">
      <create-todo @on-new-todo="addTodo($event)" />
    </div>
    <div class="row">
      <div class="col-12 col-sm-10 col-lg-6">
        <ul class="list-group">
          <todo
            v-for="(todo, index) in todos"
            :key="index"
            :description="todo.description"
            @on-toggle="toggleTodo(todo)"
            @on-delete="deleteTodo(todo)"
            @on-edit="editTodo(todo, $event)" 
          />
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "./Todo.vue";
import CreateTodo from "./CreateTodo.vue";

export default {
  props: {
    listName: String,
  },
  data() {
    return {
      todos: [
        { description: "Buy Groceries",},
        { description: "Take out the trash", },
        { description: "Finish doing laundry", },
      ],
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push({ description: newTodo });
    },
    deleteTodo(deletedTodo) {
      this.todos = this.todos.filter(todo => todo !== deletedTodo);
    },
    editTodo(todo, newTodoDescription) {
      todo.description = newTodoDescription;
    },
  },
  components: { Todo, CreateTodo },
};
</script>

<style >
  .row{
    margin-top: 10px;
  }
</style>
