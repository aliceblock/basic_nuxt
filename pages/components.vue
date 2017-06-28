<template>
  <div class="container">
    <h2>Using component</h2>
    <Counter></Counter>
    <nuxt-link to="/">Index</nuxt-link>
  </div>
</template>

<script>
import Counter from '~components/Counter'

export default {
  components: {
    // Counter: Counter,
    Counter
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
