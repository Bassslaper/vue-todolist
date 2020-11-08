<template>
  <div id="app">
      <h1>Todo LIST</h1>
      <AddTodoComponent
        @add-todo="addTodo"
      />
      <hr>
      <TodoList
        v-bind:todos="todos"
        @remove-todolist="revoveFromList"
      /> 
  </div>
</template>

<script>

import TodoList from '@/components/TodoList';
import AddTodoComponent from '@/components/AddTodoComponent';

export default {
  name: 'App',
  data() {
    return {
      todos: [
      {id: 1, title: 'Купить хлеб', completed: false},
      {id: 2, title: 'Купить молоко', completed: false},
      {id: 3, title: 'Купить сыр', completed: false}
      ]
    }
  },
  components: { TodoList, AddTodoComponent },
  methods: {
    revoveFromList(id) {
      this.todos = this.todos.filter(el => el.id !== id);
     
    },
    addTodo(todo) {
      this.todos.push(todo);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

hr {
  height: 0.2rem;
  border: none;
  background-color: greenyellow;
  margin-bottom: 2rem;
}
</style>
