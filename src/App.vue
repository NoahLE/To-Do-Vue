<template>
  <div id="app">
    <h1 class="ui dividing centered header">To-Do Vue.js</h1>
    <div class="ui three column centered grid">
      <div class="column">
        <todo-list v-bind:todos="todos"></todo-list>
        <create-todo v-on:add-todo="addTodo"></create-todo>
      </div>
    </div>
  </div>
</template>

<script>
  import sweetalert from 'sweetalert';
  import TodoList from './components/TodoList';
  import CreateTodo from './components/CreateTodo';

  export default {
    name: 'app',
    components: {
      TodoList,
      CreateTodo,
    },
    methods: {
      createTodo(newTodo) {
        this.todos.push(newTodo);
        sweetalert('Success', 'To-Do created!', 'success');
      },
    },
    data() {
      return {
        todos: [{
          id: 1,
          title: 'Todo A',
          project: 'Project A',
          done: false,
        }, {
          id: 2,
          title: 'Todo B',
          project: 'Project B',
          done: false,
        }, {
          id: 3,
          title: 'Todo C',
          project: 'Project C',
          done: false,
        }, {
          id: 4,
          title: 'Todo D',
          project: 'Project D',
          done: false,
        }],
      };
    },
  };
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
