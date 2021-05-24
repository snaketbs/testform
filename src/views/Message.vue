<template>
  <div>
    <div>
      <form @submit.prevent="onSubmitRequest">
        <select v-model="filter">
          <option value="get">GET</option>
          <option value="post">Post</option>
        </select>
        <input type="text" v-model="formarguments[0]">
        <input type="text" v-model="formarguments[1]">
        <input type="text" v-model="formarguments[2]">
        <input type="text" v-model="formarguments[3]">
        <button type="submit">Request</button>
      </form>
    </div>
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
  </div>
  <hr>
  <p>{{textCont}}</p>
  <button v-on:click="onButtonFirst">Change Text</button>
</template>

<script>
export default {
  name: "Message",
  data() {
    return {
      title: "",
      number: 0,
      textCont: "",
      filter: 'get',
      formarguments: []
    }
  },
  // watch: {
  //  filter(value) {
  //    console.log(value)
  //  }
  //},
  methods: {
    onSubmitRequest() {
      if(this.filter === 'get') {
        console.log('+++ get')
      }

      if(this.filter === 'post') {
        console.log('+++ post')
      }

      this.formarguments.forEach(element => console.log(element));
    },
    onButtonFirst() {
      this.textCont = "fsdffsfs"
    },
    onSubmitGet() {
      var text = ""
      const axios = require('axios');
      axios.get('http://localhost:5001/messages/get')
          .then(function (response) {
            // handle success
            console.log(response);
            text = response
          })
          .catch(function (error) {
            // handle error
            console.log(error);
          })
          .then(function () {
            // always executed
          }).finally(() => {
        this.textCont = text
      })
    },
    onSubmitGetString() {
      var text = ""
      const axios = require('axios');
      axios.get('http://localhost:5001/messages/get/string', {
        params: {
          content: "test message!!!"
        }
        })
        .then(function (response) {
        // handle success
        console.log(response);
          text = response
        })
        .catch(function (error) {
        // handle error
        console.log(error);
        })
        .then(function () {
        // always executed
        }).finally(() => {
        this.textCont = text
      })
    },
    onSubmitGetForm() {
      var text = ""
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
            text = response
          })
          .catch(function (error) {
            // handle error
            console.log(error);
          })
          .then(function () {
            // always executed
          }).finally(() => {
        this.textCont = text
      })
    },
    onSubmitPost() {
      var text = ""
      const axios = require('axios');
      axios.post('http://localhost:5001/messages/post')
          .then(function (response) {
            // handle success
            console.log(response);
            text = response
          })
          .catch(function (error) {
            // handle error
            console.log(error);
          })
          .then(function () {
            // always executed
          }).finally(() => {
        this.textCont = text
      })
    },
    onSubmitPostString() {
      var text = ""
      const axios = require('axios');
      axios.post('http://localhost:5001/messages/post/string', {
        params: {
          content: "test message!!!"
        }
      })
          .then(function (response) {
            // handle success
            console.log(response);
            text = response
          })
          .catch(function (error) {
            // handle error
            console.log(error);
          })
          .then(function () {
            // always executed
          }).finally(() => {
        this.textCont = text
      })
    }
  }
}
</script>

<style scoped>

</style>