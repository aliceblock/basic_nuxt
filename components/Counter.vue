<template>
  <div>
    <!--<span v-show="counter < 0">Negative Value</span>
    <span v-show="counter >= 0">{{ counter }}</span>-->
    <span v-if="counter < 0">Negative Value</span>
    <span v-else>{{ counter }}</span>
    <button type="button" @click="downVote">-</button>
    <button type="button" @click="upVote">+</button>
  </div>
</template>

<script>
export default {
  data: () => ({
    counter: 0
  }),
  methods: {
    downVote () {
      this.counter = this.counter - 1
    },
    upVote () {
      this.counter = this.counter + 1
    }
  }
}
</script>

<style scoped>
span {
  margin-right: 5px;
}
</style>
