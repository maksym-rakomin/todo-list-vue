<template>
  <div>
    <h2>Todos List</h2>
    <router-link to="/">Home</router-link>
    <hr />
    <AddTodo @add-todo="addTodos" />
    <hr />
    <select v-model="filter">
        <option value="all">All</option>
        <option value="completed">Completed</option>
        <option value="not-completed">Not completed</option>
    </select>
    <hr>
    <loader v-if="loading" />
    <TodoList
        v-else-if="filteredTodo.length"
        v-bind:todos="filteredTodo"
        @remove-todo="removeTodo"
    />
    <p v-else>No todos!</p>
  </div>
</template>

<script>
import TodoList from "@/components/todolist";
import AddTodo from "@/components/addtodo";
import Loader from "@/components/loader";
export default {
  name: "App",
  data() {
    return {
      todos: [],
      loading: true,
      filter: 'all'
    };
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=10")
      .then(response => response.json())
      .then(json => {
          setTimeout(() => {
            this.todos = json.filter(j => j.completed == false);
            this.loading = false
          }, 1000)

      });
  },
  computed: {

    filteredTodo: function () {

      let statusTodos = this.todos

      if (this.filter == 'all') {
        statusTodos = this.todos
      }
      if (this.filter == 'completed') {
        statusTodos = this.todos.filter(t => t.completed)
      }
      if (this.filter == 'not-completed') {
        statusTodos = this.todos.filter(t => !t.completed)
      }

      return statusTodos
    }
  },
  components: {
    TodoList,
    AddTodo,
    Loader
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id);
    },
    addTodos(todo) {
      this.todos.push(todo);
    }
  }
};
</script>
