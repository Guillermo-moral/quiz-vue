<template>
  <h1>Quiz App</h1>
  <ConfigGame v-if="isConfig" @config-submitted="fetchQuestions" />
  <Question
    v-if="!isConfig"
    :questions="questions"
  />
</template>

<script>
import ConfigGame from './components/ConfigGame.vue'
import Question from './components/Question.vue';
import axios from 'axios'
export default {
  name: 'Quiz',
  components: {
    ConfigGame,
    Question
  },
  data() {
    return {
      isConfig: true,
      questions: {},
    }
  },
  methods: {
    fetchQuestions(config) {
      let url = `https://opentdb.com/api.php?amount=${config.numQuestions}&category=${config.category}&difficulty=${config.difficulty}&type=multiple`;
      axios.get(url).then(res => {
        this.questions = res.data.results
        console.log(this.questions);
        this.isConfig = false
        })
      // fetch(url)
      //   .then(res => res.json())
      //   .then(data => {
      //     this.questions.results = data;
      //     this.isConfig = false;
      //     console.log(data.results[0].category);
      //     console.log(this.questions);
      //   })
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
