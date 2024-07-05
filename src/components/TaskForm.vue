<template>
    <div class="bg-black text-yellow-500 p-5 w-80 mx-auto text-center rounded-lg shadow-lg">
      <h2 class="text-3xl font-bold mb-5">ДОБАВИТЬ</h2>
      <input v-model="newTask" placeholder="НОВАЯ ЗАДАЧА" class="w-full p-2 mb-5 rounded border-none text-black" />
      <button @click="saveTask" class="bg-yellow-500 text-black py-2 px-5 rounded mb-2">СОХРАНИТЬ</button>
      <button @click="$emit('close')" class="bg-red-500 text-black py-2 px-5 rounded">X</button>
    </div>
  </template>
  
  <script>
  export default {
    name: 'TaskForm',
    data() {
      return {
        newTask: ''
      };
    },
    methods: {
      saveTask() {
        this.$emit('add-task', this.newTask);
        this.newTask = '';
      }
    }
  };
  </script>
  