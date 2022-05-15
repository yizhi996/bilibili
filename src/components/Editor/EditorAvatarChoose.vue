<template>
  <div class="flex items-center text-sm">
    <span class="cursor-default select-none flex-shrink-0">{{ title }}：</span>
    <input ref="inputRef" class="hidden" type="file" accept="image/*" @change="onChange" />
    <button class="rounded-md px-2 py-1 bg-blue-500 text-white" @click="choose">选择图片</button>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const emit = defineEmits(['update:modelValue'])

defineProps<{
  modelValue?: string
  title: string
}>()

const inputRef = ref<HTMLElement>()

const choose = () => {
  inputRef.value!.click()
}

const onChange = (ev: Event) => {
  const target = ev.target as HTMLInputElement
  if (target.files && target.files.length) {
    const src = URL.createObjectURL(target.files[0])
    emit('update:modelValue', src)
  }
}
</script>
