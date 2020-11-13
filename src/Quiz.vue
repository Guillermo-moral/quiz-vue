<template>
  <h1>Quiz App</h1>
  <ConfigGame v-if="!isConfig" @config-submitted="fetchQuestions" />
  <Question
    v-if="isConfig && !gameOver"
    :question="currentQuestion"
    @answer-submitted="nextAnswer"
  />
  <Results
    v-if="gameOver"
    :score="score"
    :questions="this.questions.length"
    @new-game="start"
  />
</template>

<script>
import ConfigGame from './components/ConfigGame.vue'
import Question from './components/Question.vue'
import Results from "./components/Results.vue";
//import axios from 'axios'

export default {
  name: 'Quiz',
  components: {
    ConfigGame,
    Question,
    Results
  },
  data() {
    return {
      isConfig: false,
      gameOver: false,
      questions: {},
      currentQuestion: {},
      counterQuestions: 0,
      score: 0
    }
  },
  watch: {
    counterQuestions() {
      if(this.counterQuestions == this.questions.length){
        this.gameOver = true;
      }
    }
  },
  methods: {

    async fetchQuestions(config) { 
      const url = `https://opentdb.com/api.php?amount=${config.numQuestions}&category=${config.category}&difficulty=${config.difficulty}&type=multiple`;
      fetch(url)
      .then(res => res.json())
      .then(data => {
        console.log(data);
        this.questions = data.results
        this.isConfig = true
        this.currentQuestion = this.questions[this.counterQuestions]
      })

    },
    nextAnswer(answer) {
      if(answer) {
        this.score++
      } 
      this.counterQuestions++
      this.currentQuestion = this.questions[this.counterQuestions]
    },
    start() {
      this.isConfig = false
      this.gameOver = false
      this.questions = {}
      this.currentQuestion = {}
      this.counterQuestions = 0
      this.score = 0
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
