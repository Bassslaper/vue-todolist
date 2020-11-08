<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model.trim="title" placeholder="Добавить новую задачу">
    <button type="submit">Добавить</button>
  </form>
</template>

<script>


  export default {
    data() {
      return {
        title: ''
      }
    },
    methods: {
      onSubmit() {
        if(this.title.trim()) {
          const newTodo = {
            id: Math.floor(Date.now() / (Math.random() * (Math.random() + Math.random()) * 1000000000) ), 
            title: this.title,
            completed: false
          }
          this.$emit('add-todo', newTodo);
          this.title = '';
        }

      }
    }
  }

</script>



<style scoped>

  form {
    display: flex;
    margin-bottom: 1.5rem;
  }

  input {
    width: 60%;
    margin-right: 1rem;
    border-radius: 1rem;
    border: 3px solid #f6f6;
    outline: none;
    font-size: 1.6rem;
    padding: 0.5rem 1rem;
  }

  input:focus {
    border-color: #007bff;
  }

  button {
    border-radius: 1rem;
    border: none;
    outline: none;
    background-color: #007bff;
    color: #fff;
    font-weight: bold;
    font-size: 1rem;
    padding: 0.75rem 1.5rem;
    letter-spacing: 1.5px;
    cursor: pointer;
  }

  button:hover {
    background-color: #008fff;
  }

  @media (max-width: 992px) { 
    input {
      font-size: 0.8rem;
    }
    
  }


</style>