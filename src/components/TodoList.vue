<template>
  <div>
    <p class="tasks">Количество Выполненных заданий: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p class="tasks">Количество заданий в ожидание: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" :todo.sync="todo"></todo>
  </div>
</template>

<script type = "text/javascript" >
import Swal from 'sweetalert2';
import Todo from './Todo';
export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo) {
      Swal.fire({
              title: 'Вы точно уверены?',
              text: "После удаления восстановление станет невозможным!",
              type: 'warning',
              showCancelButton: true,
              confirmButtonColor: '#3085d6',
              cancelButtonColor: '#d33',
              confirmButtonText: 'Yes, delete it!'
            }).then((result) => {
              if (result.value) {
                const todoIndex = this.todos.indexOf(todo);
                this.todos.splice(todoIndex, 1);
                Swal.fire(
                  'Deleted!!!!',
                  'Your file has been deleted.',
                  'success'
                )
              }
            }) 
},
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
      Swal.fire('Success!', 'To-Do completed!', 'success');
    },
  },
};
</script>

<style scoped>
p.tasks {
  text-align: center;
}
</style>