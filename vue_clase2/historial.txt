<script setup>
import { ref } from 'vue';

let newTask = ref('');

let taskList = ref([
  {
    text: 'Estudiar',
    done:false
  },
  {
    text:'Jugar play',
    done:true
  }
  ]);
  function addTask(){
    if(newTask.value.trim() === '') return
      taskList.value.push({
      text:newTask.value,
      done:false
    });
    newTask.value = '';
  }
  function setDone(index){
    taskList.value[index].done = !taskList.value[index].done
    
  }
  function deleteTask(index){
    taskList.value.splice(index,1)
  }
</script>

<template>

    <div class="card">
    <h1>Lista de cosas</h1>
    <p class="subtitle">{{ newTask }}</p>
    <div>
      <div v-for="(task, index) in taskList" :key="index" class="task" :class="{done:task.done}">{{ task.text}}<span class="button" @dblclick="deleteTask(index)" @click="setDone(index)">x</span></div>
    </div>
    <div>
      <input v-model="newTask" @keypress.enter="addTask" type="text" placeholder="Escribe tu tarea">
      <p class="help" v-show="newTask != ''">Presiona enter para confirmar</p>
    </div>
  </div>
 
  
</template>


<style scoped>
.card{
  background-color: #f7f4e8;
  max-width: 400px;
  border-radius: 8px;
  margin: 0 auto;
  padding: 18px 16px;
}
h1{
  font-family: 'Roboto', sans-serif;
  color: #0b0b0d;
  text-transform: uppercase;
  text-align: center;
  padding: 0;
  margin: 0;
  font-size: 24px;
}
input{
  border-radius: 4px;
  border: none;
  width: 97%;
  margin-top: 2px;
  padding: 3px 6px;
  outline: none;
}
.subtitle{
  margin: 0;
  text-align: center;
  opacity: 0.6;
  margin-bottom: 16px;
}
.task{
  display: flex;
  justify-content: space-between;
  background-color: #85e6c0;
  padding: 2px 8px;
  padding-right: 2px;
  border-radius: 4px;
  margin-bottom: 2px;
}
.task:hover{
  background-color: #daf3ea;
}
.button{
  display: inline-flex;
  background-color:#f7f4e8 ;
  padding: 0px 5px;
  border-radius: 2px;
  align-items: center;
}
.button:hover{
  background-color: #85e6c0;
  cursor: pointer;
}
.help{
  margin: 0;
  font-size: 10px;
  opacity: 0.4;
  padding: 0px 5px;
}
.done{
  text-decoration: line-through;
  background-color: #6bb39b;
}
</style>
