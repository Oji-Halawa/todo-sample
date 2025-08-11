<template>
    <div
        class="flex items-center justify-between bg-white rounded-xl sm:rounded-2xl px-4 sm:px-6 py-3 sm:py-4 shadow-lg">
        <div class="flex-1 min-w-0 pr-3">
            {{ todo.text }}
        </div>

        <div class="flex gap-1 sm:gap-2 lg:gap-3 ml-2 sm:ml-4 flex-shrink-0">
            <BaseButton label="Delete" variant="danger" outline icon-name="heroicons:trash" has-icon
                @click="$emit('delete', todo.id)" iconClassName="text-red-500">
            </BaseButton>


            <BaseButton label="Edit" variant="primary" outline icon-name="heroicons-outline:pencil-alt" has-icon
                @click="$emit('edit', todo.id)" iconClassName="text-teal-800">
            </BaseButton>
        </div>
    </div>
</template>

<script setup>
import { Icon } from "@iconify/vue";
import BaseButton from '@/components/Base/Button.vue'
defineProps({
    todo: Object,
})

defineEmits(['delete', 'edit'])
</script>