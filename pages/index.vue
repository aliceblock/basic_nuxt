<template>
  <div class="container">
    <h1>Show message data: {{ message }}</h1>
    <h1 v-text="'Show message data: '+message"></h1>
    <h1 v-html="'<span style=\'color:red;\'>Show message data: '+message+'</span>'"></h1>

    <hr>

    <h2>Two-way data binding</h2>
    <!--<p v-bind:title="text_input">{{ text_input }}</p>-->
    <p :title="text_input">{{ text_input }}</p>
    <input type="text" v-model="text_input">

    <hr>

    <h2>Computed variable</h2>
    <p>{{ full_name }}</p>
    <input type="text" v-model="name">
    <input type="text" v-model="surname">

    <hr>

    <h2>Class & Style binding</h2>
    <div :class="[divColor, divShow? 'isShow': '']" style="width: 100px; height: 100px"></div>
    <button @click="divColor = 'isRed'">Red</button>
    <button @click="divColor = 'isBlue'">Blue</button>

    <hr>

    <h2>For loop</h2>
    <ul>
      <li :key="user" v-for="user in users">Name - {{ user.name }}, Age - {{ user.age }}</li>
    </ul>

    <hr>

    <h2>Event binding</h2>
    <p>{{ message }}</p>
    <!--<button v-on:click="reverseMessage">Reverse Message</button>-->
    <button @click="reverseMessage">Reverse Message</button>

    <hr>

    <h2>Mounted value</h2>
    <ul>
      <li :key="food" v-for="food in loaded_values">{{ food.name }} ({{ food.price }} Baht)</li>
    </ul>

    <hr>

    <nuxt-link to="/components">[Components]</nuxt-link>
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
    loaded_values: [],
    name: 'Firstname',
    surname: 'Lastname',
    divColor: 'isRed',
    divShow: true
  }),
  computed: {
    full_name () {
      return this.name + ' ' + this.surname
    }
  },
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

<style lang="scss">
.container {
  padding: 20px;
}
hr {
  margin: 30px;
}
// div.isRed {
//   background-color: red;
// }
// div.isBlue {
//   background-color: blue;
// }
div {
  .isRed {
    background-color: red;
  }
  .isBlue {
    background-color: blue;
  }
}
</style>
