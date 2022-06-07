<template> 
    <div @dblclick="$emit('toggle-reminder', atask.id)" :class="[atask.reminder? 'reminder':'','task']">
        <div :class="[atask.situation? 'done':'']">
            <p>
                {{atask.text}}
                <svg @click="$emit('task-done',atask.id)" :class="[atask.situation? 'done-svg':'']" width="30" height="27" viewBox="0 0 19 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M18.5 8C18.5 12.0651 14.5545 15.5 9.5 15.5C4.44548 15.5 0.5 12.0651 0.5 8C0.5 3.93494 4.44548 0.5 9.5 0.5C14.5545 0.5 18.5 3.93494 18.5 8Z" stroke="#00CB39"/>
                <line x1="4.30936" y1="7.60719" x2="9.25963" y2="11.5058" stroke="#00CB39"/>
                <line x1="8.6" y1="11.7" x2="14.6" y2="3.7" stroke="#00CB39"/>
                </svg>
            </p>
            <p>
                {{atask.day}}
                    
                <svg @click="$emit('delete-task',atask.id)" width="30" height="27" viewBox="0 0 19 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M18.5 8C18.5 12.0651 14.5545 15.5 9.5 15.5C4.44548 15.5 0.5 12.0651 0.5 8C0.5 3.93494 4.44548 0.5 9.5 0.5C14.5545 0.5 18.5 3.93494 18.5 8Z" stroke="#FF0000"/>
                <line x1="5.3536" y1="11.4248" x2="13.1318" y2="3.64659" stroke="#FF0000"/>
                <line x1="5.35355" y1="3.64645" x2="13.1317" y2="11.4246" stroke="#FF0000"/>
                </svg>
            </p>
        </div>
    </div>

</template>

<script>
    export default{
        name:'aTask',
        props:{
            atask:Object,
        },    
    }

</script>



<style scoped>

.task {
    background: #FFF;
    border: 0.5px solid #CCC;
    border-radius: 8px;
    margin: 5px;
    padding: 5px 20px;
    cursor: pointer;
}
.reminder {
    border-left:10px solid #00ff11
}

.done{
    color:#CCC;
    border: none;

}
.done-svg{
    position:absolute;
    left:0;
    display:none;
}

p {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-left:.3em;
    font-size: 14px;
}
p:nth-child(1){
    font-weight: bold;
}
p:nth-child(2){
    padding-top:.3em;
}


</style>