<template>
    <div class="wrapper">
    <aHeader
      @show-form="showForm"
      :swapAddButton="toggleAddTask"
    />
    <div v-if="toggleAddTask">
      <addTask  
        @add-task="addTask"
      />
    </div>
    <aTasks
      @task-done="taskDone"
      @toggle-reminder="toggleReminder" 
      @delete-task="deleteTask" 
      :atasks="atasks"
    />
    </div>
</template>


<script>
import aHeader from './components/Header'
import aTasks from './components/Tasks'
import addTask from './components/Form'


export default {
  name: 'App',
  components: {
    aHeader, aTasks, addTask
  },
  data(){
    return{
      atasks:[],
      toggleAddTask: false,
    }
  },
  methods:{
      showForm(){
        this.toggleAddTask = !this.toggleAddTask
      },
      addTask(atask){
        this.atasks = [...this.atasks, atask]
      },
      deleteTask(id){
          if(confirm('Are you Sure?')){
              this.atasks=this.atasks.filter((atask)=>atask.id!==id)
          }
      },
      toggleReminder(id){
          this.atasks=this.atasks.map((atask)=> atask.id === id ? {...atask, reminder : !atask.reminder}: atask)
      },
      taskDone(id){
          this.atasks=this.atasks.map((atask)=> atask.id === id ? {...atask, situation : !atask.situation}: atask)
      },
  },
  created(){
      this.atasks = [
        {
          id:0,
          text:'Ballet Presentation at Daughters school',
          day:'March 10th at 2:00pm',
          reminder: true,
          situation:false,
        },
        {
          id:1,
          text:'Vet Appointment for Doug',
          day:'March 15th at 9:00am',
          reminder: true,
          situation:false,
        },
        {
          id:2,
          text:'Doctors Appointment',
          day:'March 13th at 3:00pm',
          reminder: false,
          situation:false,
        },
      ]

  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.wrapper {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  padding: 30px;
  box-sizing: border-box;
  background: #F5F3F3;
  border: 1px solid #CCCCCC;
  box-shadow: 20px 10px 20px rgba(0, 0, 0, 0.24);
  border-radius: 10px;
}
.btn {
  display: inline-block;
  background: linear-gradient(#005DCB,#4100CB);
  color: #fff;
  border: none;
  padding: 10px 20px;
  border-radius: 8px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
  font-weight:bold;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}

</style>
