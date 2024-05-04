<script setup lang="ts">
import { ref } from 'vue'

const chatInput = ref('Why is the sky blue?')

const submitChat = () => {
  console.log('submitting chat', chatInput.value)
  chatInput.value = ''
}
</script>

<template>
  <div id="chatBox">
    <div id="chatContainer">
      <div id="chatArea" ref="chatArea"></div>
    </div>
    <div id="inputArea">
      <input id="chatInput" v-model="chatInput" @keyup.enter="submitChat" />
      <button @click="submitChat" id="submitButton">Submit</button>
    </div>
  </div>
</template>

<style scoped>
#chatBox {
  display: flex;
  height: 100%;
  flex-direction: column;
}

#chatContainer {
  position: relative;
  width: 100%;
  height: calc(100% - 100px);
}

#chatArea {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  overflow-y: auto;
}
</style>