<template>
    <input
        :model-value="modelValue"
        @input="onInput"
        @keyup.enter="onEnter"
        :type="type"
        :placeholder="placeholder"
        class="flex-1 px-4 sm:px-6 py-3 sm:py-4 text-base bg-white rounded-xl   outline-none border w-full border-gray-400 text-gray-700 placeholder-gray-400"
    />
</template>

<script setup>
defineProps({
    id: String,
    modelValue: String,
    placeholder: String,
    type: String
})

const emit = defineEmits(['update:modelValue', 'enter'])
function onEnter() {
  emit('enter') // kirim event 'enter' ke parent
}

function onInput(event) {
  emit('update:modelValue', event.target.value) // kirim update:modelValue 'enter' ke parent
}
</script>

<style lang="scss" scoped>

</style>