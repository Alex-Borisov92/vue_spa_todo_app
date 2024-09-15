<template>
  <div id="app">
    <h1>Todo List</h1>
    <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new task" />
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        <TodoItem :todo="todo" @delete-todo="deleteTodo" />
      </li>
    </ul>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue';

export default {
  components: {
    TodoItem,
  },
  data() {
    return {
      newTodo: '',
      todos: [
        { id: 1, text: 'Learn Vue.js', completed: false },
        { id: 2, text: 'Create a Todo App', completed: false },
      ],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push({
          id: Date.now(),
          text: this.newTodo,
          completed: false,
        });
        this.newTodo = '';
      }
    },
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 50px;
}

input {
  margin-bottom: 20px;
  padding: 10px;
  font-size: 16px;
}
</style>
