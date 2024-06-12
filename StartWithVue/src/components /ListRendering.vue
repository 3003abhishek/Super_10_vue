<script>
import {ref} from 'vue' ; 

let id = 0 ; 
const todos = ref([
    {
        id: id++,
        text : "Learn Vue"
    } , 
     {
        id: id++,
        text : "Learn React"
    } , 
     {
        id: id++,
        text : "Learn React Native"
    } , 
])

</script>


<template>

<div v-for = "todo in todos ">
<p>{{todo.text}}</p>
</div>
</template>