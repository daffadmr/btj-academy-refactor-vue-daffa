<script setup>
import Done from './Done.vue'
import Todo from './Todo.vue';
</script>
<template>
  <div class="todos flex flex-wrap justify-between gap-7 lg:gap-3 w-full">
    <div class="todo-not-completed w-full lg:w-[49%]">
      <h3 class="font-bold text-xl pb-3">TODO</h3>
      <div class="text-center font-bold py-20" v-if="emptyTodo">
        Todo is empty
      </div>
      <Todo />
    </div>
    <div class="todo-completed w-full lg:w-[49%]">
      <h3 class="font-bold text-xl pb-3">COMPLETED</h3>
      <div class="text-center font-bold py-20" v-if="emptyCompletedTodo">
        Completed Todo is empty
      </div>
      <Done />
    </div>
  </div>
</template>

<script>
export default {
  inject: ['emptyTodo', 'emptyCompletedTodo'],
}
</script>