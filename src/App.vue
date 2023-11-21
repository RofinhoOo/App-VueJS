<template>
  <div class="container">
    <div id="header">
      <SearchComponent v-on:query-change="querySearch" />
    </div>

      <div id="main-container">
        <h2>Todos</h2>
        <TodoAdd v-on:add-todo="addTodo" />
        <TodosComponent v-bind:todoslist="copyTodos" v-on:delete-todo="deleteTodo" />
      </div>
    </div>
</template>

<script>
import SearchComponent from "./components/SearchComponent";
import TodosComponent from "./components/TodosComponent";
import TodoAdd from "./components/TodoAdd.vue";

export default {
  name: "App",
  components: {
    TodosComponent, TodoAdd, SearchComponent
  
  },
  methods: {
  deleteTodo(id) {
    this.todos = this.todos.filter(todo => todo.id != id);
    this.copyTodos = [...this.todos];
  },
  addTodo(todo) {
    this.todos.push(todo);
    this.copyTodos = [...this.todos];
  },
  querySearch(query){
    if(query.trim() === ''){
      this.copyTodos = [...this.todos];
    }else{
      const temp = this.todos.filter(todo => {return todo.title.includes(query)});
      this.copyTodos = [...temp];
    }
  }
},

  data() {
    return {
      todos: [
        {
          id: 0,
          title: "comprar la cena",
          completed: false,
        },
        {
          id: 1,
          title: "Sacar el perro a pasear",
          completed: true,
        },
        {
          id: 2,
          title: "Estudiar Vue.js",
          completed: false,
        },
        {
          id: 3,
          title: "Jugar a pádel",
          completed: true,
        }
      ],
      copyTodos: [],
    };
  },
  created() {
    this.copyTodos = [...this.todos];
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1.5em;
  padding: 0;
  margin: 0;
   
}


#main-container {
  border: solid 1px black;
  width: 600px;
  margin: 80px auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  border-radius: 20px;
  
  
}

#header {
  background: linear-gradient(to right, #4e54c8, #8f94fb);
  padding: 30px;
  width: 45%;
  text-align: center;
  color: white; /* Color del texto para asegurar la legibilidad */
  border-radius: 20px;
  margin-top: 20px;
  margin-left: auto;
  margin-right: auto;
}

h2 {
  padding: 0 10px;
}
</style>


