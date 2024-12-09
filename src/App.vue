<template>
  <div id="app">
    <chat-field :messages="messages" />
  </div>
  <v-container>
      <v-text-field placeholder="Insert request" v-model="textPrompt"></v-text-field>
      <v-btn @click="sendRequest">Send</v-btn>
  </v-container>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import OpenAI from "openai";
import ChatField from './components/chatField.vue';

const textPrompt = ref("");
const messages = ref([{ text: "Hello.", type: 'bot' }
]);
const openai = new OpenAI({
  apiKey: "xai-OEb1pAbn63liSYIlyNACR3At3K7ZT6Vwn0e9EeWCBxo3rtOjvlZ1FBIZYIwATUNxKkcyBYJvYfSkLKSw",
  baseURL: "https://api.x.ai/v1",
  dangerouslyAllowBrowser: true ,
});
const sendRequest = async () => {
  messages.value.push({ text: textPrompt.value, type: 'user' });
  textPrompt.value = "";
  const completion = await openai.chat.completions.create({
    model: "grok-beta",
    messages: [
      { role: "system", 
        content: "You are Grok, a chatbot inspired by the Hitchhikers Guide to the Galaxy." },
      {
        role: "user",
        content: textPrompt.value,
      },
    ],
  });
  console.log(completion.choices[0].message.content);
  if (completion.choices[0].message.content !== null) {
    messages.value.push({ text: completion.choices[0].message.content, type: 'bot' });
  }

};

</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  align-content: center;
  height: 100vh;
  flex-direction: column;

}
.v-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}


</style>


