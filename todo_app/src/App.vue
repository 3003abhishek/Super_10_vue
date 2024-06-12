<script setup>
import { ref , computed } from 'vue' ;

let id = 0 ;

const todos = ref([
{
id: id++,
text : "Learn Javascipt" , 
done : false ,

} ,
{
id: id++,
text : "Learn typescript" , 
done : false ,

} ,
{
id: id++,
text : "Learn vue" ,
done : true ,

} ,

]);

const new_todo = ref("");

const hideAllDone = ref(false); 

 function handleInputChange(e) {
  new_todo.value = e.target.value; 
 }

function handleAddTodo() {
  todos.value.push({
    id: id++ , 
    text : new_todo.value , 
    done : false ,
  });
  new_todo.value = "" ; 
}


const filterTodos = computed(()=>{
  return (hideAllDone.value)? todos.value.filter((todo)=>{
    return todo.done == false;   
  }): todos.value ; 
}) ; 

</script>

<template>
<div>
<div>
<h1>Todos</h1>
<ul>
<li v-for="todo in filterTodos" :key = "todo.id">
<input type = "checkbox" v-model = "todo.done"/>
{{todo.text}}</li>
</ul>
</div>

<div>
<input :value = "new_todo" @input = "handleInputChange"/>
<button @click = "handleAddTodo">Add Todo</button>

</div>

<div>
<button @click = "hideAllDone=!hideAllDone">{{hideAllDone? "showAll" : "hideAllDone"}} </button>
</div>


</div>





</template>
