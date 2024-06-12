<script setup>

import {reactive ,ref} from "vue" ;
const counter = reactive({
count : 0 ,
}) ;
console.log(counter.count) ;


const message = ref("hello world") ;
console.log(message.value)         ;

const titleClass = ref("blueTitle");

const text = ref("");

const awesome = ref(true);


function onToggle(){
  awesome.value = !awesome.value ; 
}


function increment() {
  counter.count++;
}

function onChange(e) {
  console.log("Change hua bhai ") ; 
  console.log(e.target.value);
  text.value = e.target.value ; 
}

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

<div>
<button @click = "increment" >Click me </button>
<h1 :class = "titleClass">{{message }}</h1>
<p>Count is : {{counter.count}}</p>
<input @value = "text" @input = "onChange"/>
<p>{{text}}</p>

<button @click = "onToggle">Toggle</button>
<p v-if = "awesome">Awesome</p>
<p v-else >Oh-no</p>

<ul v-for = "todo in todos "  :key = "todo.id">
{{todo.text}}
</ul>
</div>

</template>

<style>

.redTitle{
color : red  ;
}
.blueTitle {
color : blue ;
}
</style>
