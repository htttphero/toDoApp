<template>
  <div class="containerr">
    <button  class= "btn" v-on:click="openForm" v-show="!isCreating">
       <font-awesome-icon icon="user-plus" class="fa"/>
    </button>
    <div class='CreateContainerr' v-show="isCreating">
 
 
  
          <label for="fname">Название</label>
          <input type="text" id="fname" placeholder="Название.." v-model="titleText">
          
 
          <label for="fname">Описание</label>
          <input type="text" id="fname" placeholder="Название.."v-model="projectText">
 
        <!--     <button class="btn" v-on:click="hideForm" value="Закрыть">Изменить</button> -->


      <!--     <div class='field'>
            <label>Title</label>
            <input v-model="titleText" type='text'>
          </div>
          <div class='field'>
            <label>Project</label>
            <input v-model="projectText" type='text'>
          </div> -->
<!--           <div class='ui two button attached buttons'> -->


            <button class='btn' style="background-color:green" v-on:click="sendForm()">
              Создать
            </button>
            <button class='btn'style="background-color:red" v-on:click="closeForm">
              Cancel
            </button>



   <!--        </div> -->
     
 
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titleText: '',
      projectText: '',
      isCreating: false,
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (this.titleText.length > 0 && this.projectText.length > 0) {
        const title = this.titleText;
        const project = this.projectText;
        this.$emit('create-todo', {
          title,
          project,
          done: false,
        });
        this.titleText = '';
        this.projectText = '';
        this.isCreating = false;
      }
    },
  },
};
</script>

<style scoped>
h1 {
  text-align: center;
}

.fa {
  padding: 20px;
  font-size: 30px;
  width: 50px;
  text-align: center;
  text-decoration: none;
   border-radius: 90%; 
}

/* Add a hover effect if you want */
.fa:hover {
  opacity: 0.7;
}

 
.containerr{
  text-align: center;
    border: 1px Dotted black; /* Dotted border */
  width: 80%; 
  border-radius: 15px; /* Rounded border */
  margin: 0 auto; /* Center the coupon */
  max-width: 600px; 
  margin-bottom: 10px;
}

.CreateContainerr{
    border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}

  .btn{
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  border-radius: 50%;
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

 
</style>