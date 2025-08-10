<template>
    <BaseModal :show="show">
      <h2 class="text-lg font-semibold mb-4">Edit Todo</h2>
      <input
        v-model="localText"
        @keyup.enter="save"
        class="w-full border rounded p-2 mb-4"
      />
      <div class="flex justify-end gap-2">
        <button @click="$emit('cancel')" class="px-4 py-2 bg-gray-200 rounded">Cancel</button>
        <button @click="save" class="px-4 py-2 bg-blue-500 text-white rounded">Save</button>
      </div>
    </BaseModal>
  </template>
  
  <script setup>
  import { ref, watch } from 'vue'
  import BaseModal from '@/components/Base/BaseModal.vue'
  
  const props = defineProps({
    show: Boolean,
    todoText: String
  })
  
  const emit = defineEmits(['save', 'cancel'])
  
  const localText = ref('')
  
  watch(
    () => props.todoText,
    (val) => {
      localText.value = val
    },
    { immediate: true }
  )
  
  function save() {
    emit('save', localText.value)
    localText.value = ''
  }
  </script>
  