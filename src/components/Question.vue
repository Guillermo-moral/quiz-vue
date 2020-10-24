<template>
  <div class="question">
    <div class="categoria">
      <p>{{ question.category }}</p>
    </div>
    <h2 class="pregunta">{{ question.question }}</h2>
    <div class="respuestas">
      <div class="respuesta" v-for="(answer, index) in answers" :key="index">
        <input type="radio" name="respuesta" value="1" id="respuesta-1">
        <label for="respuesta-1">{{ answer }}</label>
      </div>
      <button @click="submitAnswer">Submit</button>
    </div>
    <div class="control-preguntas">

    </div>
  </div>
</template>

<script>
export default {
  name:'Question',
  props: {
    question: Object,
  },
  data() {
    return {}
  },
  computed: {
    answers() {
      return this.question.incorrect_answers.concat(this.question.correct_answer)
    }
  },
  methods: {
    submitAnswer() {
      this.$emit('answer-submitted')
      console.log('submitAnswer');
    }
  }
  
}
</script>

<style scoped>
.question {
  max-width: 600px;
  background-color: #fff;
  margin: 50px;
  border-radius: 10px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.4);
}

.categoria {
  background-color: #feb60a;
  padding: 10px 30px;
  border-radius: 10px 10px 0 0;
}

.pregunta {
  font-weight: 400;
  margin: 20px 30px;
  padding-bottom: 20px;
  border-bottom: 1px solid #1a1940;
}

.respuestas {
  font-family: 'Josefin Sans', sans-serif;
  font-weight: 300;
  margin: 30px;
}

.respuesta {
  font-size: 1.2rem;
  margin-top: 20px;
}

.control-preguntas {
  height: 10px;
  border-radius: 20px;
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  margin: 10px;
}

.control-preguntas div {
  background-color: #ccc;
  border-right: 2px solid #fff;
  border-top: 2px solid #fff;
}

.control-preguntas div.selec {
  background-color: #da00f7;
}
</style>