<template>
  <div
    class="font-normal relative flex flex-col px-2.5 mt-10 "
    :class="isPreview ? 'flex mt-0 items-center justify-center w-full h-screen' : ''"
    @mousemove="showExitPreviewButton"
    @touchmove="showExitPreviewButton"
  >
    <div class="flex-shrink-0" :style="!isPreview ? 'width:720px;' : 'max-width: 720px;'">
      <bili-comment class="ml-14px" :data="commentData">
        <div class="mt-4px"><bili-sub-component :data="subComponentData"></bili-sub-component></div>
      </bili-comment>
    </div>
    <div v-show="!isPreview" class="mx-2.5 my-10 flex flex-col">
      <span class="text-sm text-gray-600"
        >旋转屏幕，双指放大（PC 端放大网页），可获得更高质量。</span
      >
      <button class="mt-1 w-20 rounded-md px-2 py-1 bg-blue-500 text-white" @click="preview">
        预览模式
      </button>
      <div class="mt-2.5 flex flex-col sm:flex-row space-y-5 sm:space-x-5 sm:space-y-0">
        <editor :data="commentData" title="主评论"></editor>
        <editor :data="subComponentData" title="子评论"></editor>
      </div>
    </div>
    <button
      v-show="isPreview && isShowExitPreviewButton"
      class="absolute top-20 rounded-md px-2 py-1 bg-blue-500 text-white"
      @click="preview"
    >
      退出预览模式
    </button>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue'
import BiliComment from './components/Bili/BiliComment.vue'
import BiliSubComponent from './components/Bili/BiliSubComponent.vue'
import Editor from './components/Editor/Editor.vue'
import { CommentData } from './models/comment'
import mongolia from './assets/mongolia.jpg'
import chenrui from './assets/chenrui.png'

const commentData = reactive<CommentData>({
  avatar: chenrui,
  nickname: '陈睿',
  isVip: true,
  verify: true,
  level: '6',
  content: '你所热爱的，就是你的生活。',
  time: '2020-05-04 00:14',
  likeCount: '79586'
})

const subComponentData = reactive<CommentData>({
  avatar: mongolia,
  nickname: '蒙古上单',
  isVip: true,
  verify: false,
  level: '5',
  content: '你 妈什么时候死啊？',
  time: '0秒前',
  likeCount: ''
})

const isPreview = ref(false)

const preview = () => {
  isPreview.value = !isPreview.value
}

const isShowExitPreviewButton = ref(false)

let hideExitPreviewButtonTimer: ReturnType<typeof setTimeout>

const showExitPreviewButton = () => {
  isShowExitPreviewButton.value = true

  clearTimeout(hideExitPreviewButtonTimer)
  hideExitPreviewButtonTimer = setTimeout(() => {
    isShowExitPreviewButton.value = false
  }, 1000)
}
</script>

<style>
#app {
  font-family: 'Helvetica Neue', sans-serif;
  -webkit-font-smoothing: antialiased;
}
</style>
