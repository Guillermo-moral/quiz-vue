<template>
  <h1>Quiz App</h1>
  <ConfigGame/>
</template>

<script>
import ConfigGame from './components/ConfigGame.vue'

export default {
  name: 'Quiz',
  components: {
    ConfigGame
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;

  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  margin-top: 60px;
}
</style>
