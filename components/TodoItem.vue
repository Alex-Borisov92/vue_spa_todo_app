<template>
  <div class="todo-item">
    <input type="checkbox" v-model="todo.completed" />
    <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
    <button @click="deleteTodo">Delete</button>
  </div>
</template>

<script>
export default {
  props: ['todo'],
  methods: {
    deleteTodo() {
      this.$emit('delete-todo', this.todo.id);
    },
  },
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
.todo-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
