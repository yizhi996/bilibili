<template>
  <div class="flex items-center text-b-gray-2 text-13">
    <span class="mr-19px">{{ time }}</span>
    <i class="like w-4 h-4 mr-5px bg-center bg-cover bg-no-repeat mb-1px ml-1px cursor-pointer"></i>
    <span class="mr-19px">{{ likeCount }}</span>
    <i
      class="heat w-4 h-4 bg-center bg-cover bg-no-repeat mr-19px mb-1px ml-1px cursor-pointer"
    ></i>
    <span class="ml-5px cursor-pointer">回复</span>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  time?: string
  likeCount?: string
}>()
</script>

<style scoped>
.like {
  background-image: url('/src/assets/like.svg');
}

.heat {
  background-image: url('/src/assets/heat.svg');
}
</style>
