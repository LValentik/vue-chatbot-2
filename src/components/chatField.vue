<template>
  <div class="chat-field">
    <component
      v-for="(message, index) in messages"
      :is="message.type === 'user' ? ChatBubbleUsr : ChatBubbleBot"
      :key="index"
      :message="message.text"
    />
  </div>
</template>

<script setup lang="ts">
import { defineProps } from 'vue';
import ChatBubbleUsr from './chatBubbleusr.vue';
import ChatBubbleBot from './chatBubblebot.vue';

const props = defineProps<{
  messages: { text: string; type: string }[];
}>();
</script>

<style scoped>
.chat-field {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 80vw;
}
</style>