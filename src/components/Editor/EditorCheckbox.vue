<template>
  <div class="flex items-center text-sm">
    <span class="cursor-default select-none flex-shrink-0">{{ title }}：</span>
    <input class="border px-1" type="checkbox" :checked="modelValue" @change="onChange" />
  </div>
</template>

<script setup lang="ts">
const emit = defineEmits(['update:modelValue'])

defineProps<{
  modelValue?: boolean
  title: string
}>()

const onChange = (ev: Event) => {
  const target = ev.target as HTMLInputElement
  emit('update:modelValue', target.checked)
}
</script>
