<template>
   <button
        @click="addTodo"
        class="px-6 sm:px-8 py-3 sm:py-4 bg-slate-700 hover:bg-slate-600 text-white font-semibold rounded-xl sm:rounded-r-2xl sm:rounded-l-none transition-colors duration-200 text-base sm:text-lg"
    >
        {{label}}
    </button>
</template>

<script setup>
defineProps({
    id: String,
    label: String,
    type: String
})

const emit = defineEmits(['add'])
function addTodo() {
  emit('add') // kirim event 'enter' ke parent
}

</script>

<style lang="scss" scoped>

</style>