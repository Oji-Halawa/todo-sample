<template>
    <button
      :class="buttonClasses"
      @click="handleClick"
    >
      <span v-if="hasIcon && iconName" class="mr-2">
        <Icon :icon="iconName" class="w-5 h-5" :class="iconClassName" />
      </span>
      {{ label }}
    </button>
  </template>
  
  <script setup>
  import { Icon } from '@iconify/vue'
  import { computed } from 'vue'
  
  const props = defineProps({
    label: { type: String, required: true },
    variant: { type: String, default: 'primary' }, // primary, secondary, danger
    outline: { type: Boolean, default: false },
    hasIcon: { type: Boolean, default: false },
    customClass: { type: String, default: '' },
    iconName: { type: String, default: '' },
    iconClassName: { type: String, default: '' }
  })
  
  const emit = defineEmits(['click'])
  
  const variantClasses = {
    primary: 'bg-slate-700 hover:bg-slate-600 text-white',
    secondary: 'bg-gray-200 hover:bg-gray-300 text-gray-700',
    danger: 'bg-red-500 hover:bg-red-600 text-white'
  }
  
  const outlineClasses = {
    primary: 'border border-slate-700 text-slate-700 hover:bg-slate-100',
    secondary: 'border border-gray-400 text-gray-700 hover:bg-gray-100',
    danger: 'border border-red-500 text-red-500 hover:bg-red-100'
  }
  
  const buttonClasses = computed(() => {
    const baseClass =
      'px-6  py-3 font-medium rounded-xl transition-colors duration-200 flex items-center justify-center cursor-pointer'
  
    const variantClass = props.outline
      ? outlineClasses[props.variant]
      : variantClasses[props.variant]
  
    return `${baseClass} ${variantClass} ${props.customClass}`
  })
  
  function handleClick() {
    emit('click')
  }
  </script>
  