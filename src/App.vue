<template>
  <div id="app">
    <div class="container">
      <div class="col-md-6 offset-md-2">
        <h1 class="text-center mb-4">Vue.js To-Do App</h1>
        <input type="text"
          class="form-control mb-4"
          v-model="userInput"
          @keyup.enter="addNewTodo()">
          <div class="list-group mb-4">
            <todo v-for="todo in activeTodoList()" :label="todo.label" @componentClick="toggleTodoState(todo)"/>
          </div>
          <div class="text-right">
            <button type="button" class="btn btn-sm" @click="changeCurrentState('active')">To do</button>
            <button type="button" class="btn btn-sm" @click="changeCurrentState('done')">Completed</button>
            <button type="button" class="btn btn-sm" @click="changeCurrentState('all')">Show all</button>
          </div>
      </div>
    </div>
  </div>
</template>


<script>
import Todo from './components/Todo';

export default {
  name: 'app',
  data() {
    return {
      userInput: '',
      todoList: [],
      currentState: 'active'
    };
  },
  methods: {
    activeTodoList() {
      return this.todoList.filter(todo => this.currentState === 'all' || todo.state === this.currentState);
    },
    addNewTodo() {
      if (this.userInput == '') {
        return;
      } else {
        this.todoList.push({
          label: this.userInput,
          state: 'active'
        });
        this.userInput = '';
        return;
      }
    },
    changeCurrentState(state) {
      this.currentState = state;
    },
    toggleTodoState(todo) {
      todo.state = (todo.state === 'active' ? 'done': 'active');
      return;
    }
  },
  components: {
    Todo
  }
}
</script>


<style>
#app {
  text-align: center;
  margin-top: 60px;
}
</style>
