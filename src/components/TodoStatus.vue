<template>
  <ul class="todo-status hidden sm:flex flex-wrap justify-evenly sm:justify-between items-center gap-5">
    <li class="min-w-[100px] md:min-w-[120px] lg:min-w-[160px] text-xs border-2 rounded-md flex flex-col items-center p-3"
      v-for="(status, index) in todoStatus" :key="index">
      {{ status.name }}
      <span class="text-3xl font-bold">{{ status.value }}</span>
    </li>
  </ul>
</template>

<script>
export default {
  inject: ['todoStatus']
}
</script>