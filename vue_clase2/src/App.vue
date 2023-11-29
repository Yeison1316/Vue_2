<script setup>
import TaskComponent from '@/components/TaskComponent.vue'
import { ref } from 'vue';

const tareas = ref(['Estudiar', 'Sacar 5', 'Descansar'])

function borrarTarea(index){
  tareas.value.splice(index,1)
}
</script>

<template>

 <div class=" bg-slate-50 shadow-md rounded mx-auto mt-12 p-3 w-96">
  <h1 class="text-2xl font-semibold">Tareas</h1>
  <div class=" flex mt-2">
    <input type="text" class=" w-4/5 h-8 px-2 py-1 border rounded border-green-600 rounded-r-none">
    <span class=" w-1/5 h-8 text-xl rounded rounded-l-none bg-green-500 text-center text-white hover:bg-green-700 hover:cursor-pointer">+</span>
  </div>
  <TaskComponent
  v-for="(task,index) in tareas" 
  :key="index"
  :tarea="task"
  :index="index"
  @borrarTarea="borrarTarea"
  />
  
 </div>
  
</template>
