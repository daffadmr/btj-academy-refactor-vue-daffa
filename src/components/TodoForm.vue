<template>
  <form class="todo-form border-2 rounded-md p-5 flex flex-col justify-center items-center gap-5">
    <div class="input-section w-full flex flex-col md:flex-row gap-5">
      <div class="input-group w-full md:w-[50%] flex flex-col">
        <label for="name">Name</label>
        <input class="border-2 rounded-md p-2" type="text" placeholder="Nama todo" v-model="todoInput.name" />
      </div>
      <div class="input-group w-full md:w-[50%] flex flex-col">
        <label for="priority">Priority</label>
        <select class="border-2 rounded-md p-2" name="priority" id="priority" v-model="todoInput.priority">
          <option value="High">High</option>
          <option value="Medium">Medium</option>
          <option value="Low">Low</option>
        </select>
      </div>
    </div>
    <button type="submit" @click="addTodo"
      class="w-full lg:w-1/5 self-end bg-green-400 border-2 border-transparent p-2 rounded-md text-white">
      Save
    </button>
  </form>
</template>

<script>
export default {
  inject: ['todoList', 'todoInput', 'addTodo'],
}
</script>
