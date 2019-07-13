<template>
  <div id="app">
    <h1 style="text-align:center">Todo приложение на Vue.js</h1>
    <div>
      <div>
        <todo-list v-bind:todos="todos"></todo-list>
        <create-todo v-on:create-todo="createTodo"></create-todo>
      </div>
    </div>
  </div>
</template>

<script>
import Swal from 'sweetalert2';
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';
export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo,
  },
  data() {
    return {
      todos: [{
        title: 'Покупки',
        project: 'Купить мясо, молоко, сыр, фрукты',
        done: true,
      }, {
        title: 'Уборка',
        project: 'Убрать залу, прихожую, сдать ковры в химчистку',
        done: false,
      }],
    };
  },
  methods: {
    createTodo(newTodo) {
      this.todos.push(newTodo);
      Swal.fire('Success!', 'To-Do created!', 'success');
    },
  },
};
</script>

<style>
body{
  background-color: lightgray;
}
</style>