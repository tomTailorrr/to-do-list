<template>
    <div class="bg-yellow-500 min-h-screen flex flex-col items-center">
      <div class="bg-yellow-500 p-5 w-80 mx-auto text-center">
        <h1 class="text-4xl font-bold mb-5">TO-DO</h1>
        <button @click="showAddTask = true" class="bg-transparent border-2 border-black rounded-full w-8 h-8 text-2xl mb-5">+</button>
        <div v-for="task in tasks" :key="task.id" class="bg-black text-yellow-500 p-3 my-2 flex justify-between items-center">
          <span :class="{ 'line-through': task.done }">{{ task.text }}</span>
          <div>
            <input type="checkbox" v-model="task.done" class="form-checkbox mr-2" />
            <button @click="removeTask(task.id)" class="text-red-500 font-bold">X</button>
          </div>
        </div>
        <TaskForm v-if="showAddTask" @add-task="addTask" @close="showAddTask = false" />
      </div>
    </div>
  </template>
  
  <script>
  import TaskForm from './TaskForm.vue';
  
  export default {
    name: 'TodoList',
    components: {
      TaskForm
    },
    data() {
      return {
        tasks: [],
        showAddTask: false
      };
    },
    methods: {
      addTask(task) {
        this.tasks.push({ id: Date.now(), text: task, done: false });
        this.showAddTask = false;
      },
      removeTask(taskId) {
        this.tasks = this.tasks.filter(task => task.id !== taskId);
      }
    }
  };
  </script>
  
  <style scoped>
  .line-through {
    text-decoration: line-through;
  }
  </style>
  