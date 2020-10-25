<template>
  <div class="question">
    <div class="categoria">
      <p>{{ question.category }}</p>
    </div>
    <h2 class="pregunta">{{ question.question }}</h2>
    <div class="respuestas">
      <div class="respuesta" v-for="(answer, index) in answers" :key="index">
        <input type="radio" name="respuesta"
          :value="answer"
          :id="index"
          v-model="selected">
        <label
          :for="index">
          {{ answer }}
        </label>
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
    return {
      selected: ''
    }
  },
  computed: {
    answers() {
      const answers = this.question.incorrect_answers.concat(this.question.correct_answer)
      return answers.sort(() => Math.random() - 0.5);
    },
  },
  methods: {
    submitAnswer() {
      if(this.selected == this.question.correct_answer){
        this.$emit('answer-submitted', true)
        console.log('correcto');
      } else {
        this.$emit('answer-submitted', false)
        console.log('incorrecto');
      }
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