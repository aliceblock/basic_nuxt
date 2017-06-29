<template>
  <div>
    <button type="button" @click="select(1)">1</button>
    <button type="button" @click="select(2)">2</button>
    <button type="button" @click="select(3)">3</button>
    <button type="button" @click="select(4)">4</button>
  </div>
</template>

<script>
export default {
  methods: {
    select (number) {
      this.$emit('setNum', number)
    }
  }
}
</script>

<style>

</style>
