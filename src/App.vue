<template>
  <div id="app">
    <SendMessage/>
    <Messages/>
  </div>
</template>

<script>
import SendMessage from './components/SendMessage.vue'
import Messages from './components/Messages.vue'

export default {
  name: 'App',
  components: {
    SendMessage,
    Messages
  }
}
</script>

