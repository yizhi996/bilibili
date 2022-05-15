<template>
  <div class="flex items-center text-sm">
    <span class="cursor-default select-none flex-shrink-0">{{ title }}：</span>
    <component
      :is="textarea ? 'textarea' : 'input'"
      class="appearance-none w-60 h-10 border px-1 rounded-md shadow-sm"
      :value="modelValue"
      @input="onInput"
    />
  </div>
</template>

<script setup lang="ts">
const emit = defineEmits(['update:modelValue'])

withDefaults(
  defineProps<{
    modelValue?: string
    title: string
    textarea?: boolean
  }>(),
  {
    textarea: false
  }
)

const onInput = (ev: Event) => {
  const target = ev.target as HTMLInputElement
  emit('update:modelValue', target.value)
}
</script>
