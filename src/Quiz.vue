<template>
  <h1>Quiz App</h1>
  <ConfigGame v-if="isConfig" @config-submitted="fetchQuestions" />
  <Question
    v-if="!isConfig"
    :questions="questions"
    :prueba="prueba"
  />
</template>

<script>
import ConfigGame from './components/ConfigGame.vue'
import Question from "./components/Question.vue";

export default {
  name: 'Quiz',
  components: {
    ConfigGame,
    Question
  },
  data() {
    return {
      isConfig: true,
      questions: [],
      prueba: ''
    }
  },
  methods: {
    fetchQuestions(config) {
      let url = `https://opentdb.com/api.php?amount=${config.numQuestions}&category=${config.category}&difficulty=${config.difficulty}&type=multiple`;
      fetch(url)
        .then(res => res.json())
        .then(data => {
          this.questions = data;
          this.isConfig = false;
          console.log(this.questions.results);
        })
    }
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
