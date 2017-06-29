<template>
  <div class="container">
    <h2>Using component</h2>
    <Counter></Counter>
    <hr>
    <h2>Component event</h2>
    {{ parent_num }}
    <Numpad @setNum="setParentNum($event)"></Numpad>
    <hr>
    <h2>Component sync value</h2>
    {{ parent_num }}
    <Numpad2 :value.sync="parent_num"></Numpad2>
    <hr>
    <nuxt-link to="/">Index</nuxt-link>
  </div>
</template>

<script>
import Counter from '~components/Counter'
import Numpad from '~components/Numpad'
import Numpad2 from '~components/Numpad2'

export default {
  components: {
    // Counter: Counter,
    Counter,
    Numpad,
    Numpad2
  },
  data: () => ({
    parent_num: 0
  }),
  methods: {
    setParentNum (num) {
      this.parent_num = num
    }
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
