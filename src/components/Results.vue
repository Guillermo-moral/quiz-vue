<template>
  <h1>You got {{ score }} questions right out of {{ questions }}</h1>
  <button @click="playAgain">Play again</button>
</template>

<script>
export default {
  name: 'Results',
  props: {
    score: Number,
    questions: Number
  },
  emits:['new-game'],
  methods: {
    playAgain() {
      this.$emit('new-game')
    }
  }
}
</script>

<style>

</style>