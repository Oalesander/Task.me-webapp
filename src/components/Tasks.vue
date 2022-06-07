<template>
     <div :key="atask.id" v-for="atask in atasks">
     <aTask
        @task-done="$emit('task-done', atask.id)" 
        @toggle-reminder="$emit('toggle-reminder', atask.id)" 
        @delete-task="$emit('delete-task', atask.id)" 
        :atask="atask"
     />
  </div>
</template>


<script>
import aTask from './Task'


export default{
    name:'aTasks',
    props:{
        atasks: Array,
    },
    components: {
        aTask
    },
    emits:['delete-task','toggle-reminder','task-done']
}

</script>