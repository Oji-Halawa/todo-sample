<template>
    <div class="space-y-3 sm:space-y-4 px-4 sm:px-0">
      <TodoItem
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        :editing-id="editingId"
        :edit-text="editText"
        @delete="deleteTodo"
        @edit="editTodo"
      />
    </div>
  </template>
  
  <script setup>
  import TodoItem from './TodoItem.vue'
  
  defineProps({
    todos: Array,
    editingId: Number,
    editText: String
  })
  
  const emit = defineEmits([
    'delete',
    'edit',
  ])

  const deleteTodo = (id) => {
    emit('delete', id  )
  }

  const editTodo = (id) => {
    emit('edit', id  )
  }
  </script>
  