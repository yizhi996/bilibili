<template>
  <div class="flex-shrink-0" :class="small ? 'absolute left-0 top-9px' : 'relative'">
    <img
      class="bg-white absolute left-2/4 top-2/4 -translate-x-2/4 -translate-y-2/4 border border-gray box-content w-full h-full rounded-full object-cover"
      :src="src"
    />
    <i
      v-if="verify"
      class="verify bg-cover absolute right-0 -bottom-1px"
      :class="small ? 'w-12px h-12px' : 'w-18px h-18px'"
    ></i>
  </div>
</template>

<script setup lang="ts">
withDefaults(
  defineProps<{
    src?: string
    verify: boolean
    small?: boolean
  }>(),
  {
    small: false,
    verify: false
  }
)
</script>

<style scoped>
.verify {
  background-image: url('/src/assets/verify.svg');
}

.border-gray {
  border-color: #f1f2f3;
}
</style>
