<template>
  <div class="min-h-screen bg-gradient-to-br from-teal-800 via-slate-800 to-purple-800 p-4 sm:p-6 lg:p-8">
    <div class="max-w-sm sm:max-w-md md:max-w-lg lg:max-w-2xl mx-auto">
      <!-- Title -->
      <h1 class="text-2xl sm:text-3xl lg:text-4xl font-bold text-white text-center mb-8 sm:mb-10 lg:mb-12 tracking-wider px-4">
        MY TO DO LIST
      </h1>
      
      <!-- Add Todo Form -->
      <div class="flex flex-col sm:flex-row gap-3 sm:gap-0 mb-6 sm:mb-8 px-4 sm:px-0">
        <BaseInput
          v-model="newTodo"
          type="text"
          placeholder="Masukan to do list"
          @enter="handleAddTodo"
        />

        <BaseButton label="Save" @add="handleAddTodo" />
      </div>
      
      <!-- Todo List -->
      <TodoList
      :todos="todos"
      :editing-id="editingId"
      :edit-text="editText"
      @delete="handleDeleteTodo"
      @edit="openEditModal"
    />

    <EditTodoModal
      :show="isEditModalOpen"
      :todo-text="editText"
      @save="saveEdit"
      @cancel="closeEditModal"
    />
      
      <!-- Empty State -->
      <div v-if="todos.length === 0" class="text-center py-8 sm:py-12 px-4">
        <p class="text-white/60 text-base sm:text-lg">No tasks yet. Add your first to-do item above!</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import BaseInput from '@/components/Base/Input.vue'
import BaseButton from '@/components/Base/Button.vue'
import TodoList from '@/components/todo/TodoList.vue'
import EditTodoModal from '@/components/EditTodoModal.vue'


// Reactive data
const newTodo = ref('')
const isEditModalOpen = ref(false)
const editingId = ref(null)
const editText = ref('')

// Initial todos matching the image
const todos = ref([
  { id: 1, text: 'Membuat Api', completed: false },
  { id: 2, text: 'Membuat tampilan Home page', completed: false },
  { id: 3, text: 'Dashboard Menu', completed: false },
  { id: 4, text: 'Usability testing bareng marketing', completed: false }
])

let nextId = 5

// Functions
const handleAddTodo = () => {
  if (newTodo.value.trim()) {
    todos.value.push({
      id: nextId++,
      text: newTodo.value.trim(),
      completed: false
    })
    newTodo.value = ''
  }
}

const handleDeleteTodo = (id) => {
  todos.value = todos.value.filter(todo => todo.id !== id)
}

function openEditModal(id, text) {
  editingId.value = id
  editText.value = text
  isEditModalOpen.value = true
}

function closeEditModal() {
  isEditModalOpen.value = false
}

function saveEdit(newText) {
  const todo = todos.value.find(t => t.id === editingId.value)
  if (todo) todo.text = newText

  closeEditModal()
}
</script>