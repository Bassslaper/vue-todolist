<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" v-on:change="todo.completed = !todo.completed"/>
      <strong>{{ index + 1}}</strong>
      {{ todo.title | uppercase}}

    </span>
    <button class="btn-del" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
  export default {
    props: {
      todo: {
        type: Object,
        required: true
      },
      index: Number
    },
    filters: {
      uppercase(value) {
        return value.toUpperCase();
      }
    }
    
  }
</script>

<style scoped>
  li {
    border: 1px solid #f6f6;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0.5rem 2rem;
    background:#f6f6;
    margin-bottom: 1rem;
  }

  .btn-del {
    background-color: #ee30a7;
    color: #fff;
    border-radius: 50%;
    border: none;
    outline: none;
    width: 1.2rem;
    height: 1.2rem;
  }

  strong {
   margin-right: 1rem;
  }

  input {
    margin-right: 1rem;
  }

  .done {
    text-decoration: line-through;
  }

</style>