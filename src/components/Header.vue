<template>
    <header>
        <h1>Task<span class="bluedot">.</span><span class="greyme">Me</span></h1>
        <addButton 
            @show-form="$emit('show-form')"
            :text="swapAddButton?'X':'Add Task'"
            :color="swapAddButton?'rgba(255,0,0,.7)':'linear-gradient(180deg, #005DCB 0%, rgba(65, 0, 203, 0.42) 100%)' "
        />
    </header>
</template>

<script>
import addButton from './Button'



export default{
       name:'aHeader',
       props:{
               swapAddButton:Boolean,
        },

       components:{
           addButton,
           
       },
}
</script>

<style scoped>
    header{
        display:flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom:20px;
    }
    .bluedot{
        color:#005DCB;
    }
    .greyme{
        color:#777;
    }

</style>
