<template>
  <form @submit.prevent="onSubmitGet">
    <span>Get</span>
    <input type="text" v-model="title">
    <button type="submit">Create</button>
  </form>
  <form @submit.prevent="onSubmitGetString">
    <span>Get String</span>
    <input type="text" v-model="title">
    <button type="submit">Create</button>
  </form>
  <form @submit.prevent="onSubmitGetForm">
    <span>Get String</span>
    <input type="text" v-model="title">
    <input type="number" v-model="number">
    <button type="submit">Create</button>
  </form>
  <form @submit.prevent="onSubmitPost">
    <span>Post</span>
    <input type="text" v-model="title">
    <button type="submit">Create</button>
  </form>
  <form @submit.prevent="onSubmitPostString">
    <span>Post String</span>
    <input type="text" v-model="title">
    <button type="submit">Create</button>
  </form>
  <hr>
</template>

<script>
export default {
  name: "Message",
  data() {
    return {
      title: '',
      number: 0
    }
  },
  methods: {
    onSubmitGet() {
      const axios = require('axios');
      axios.get('http://localhost:5001/messages/get')
          .then(function (response) {
            // handle success
            console.log(response);
          })
          .catch(function (error) {
            // handle error
            console.log(error);
          })
          .then(function () {
            // always executed
          })
    },
    onSubmitGetString() {
      const axios = require('axios');
      axios.get('http://localhost:5001/messages/get/string', {
        params: {
          content: "test message!!!"
        }
        })
        .then(function (response) {
        // handle success
        console.log(response);
        })
        .catch(function (error) {
        // handle error
        console.log(error);
        })
        .then(function () {
        // always executed
        })
    },
    onSubmitGetForm() {
      const axios = require('axios');
      axios.get('http://localhost:5001/messages/get/form', {
        params: {
          title: this.title,
          number: this.number
        }
      })
          .then(function (response) {
            // handle success
            console.log(response);
          })
          .catch(function (error) {
            // handle error
            console.log(error);
          })
          .then(function () {
            // always executed
          })
    },
    onSubmitPost() {
      const axios = require('axios');
      axios.post('http://localhost:5001/messages/post')
          .then(function (response) {
            // handle success
            console.log(response);
          })
          .catch(function (error) {
            // handle error
            console.log(error);
          })
          .then(function () {
            // always executed
          })
    },
    onSubmitPostString() {
      const axios = require('axios');
      axios.post('http://localhost:5001/messages/post/string', {
        params: {
          content: "test message!!!"
        }
      })
          .then(function (response) {
            // handle success
            console.log(response);
          })
          .catch(function (error) {
            // handle error
            console.log(error);
          })
          .then(function () {
            // always executed
          })
    }
  }
}
</script>

<style scoped>

</style>