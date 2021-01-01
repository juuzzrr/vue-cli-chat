<template>
    <div class="container" id="Container">
      <ChatWindow>
        <ChatMessage>
        </ChatMessage>
      </ChatWindow>
    </div>
</template>
<script>
import ChatMessage from './ChatMessage.vue'
import ChatWindow from './ChatWindow.vue'
export default {
  name: 'Container',
  components: {
    ChatMessage,
    ChatWindow
  },
}
</script>
<style>
    .container {
    width: 764px;
    margin: auto;
    box-shadow: 0 0 15px 0 #5f5f5f73;
    }
</style>