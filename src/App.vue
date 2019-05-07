<template>
  <div id="app">
    <div class="container">
      <div class="col-md-6 offset-md-2">
        <h1 class="text-center mb-4">Vue.js To-Do App</h1>
        <input type="text"
          class="form-control mb-4"
          v-model="userInput"
          @keyup.enter="addNewTodo()">
          <div class="list-group">
            <template>
              <button class="list-group-item text-left"
              v-for="todo in todoList">
                {{ todo }}
              </button>
            </template>
          </div>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: 'app',
  data() {
    return {
      userInput: '',
      todoList: []
    };
  },
  methods: {
    addNewTodo() {
      if (this.userInput == '') {
        return;
      } else {
        this.todoList.push(this.userInput);
        this.userInput = '';
        return;
      }
    }
  }
}
</script>


<style>
#app {
  text-align: center;
  margin-top: 60px;
}
</style>
