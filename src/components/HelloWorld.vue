<template>
  <div class="hello">
  <p class="title is-large">HELLO</p>
    <div class="columns">
      <div class="column is-3"></div>
      <div class="column is-3 subtitle">
        <p>Name</p>
        <p>Type</p>
        <p>code</p>
        <p>text</p>
        </div>
      <div class="column is-3">
        <p><input class="input" type="text" v-model="name"></p>
        <p><input class="input" type="text" v-model="type"></p>
        <p><input class="input" type="text" v-model="code"></p>
        <p><input class="input" type="text" v-model="text"></p>
        </div>
      <div class="column is-3"></div>
    </div>
    <a class="button is-dark" @click="addproduct" >submit</a>
    <a class="button is-dark">cancel</a>
  </div>
</template>

<script>

import Firebase from 'firebase'
var config = {
  apiKey: 'AIzaSyB0DK0nuF8LAWVU34nU3fxrN47ktAICPnk',
  authDomain: 'sell-7bc46.firebaseapp.com',
  databaseURL: 'https://sell-7bc46.firebaseio.com',
  projectId: 'sell-7bc46',
  storageBucket: 'sell-7bc46.appspot.com',
  messagingSenderId: '795956250403'
}
let app = Firebase.initializeApp(config)
let db = app.database()
let dataRef = db.ref('data')

export default {
  name: 'HelloWorld',
  firebase: {
    data: dataRef
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      newData: [],
      name: '',
      type: '',
      code: '',
      text: ''
    }
  },
  methods: {
    addproduct () {
      let tmp = {
        name: this.name,
        type: this.type,
        code: this.code,
        text: this.text
      }
      dataRef.push(tmp)
    }
  }
}
</script>

<style scoped>

</style>
