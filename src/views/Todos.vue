<template>
   <div>
      <h2>Todo LIST</h2>
      <AddTodoComponent
          @add-todo="addTodo"
      />
      <select v-model="filter">
        <option value="all">All</option>
        <option value="completed">Completed</option>
        <option value="not-completed">Not completed</option>
      </select>
      <hr>
      <Loader v-if="loading"/>
      <TodoList
        v-else-if="filteredTodos.length"
        v-bind:todos="filteredTodos"
        @remove-todolist="revoveFromList"
      />
      <p v-else>No todos!</p>

  </div>
</template>

<script>

import TodoList from '@/components/TodoList';
import AddTodoComponent from '@/components/AddTodoComponent';
import Loader from '@/components/Loader';

export default {
  name: 'App',
  data() {
    return {
      todos: [],
      loading: true,
      filter: 'all'
    }
  },

  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(response => response.json())
      .then(json => {
        this.todos = json;
        this.loading = false;
      });
  },
  // watch: {
  //   filter(value) {
  //     console.log(value);
  //   }
  // },

  computed: {
    filteredTodos() {
      if( this.filter === 'all' ) {
        return this.todos;
      }

      if( this.filter === 'completed' ) {
        return this.todos.filter(el => el.completed);
      }
      if( this.filter === 'not-completed') {
        return this.todos.filter(el => !el.completed);
      }

    }
  },
  

  components: { TodoList, AddTodoComponent, Loader },
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