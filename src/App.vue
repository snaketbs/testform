<template>
  <div id="app">
    <h1>Test Form</h1>
    <hr>
    <Message />
  </div>
</template>

<script>
import Message from '@/views/Message'

export default {
  name: 'App',
  components: {
    Message
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
