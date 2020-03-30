<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo" />
    <!-- get emit del-todo and execute delete todo method -->
    <Todos v-bind:todoslist="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';
import axios from 'axios';

export default {
  name: 'home',
  components: {
    Todos,
    AddTodo
  },
  methods: {
    deleteTodo(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}
      `)
        // eslint-disable-next-line no-unused-vars
        .then(res => this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(err => console.log(err))
    },
    addTodo(newTodo) {
      const {title, completed} = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err))
    }
  },
  data () {
    return {
      todos: []
    }
  },
  // first thing to display on the screen
  created() {
    // grab json and assign to todos
    // returns a promise
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
  }
}
</script>

<style>
    * {
      box-sizing: border-box;
      margin:0;
      padding: 0;
    }

    body{
      font-family: Arial, Helvetica, sans-serif;
      line-height: 1.4;
    }

    /* .btn{
      display: inline-block;
      border: none;
      background: #555;
      color: #fff;
      padding: 7px 20px;
      cursor: pointer;
    } */

    /* .btn:hover {
      background: #666;

    } */

</style>
