<script setup>
import TodoForm from './TodoForm.vue';
import TodoStatus from './TodoStatus.vue';
import Todos from './Todos.vue';
</script>

<template>
  <div class="todo-list w-[900px] flex flex-col gap-5">
    <p class="text-2xl text-center sm:text-left font-bold">TODO APP</p>
    <TodoStatus />
    <TodoForm />
    <Todos />
  </div>
</template>

<script>
  
</script>