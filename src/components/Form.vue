<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="text" name="text" placeholder="Enter a task..." />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
        type="text"
        v-model="day"
        name="day"
        placeholder="Enter day and time..."
      />
    </div>
    <div class="form-control form-control-check">
      <label>Reminde Me</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>
    <div class="saveTask">
        <button>
            <svg viewBox="0 0 56 20" fill="none" xmlns="http://www.w3.org/2000/svg">
            <line x1="40.75" y1="10.25" x2="33.25" y2="10.25" stroke="#005DCB" stroke-width="2.5" stroke-linecap="round"/>
            <path d="M4.99 12.76H2.37L1.95 14H0.16L2.7 6.98H4.68L7.22 14H5.41L4.99 12.76ZM4.55 11.44L3.68 8.87L2.82 11.44H4.55ZM7.65305 11.2C7.65305 10.6267 7.75971 10.1233 7.97305 9.69C8.19305 9.25667 8.48971 8.92333 8.86305 8.69C9.23638 8.45667 9.65305 8.34 10.113 8.34C10.4797 8.34 10.813 8.41667 11.113 8.57C11.4197 8.72333 11.6597 8.93 11.833 9.19V6.6H13.543V14H11.833V13.2C11.673 13.4667 11.443 13.68 11.143 13.84C10.8497 14 10.5064 14.08 10.113 14.08C9.65305 14.08 9.23638 13.9633 8.86305 13.73C8.48971 13.49 8.19305 13.1533 7.97305 12.72C7.75971 12.28 7.65305 11.7733 7.65305 11.2ZM11.833 11.21C11.833 10.7833 11.713 10.4467 11.473 10.2C11.2397 9.95333 10.953 9.83 10.613 9.83C10.273 9.83 9.98305 9.95333 9.74305 10.2C9.50971 10.44 9.39305 10.7733 9.39305 11.2C9.39305 11.6267 9.50971 11.9667 9.74305 12.22C9.98305 12.4667 10.273 12.59 10.613 12.59C10.953 12.59 11.2397 12.4667 11.473 12.22C11.713 11.9733 11.833 11.6367 11.833 11.21ZM14.4402 11.2C14.4402 10.6267 14.5468 10.1233 14.7602 9.69C14.9802 9.25667 15.2768 8.92333 15.6502 8.69C16.0235 8.45667 16.4402 8.34 16.9002 8.34C17.2668 8.34 17.6002 8.41667 17.9002 8.57C18.2068 8.72333 18.4468 8.93 18.6202 9.19V6.6H20.3302V14H18.6202V13.2C18.4602 13.4667 18.2302 13.68 17.9302 13.84C17.6368 14 17.2935 14.08 16.9002 14.08C16.4402 14.08 16.0235 13.9633 15.6502 13.73C15.2768 13.49 14.9802 13.1533 14.7602 12.72C14.5468 12.28 14.4402 11.7733 14.4402 11.2ZM18.6202 11.21C18.6202 10.7833 18.5002 10.4467 18.2602 10.2C18.0268 9.95333 17.7402 9.83 17.4002 9.83C17.0602 9.83 16.7702 9.95333 16.5302 10.2C16.2968 10.44 16.1802 10.7733 16.1802 11.2C16.1802 11.6267 16.2968 11.9667 16.5302 12.22C16.7702 12.4667 17.0602 12.59 17.4002 12.59C17.7402 12.59 18.0268 12.4667 18.2602 12.22C18.5002 11.9733 18.6202 11.6367 18.6202 11.21Z" fill="#005DCB"/>
            <path d="M47 9.68C47 14.3575 42.6468 18.36 37 18.36C31.3532 18.36 27 14.3575 27 9.68C27 5.00245 31.3532 1 37 1C42.6468 1 47 5.00245 47 9.68Z" stroke="#005DCB" stroke-width="2"/>
            <line x1="37.25" y1="6.25" x2="37.25" y2="13.75" stroke="#005DCB" stroke-width="2.5" stroke-linecap="round"/>
            </svg>
        </button>
    </div>
  </form>
</template>


<script>

export default{
    name:"addTask",
    data(){
        return{
            text:'',
            day:'',
            reminder: false,
        }
    },
    methods:{
        onSubmit(e){
            e.preventDefault()

            if (!this.text) {
        alert('Please add a task')
        return
      }
      const newTask = {
        id: Math.floor(Math.random() * 100000),
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      }
      this.$emit('add-task', newTask)
      this.text = ''
      this.day = ''
      this.reminder = false
    },
  },
    
}
</script>

<style scoped>
.add-form {
  margin-bottom: 4em;
}
.form-control {
  margin: 10px 0;
}
.form-control label {
  display: block;
}
.form-control input {
    border-color:rgba(0, 0, 255, 0.5);
    border-radius:8px;
    width: 100%;
    height: 40px;
    padding: 3px 7px;
    font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
    position:absolute;
    left:-5em;
    flex: 2;
    height: 20px;

}
.saveTask{
    position:relative;
    display: flex;
    align-items: right;
    justify-content: space-between;
    
}
.saveTask svg{
    position:absolute;
    width:6em;
    right:0;
    cursor:pointer;
}
.savetask button{
    border:none;
    background-color:transparent;
}

</style>