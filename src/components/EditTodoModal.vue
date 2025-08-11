<template>
    <BaseModal :show="show">
        <h2 class="text-lg font-semibold mb-4">Edit Todo</h2>
        <BaseInput v-model="localText" type="text" placeholder="Edit todo" @enter="save" />
        <div class="flex justify-end gap-2 mt-5">
            <BaseButton variant="secondary" label="Cancel" @click="$emit('cancel')" icon-name="heroicons:x-circle"
                has-icon iconClassName="text-gray-500" />

            <BaseButton variant="primary" label="Save" @click="save" icon-name="heroicons:arrow-up-right-16-solid"
                has-icon iconClassName="text-white" />
        </div>
    </BaseModal>
</template>

<script setup>
import { ref, watch } from 'vue'
import BaseModal from '@/components/Base/BaseModal.vue'
import BaseButton from '@/components/Base/Button.vue'
import BaseInput from '@/components/Base/Input.vue'

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