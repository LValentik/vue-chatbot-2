<template>
  <div class="chat-bubble bot">
    {{ message }}
  </div>
</template>

<script setup lang="ts">
import { defineProps } from 'vue';

const props = defineProps({
  message: {
    type: String,
    required: true
  }
});
</script>

<style scoped>
.chat-bubble {
  padding: 10px;
  background-color: gray;
  border-radius: 10px;
  max-width: 60%;
}

.chat-bubble.bot {
  padding: 10px;
  background-color: rgb(59, 59, 59);
  border-radius: 10px;
  max-width: 60%;
  align-self: flex-start;
}
</style>