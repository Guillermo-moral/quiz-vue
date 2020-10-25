<template>
  <h1>Quiz App</h1>
  <ConfigGame v-if="!isConfig" @config-submitted="fetchQuestions" />
  <Question
    v-if="isConfig"
    :question="currentQuestion"
    @answer-submitted="nextAnswer"
  />
</template>

<script>
import ConfigGame from './components/ConfigGame.vue'
import Question from './components/Question.vue'
import axios from 'axios'

export default {
  name: 'Quiz',
  components: {
    ConfigGame,
    Question
  },
  data() {
    return {
      isConfig: false,
      questions: {},
      currentQuestion: {},
      counterQuestions: 0,
      score: 0
    }
  },
  watch: {

  },
  methods: {
    fetchQuestions(config) {
      const url = `https://opentdb.com/api.php?amount=${config.numQuestions}&category=${config.category}&difficulty=${config.difficulty}&type=multiple`;
      axios.get(url).then(res => {
        this.questions = res.data.results
        this.isConfig = true
        this.currentQuestion = this.questions[this.counterQuestions]
        })
    },
    nextAnswer(answer) {
      if(answer) {
        this.score++
        console.log(this.score);
      }
      this.counterQuestions++
      this.currentQuestion = this.questions[this.counterQuestions]
    }
  },

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
