<template>
  <div class="chat-bubble usr">
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

.chat-bubble.usr {
  padding: 10px;
  background-color: rgb(70, 70, 172);
  border-radius: 10px;
  max-width: 60%;
  align-self: flex-end;
}
</style>