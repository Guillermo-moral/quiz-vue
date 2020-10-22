<template>
  <h1>Quiz App</h1>
  <ConfigGame @config-submitted="fetchQuestions" />
</template>

<script>
import ConfigGame from './components/ConfigGame.vue'


export default {
  name: 'Quiz',
  components: {
    ConfigGame
  },
  methods: {
    fetchQuestions(config) {
      console.log(config.numQuestions);
      console.log(config);
      //console.log(config);
      fetch(`https://opentdb.com/api.php?amount=${config.numQuestions}&category=${config.category}&difficulty=${config.difficulty}&type=multiple`)
        .then(res => res.json())
        .then(data => console.log(data))
    }
  },
  mounted() {
    
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
