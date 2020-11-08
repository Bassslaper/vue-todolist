<template>
  <div id="app">
      <div class="container">
          <h1><router-link to="/">Todo Application</router-link></h1>
          <hr>  
          <router-view/> 
      </div>
  </div>
</template>


<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  .container {
    max-width: 65%;
    padding: 0 15px;
    margin: 0 auto;
  }

  h1 a {
    text-decoration: none;
    color: inherit;
  }

  h1:hover a {
    color: #007bff;
  }


  hr {
    height: 0.2rem;
    border: none;
    background-color: greenyellow;
    margin-bottom: 2rem;
  }
</style>
