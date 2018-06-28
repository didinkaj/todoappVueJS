<template>
  <div id="app">
      <h2 style="">{{ databinding }}</h2>
      <p style="color:red;">{{ fullname() }}</p>
      <table>
          <tr>
              <td>  FirstName:</td>
              <td><input type="text" v-model="firstname"/></td>
          </tr>
          <tr>
              <td>SecondName :</td>
              <td> <input type="text" v-model="secondname"/></td>
          </tr>
      </table>


      <h2 style="">{{ apptitle }}</h2>

      <div v-on:delete-task="deleteTask" v-for="todo in todos" :key="todo.id">
          <div>{{ todo.title }} &nbsp;&nbsp;&nbsp;{{todo.Task}} &nbsp;&nbsp;&nbsp;<button v-on:click="deleteTask(todo)" >X</button></div>

    </div>
      <div><br/><button v-on:click="showForm()" style="background:blue; color:white;">Add New Task</button></div>
      <div>
          <div v-show="isEditing">
          <h2>Adding a task</h2>

              <table>
                  <tr>
                      <td>Task title:</td>
                      <td><input type="text" name="title" v-model="taskTitle" /></td>
                  </tr>
                  <tr>
                      <td>Task name:</td>
                      <td><input type="tex" name="taskname" v-model="taskName" /></td>
                  </tr>
                  <tr>
                      <td></td>
                      <td>  <button v-on:click="closeForm()" style="background:grey; color:black;">close</button>&nbsp;&nbsp;&nbsp;<input  v-on:click="sendForm()" type="submit" name="send"/>  </td>
                  </tr>
              </table>




          </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'app',
    data(){

      return{
          firstname:"",
          secondname :"",
          taskTitle:"",
          taskName:"",
          date: Date(),
          isEditing: false,

          todos:[{
              id:1,
              title:'Todo A',
              Task:'project A',
              date:'jun 30 2018',
              done:false
          },
              {
                  id:2,
                  title:'Todo B',
                  Task:'project B',
                  date:'jun 30 2018',
                  done:false
              },{
                  id:3,
                  title:'Todo C',
                  Task:'project C',
                  date:'jun 30 2018',
                  done:false
              }],

          apptitle:"Simple to do List",
          databinding:"Two way data binding"



          
      };

    },



    methods:{
        fullname (){
            return "I am "+ this.firstname +" "+ this.secondname;
        },
        showForm(){
          this.isEditing = true;
        },
        closeForm(){
            this.isEditing = false;
        },
        sendForm (){
            let id = this.todos.length +1;

            if(this.taskTitle!='' && this.taskName!='') {
                const date = new Date();
                const done = false;

                const newTodos = {id:id,title:this.taskTitle,Task:this.taskName,date:this.date,done:this.done};
                this.todos.push(newTodos);
                this.newTodos = '';
            }else{
                console.log(newTodos);
            }

        },
        deleteTask(todo){
            console.log(todo);
            this.todos.pop(todo);


        }

    },
    computed:{

    }



}
</script>

<style>

</style>
