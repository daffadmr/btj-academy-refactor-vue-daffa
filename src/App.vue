<script setup>
import TodoList from './components/TodoList.vue';
import { computed } from 'vue'
</script>

<template>
  <div class="container p-5 flex justify-center items-center min-h-screen">
    <TodoList />
  </div>
</template>

<script>
export default {
  data() {
    return {
      todoList: [
        { id: 100, name: "Nonton Twice", priority: "High", isCompleted: false },
        { id: 121, name: "Ngopi", priority: "Medium", isCompleted: false },
        { id: 423, name: "Ngoding", priority: "Low", isCompleted: false },
      ],
      todoInput: {
        name: "",
        priority: "",
        isCompleted: false,
      },
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      if (this.todoInput.name === "" && this.todoInput.priority === "") {
        alert("Nama todo dan prioritas tidak boleh kosong!");
      } else if (this.todoInput.name === "") {
        alert("Nama todo tidak boleh kosong!");
      } else if (this.todoInput.priority === "") {
        alert("Prioritas todo tidak boleh kosong");
      } else {
        this.todoList.push({
          id: Math.round(Math.random() * (999 - 100)),
          name: this.todoInput.name,
          priority: this.todoInput.priority,
          isCompleted: false,
        });
        this.todoInput.name = "";
        this.todoInput.priority = "";
      }
    },
    deleteTodo(id) {
      this.todoList = this.todoList.filter((todo) => todo.id !== id);
    },
    completeTodo(id) {
      this.todoList.map((todo) => {
        if (id === todo.id) {
          todo.isCompleted = !todo.isCompleted;
        }
      });
    },
  },
  computed: {
    todoCompleted() {
      return this.todoList.filter((todo) => !todo.isCompleted);
    },
    todoNotCompleted() {
      return this.todoList.filter((todo) => todo.isCompleted);
    },
    pendingTodo() {
      let pending = this.todoList.filter((todo) => !todo.isCompleted);
      return pending.length;
    },
    lowPriorityTodo() {
      let lowPriority = this.todoList.filter(
        (todo) => todo.priority === "Low" && !todo.isCompleted
      );
      return lowPriority.length;
    },
    mediumPriorityTodo() {
      let mediumPriority = this.todoList.filter(
        (todo) => todo.priority === "Medium" && !todo.isCompleted
      );
      return mediumPriority.length;
    },
    highPriorityTodo() {
      let highPriority = this.todoList.filter(
        (todo) => todo.priority === "High" && !todo.isCompleted
      );
      return highPriority.length;
    },
    completedTodo() {
      let completed = this.todoList.filter((todo) => todo.isCompleted);
      return completed.length;
    },
    todoStatus() {
      return [
        {
          name: "PENDING",
          value: this.pendingTodo,
        },
        {
          name: "LOW",
          value: this.lowPriorityTodo,
        },
        {
          name: "MEDIUM",
          value: this.mediumPriorityTodo,
        },
        {
          name: "HIGH",
          value: this.highPriorityTodo,
        },
        {
          name: "COMPLETED",
          value: this.completedTodo,
        },
      ];
    },
    emptyTodo() {
      return this.todoCompleted.length === 0;
    },
    emptyCompletedTodo() {
      return this.todoNotCompleted.length === 0;
    },
  },
  provide() {
    return {
      todoList: this.todoList,
      todoInput: this.todoInput,
      addTodo: this.addTodo,
      deleteTodo: this.deleteTodo,
      completeTodo: this.completeTodo,
      todoCompleted: computed(() => this.todoCompleted),
      todoNotCompleted: computed(() => this.todoNotCompleted),
      todoStatus: computed(() => this.todoStatus),
      emptyCompletedTodo: computed(() => this.emptyCompletedTodo),
      emptyTodo: computed(() => this.emptyTodo)
    }
  },
}
</script>