<template>
  <div class="container">
    <div v-show="!isEditing">
      <div class='header'>
          {{ todo.title }}
      </div>
      <div class='content'>
          {{ todo.project }}
      </div>
      <div class='flex-container'>
          <span class='editIcon flex-item ' v-on:click="showForm">
      
            <font-awesome-icon icon="user-edit" />
    
        </span>
        <span class='trashIcon flex-item' v-on:click="deleteTodo(todo)">
            <font-awesome-icon icon="trash-alt" />
        </span>
      </div>
    </div>
    <div class="EditContainer" v-show="isEditing">
 
      
          <label for="fname">Название</label>
          <input type="text" id="fname" placeholder="Название.." v-model="todo.title">
          
 
          <label for="fname">Описание</label>
          <input type="text" id="fname" placeholder="Название.." v-model="todo.project">
 
            <button class="btn" v-on:click="hideForm" value="Закрыть">Изменить</button>
    
    </div>
 
    <button type="button" style = "border: 5px solid MediumSeaGreen" class="btn1" v-show="!isEditing &&todo.done" disabled>Выполнено</button>
    <button type="button" style = "border: 5px solid Orange" class="btn1" v-on:click="completeTodo(todo)" v-show="!isEditing && !todo.done">Ожидает выполнения</button>
 
  </div>
</template>

<script type="text/javascript">
  export default {
    props: ['todo'],
    data() {
      return {
        isEditing: false,
      };
    },
    methods: {
      completeTodo(todo) {
        this.$emit('complete-todo', todo);
      },
      deleteTodo(todo) {
        this.$emit('delete-todo', todo);
      },
      showForm() {
        this.isEditing = true;
      },
      hideForm() {
        this.isEditing = false;
      },
    },
  };
</script>
 

<style scoped>
.container {
  border: 1px Dotted black; /* Dotted border */
  width: 80%; 
  border-radius: 15px; /* Rounded border */
  margin: 0 auto; /* Center the coupon */
  max-width: 600px; 
  margin-bottom: 20px;
}
 .header{
   text-transform: uppercase;
   font-size: 30px;
   text-align: center;
   text-decoration: underline;
   margin: 3px;
 }

 .content{
     font-size: 25px;
     text-align: justify;
    font-style: italic;
    padding: 2px;

 }
 .editIcon{
  margin: 2px;
  color: green;
  cursor: pointer;
 }
 .trashIcon{
  margin: 2px;
  color: tomato;
  cursor: pointer;
 }

.flex-container {
  display: flex;
  flex-direction: row-reverse;
}

.btn1 {
  display: block;
  width: 100%;
  background-color: white;
  padding: 14px 28px;
  font-size: 16px;
  cursor: pointer;
  text-align: center;
  border-radius: 15px;
  margin-top: 2px;
  background-color: lightgray;
}




input[type=text] {
  width: 100%; /* Full width */
  padding: 12px; /* Some padding */  
  border: 1px solid #ccc; /* Gray border */
  border-radius: 4px; /* Rounded borders */
  box-sizing: border-box; /* Make sure that padding and width stays in place */
  margin-top: 6px; /* Add a top margin */
  margin-bottom: 16px; /* Bottom margin */
  resize: vertical /* Allow the user to vertically resize the textarea (not horizontally) */
}

/*input[type=submit] {
  background-color: #4CAF50;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}*/

.EditContainer {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}

  .btn{
    border: none; /* Remove borders */
  color: white; /* Add a text color */
  padding: 14px 28px; /* Add some padding */
  cursor: pointer;  
  background-color: #2196F3;
  }
</style>