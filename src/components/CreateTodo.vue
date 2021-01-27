<template>
  <form class="col-md-6" @submit.prevent="addTodo()">
    <div class="input-group mb-3">
    <input
      v-model="newTodo"
      type="text"
      class="form-control"
      placeholder="What you want to do" />
      <div class="input-group-append">
    <button class="btn btn-primary" type="submit">Add</button>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      newTodo: ""
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.length > 0) {
        this.$emit("on-new-todo", this.newTodo);
      }
      this.newTodo = "";
    }
  }
};
</script>

<style>

</style>
