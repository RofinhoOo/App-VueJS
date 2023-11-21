<template>
  <div>
    <div v-bind:key="todo.id" v-for="todo in todoslist">
      <TodoItem v-bind:todo="todo" v-on:delete-todo="handleDeleteTodo" />
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
  name: 'TodosComponent',
  props: ['todoslist'],
  components: {
    TodoItem
  },
  methods: {
    handleDeleteTodo(todoId) {
      // Puedes realizar cualquier lógica adicional aquí si es necesario

      // Luego, emite el evento delete-todo hacia el componente padre
      this.$emit('delete-todo', todoId);
    }
  }
};
</script>

<style>

</style>