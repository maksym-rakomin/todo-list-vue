<template>
  <div id="app">
    <h1>Todo Vue Application</h1>
    <hr>
    <TodoList />
  </div>
</template>

<script>
import TodoList from '@/components/todolist'
export default {
  name: 'App',
  components: {
    TodoList
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
</style>
