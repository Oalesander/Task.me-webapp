<template>
    <button 
    @click="onClick()" class="btn" :style="{background: color}">{{text}}</button>
</template>


<script>




    export default{
        name: "addButton",
        props:{
            text: String,
            color: String,
        },
        methods:{
            onClick(){
                this.$emit('show-form')
            }
        }
    }
</script>
