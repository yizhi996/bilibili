<template>
  <span class="inline-flex items-center h-22px">
    <span class="text-13" :class="vip ? 'text-b-pink' : 'text-b-gray'">{{ nickname }}</span>
    <img class="ml-5px w-22px h-22px" v-if="levelURL" :src="levelURL" />
  </span>
</template>

<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps<{ nickname: string; level: string; vip: boolean }>()

const levelURL = computed(() => {
  const modules = import.meta.globEager('../../assets/*.svg')
  const i = parseInt(props.level)
  if (i >= 0 && i <= 6) {
    const path = `../../assets/level_${props.level}.svg`
    return modules[path].default
  }
  return ''
})
</script>
