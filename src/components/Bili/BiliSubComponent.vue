<template>
  <div class="flex py-8px relative">
    <bili-avatar class="w-24px h-24px" small :src="data.avatar" :verify="data.verify">
    </bili-avatar>
    <div class="flex flex-col ml-34px">
      <div class="mb-2 text-13">
        <bili-nickname
          :nickname="data.nickname"
          :level="data.level"
          :vip="data.isVip"
        ></bili-nickname>
        <span class="ml-12px text-14 whitespace-pre-wrap break-words">{{ data.content }}</span>
      </div>
      <bili-comment-info :time="data.time" :like-count="data.likeCount"></bili-comment-info>
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
