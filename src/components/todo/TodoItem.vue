<template>
    <div class="flex items-center justify-between bg-white rounded-xl sm:rounded-2xl px-4 sm:px-6 py-3 sm:py-4 shadow-lg">
      <div class="flex-1 min-w-0 pr-3">
        {{todo.text}}
      </div>
  
      <div class="flex gap-1 sm:gap-2 lg:gap-3 ml-2 sm:ml-4 flex-shrink-0">
      <button @click="$emit('delete', todo.id)" class="p-1.5 sm:p-2 text-red-500 hover:bg-red-50 rounded-md sm:rounded-lg">
        🗑
      </button>
  
      <button
        @click="$emit('edit', todo.id )"
        class="p-1.5 sm:p-2 text-orange-500 hover:bg-orange-50 rounded-md sm:rounded-lg"
      >
        ✏
      </button>
    </div>
    </div>
  </template>
  
  <script setup>
  
  defineProps({
    todo: Object,
  })
  
  defineEmits(['delete', 'edit'])
  </script>
  