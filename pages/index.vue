<template>
  <div class="container">
    <h1>Show message data: {{ message }}</h1>
    <hr>
    <h2>Two-way data binding</h2>
    <!--<p v-bind:title="text_input">{{ text_input }}</p>-->
    <p :title="text_input">{{ text_input }}</p>
    <input type="text" v-model="text_input">
    <hr>
    <h2>For loop</h2>
    <ul>
      <li v-for="user in users">Name - {{ user.name }}, Age - {{ user.age }}</li>
    </ul>
    <hr>
    <h2>Event binding</h2>
    <p>{{ message }}</p>
    <!--<button v-on:click="reverseMessage">Reverse Message</button>-->
    <button @click="reverseMessage">Reverse Message</button>
    <hr>
    <h2>Mounted value</h2>
    <ul>
      <li v-for="food in loaded_values">{{ food.name }} ({{ food.price }} Baht)</li>
    </ul>
    <hr>
    <nuxt-link to="/components">Components</nuxt-link>
    <button type="button" @click="goToComponent">Components</button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  // data: function() {
  //   return {
  //     message: 'Hello Vue!!'
  //   }
  // }
  // data () {
  //   return {
  //     message: 'Hello Vue!!'
  //   }
  // }
  data: () => ({
    message: 'Hello Vue!!',
    text_input: 'Enter your text here!!',
    users: [
      {name: 'A', age: '15'},
      {name: 'B', age: '16'},
      {name: 'C', age: '15'},
      {name: 'D', age: '16'},
      {name: 'E', age: '18'}
    ],
    loaded_values: []
  }),
  methods: {
    reverseMessage () {
      this.message = this.message.split('').reverse().join('')
    },
    goToComponent () {
      this.$router.push('/components')
    }
  },
  mounted () {
    // Maybe uses AJAX here and assigns values
    axios.get('https://nuxt-da01e.firebaseio.com/food.json')
      .then((response) => {
        console.log(response)
        this.loaded_values = response.data
      })
  }
}
</script>

<style>
.container {
  padding: 20px;
}
hr {
  margin: 30px;
}
</style>
