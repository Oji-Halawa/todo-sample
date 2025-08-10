<template>
    <div
      v-if="show"
      class="fixed inset-0 flex items-center justify-center bg-black/60 bg-opacity-40 z-50"
    >
      <div class="bg-white rounded-lg p-6 max-w-md w-full shadow-lg">
        <slot />
      </div>
    </div>
  </template>
  
  <script setup>
  defineProps({
    show: Boolean
  })
  </script>
  