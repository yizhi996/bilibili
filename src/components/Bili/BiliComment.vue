<template>
  <div class="flex">
    <bili-avatar
      class="w-50px h-50px mt-24px mr-30px"
      :src="data.avatar"
      :verify="data.verify"
    ></bili-avatar>
    <div class="flex flex-col pt-22px pb-14px">
      <bili-nickname
        class="mb-2px"
        :nickname="data.nickname"
        :level="data.level"
        :vip="data.isVip"
      ></bili-nickname>
      <p class="text-14 mb-6px whitespace-pre-wrap break-words">{{ data.content }}</p>
      <bili-comment-info :time="data.time" :like-count="data.likeCount"></bili-comment-info>
      <slot></slot>
    </div>
  </div>
</template>

<script setup lang="ts">
import BiliAvatar from './BiliAvatar.vue'
import BiliNickname from './BiliNickname.vue'
import BiliCommentInfo from './BiliCommentInfo.vue'
import { CommentData } from '../../models/comment'

defineProps<{ data: CommentData }>()
</script>
