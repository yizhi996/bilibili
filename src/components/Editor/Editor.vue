<template>
  <div class="w-80 border rounded-md shadow-sm bg-gray-100 p-2.5">
    <span>{{ title }}</span>
    <div class="flex flex-col items-center space-y-2 mt-1">
      <editor-avatar-choose v-model="data.avatar" title="头像"></editor-avatar-choose>
      <editor-input v-model="data.nickname" title="昵称"></editor-input>
      <editor-input v-model="data.content" title="评论" textarea></editor-input>
      <editor-input v-model="data.time" title="时间"></editor-input>
      <editor-input v-model="data.likeCount" title="点赞"></editor-input>
      <editor-input v-model="data.level" title="等级"></editor-input>
      <div class="flex space-x-5">
        <editor-checkbox v-model="data.isVip" title="大会员"></editor-checkbox>
        <editor-checkbox v-model="data.verify" title="认证"></editor-checkbox>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import EditorInput from './EditorInput.vue'
import EditorCheckbox from './EditorCheckbox.vue'
import EditorAvatarChoose from './EditorAvatarChoose.vue'
import { CommentData } from '../../models/comment'

defineProps<{ title: string; data: CommentData }>()
</script>
