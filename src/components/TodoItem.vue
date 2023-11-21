<template>
  <div class="todo" v-bind:class="{ completed: todo.completed }">
    <div class="todo-body">
      <input type="checkbox" v-bind:checked="todo.completed" v-on:change="checkTodo">
      {{ todo.title }}
    </div>

    <div class="todo-actions">
      <button @click="deleteTodo">Eliminar</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ['todo'],
  methods: {
    checkTodo() {
      // Emitir un evento para notificar al padre que el todo ha cambiado
      this.$emit('update-todo', { ...this.todo, completed: !this.todo.completed });
    },
    deleteTodo() {
      // Emitir un evento para notificar al padre que se debe eliminar el todo
      this.$emit('delete-todo', this.todo.id);
    },
  },
};
</script>

<style scoped>
.todo {
  border-bottom: solid 1px #ccc;
  padding: 10px;
}

.todo:not(.completed):hover {
  background-color: #eee;
}

.completed {
  color: #ccc;
  text-decoration: line-through;
}
.completed .todo-body {
  text-decoration: line-through;
}

.todo-body,
.todo-actions {
  display: inline-block;
  vertical-align: top;
}

.todo-body {
  width: 85%;
}
.todo-actions {
  padding: 0 10px;
  width: 10%;
}

button {
  border: none;
  border-radius: 10px;
  padding: 10px;
  background: linear-gradient(to right, #4e54c8, #8f94fb);
  color: black;
}
button:hover {
  background: #da2020;
  color: white;
}
</style>