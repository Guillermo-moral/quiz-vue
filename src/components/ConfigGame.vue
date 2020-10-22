<template>
  <form class="configuracion" @submit.prevent="onSubmit">
    <label for="dificultad">Difficulty</label>
    <select name="dificultad" v-model="config.difficulty">
      <option value="" selected>Select difficulty</option>
      <option v-for="(item, index) in difficulty" :key="index">{{ item.content }}</option>
    </select>

    <label for="numQuestions">Number of questions</label>
    <select name="numQuestions" v-model="config.numQuestions">
      <option value="" selected>Select questions</option>
      <option v-for="(item, index) in numQuestions" :key="index">{{ item }}</option>
    </select>

    <label for="category">Category</label>
    <select name="category" v-model="config.category">
      <option
        v-for="(category, index) in categories"
        :key="index"
        :value="category.value">
        {{ category.category }}
      </option>
    </select>
    <button>Let's play!</button>
  </form>
</template>

<script>
export default {
  name: 'ConfigGame',
  data(){
    return {
      config: {
        difficulty: '',
        numQuestions: '',
        category:''
      },
      difficulty: [
        { value: '', content: 'Any' },
        { value: 'easy', content: 'Easy' },
        { value: 'medium', content: 'Medium' },
        { value: 'hard', content: 'Hard' },
      ],
      numQuestions: [5, 10, 15],
      categories: [
        { value: '', category: 'Any Category'},
        { value:'9', category: 'General Knowledge'},
        { value:'10', category: 'Entertainment: Books'},
        { value:'11', category: 'Entertainment: Film'},
        { value:'12', category: 'Entertainment: Music'},
        { value:'13', category: 'Entertainment: Musicals &amp; Theatre'},
        { value:'14', category: 'Entertainment: Television'},
        { value:'15', category: 'Entertainment: Video Games'},
        { value:'16', category: 'Entertainment: Board Games'},
        { value:'17', category: 'Science & Nature'},
        { value:'18', category: 'Science: Computers'},
        { value:'19', category: 'Science: Mathematics'},
        { value:'20', category: 'Mythology'},
        { value:'21', category: 'Sports'},
        { value:'22', category: 'Geography'},
        { value:'23', category: 'History'},
        { value:'24', category: 'Politics'},
        { value:'25', category: 'Art'},
        { value:'26', category: 'Celebrities'},
        { value:'27', category: 'Animals'},
        { value:'28', category: 'Vehicles'},
        { value:'29', category: 'Entertainment: Comics'},
        { value:'30', category: 'Science: Gadgets'},
        { value:'31', category: 'Entertainment: Japanese Anime & Manga'},
        { value:'32', category: 'Entertainment: Cartoon & Animations'}
      ]
    }
  },
  methods: {
    onSubmit() {
      let config = {
        difficulty: this.config.difficulty.toLowerCase(),
        numQuestions: this.config.numQuestions,
        category:this.config.category
      }
      this.$emit('config-submitted', config)
    }
  }
}
</script>

<style scoped>

  .configuracion {
    width: 500px;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding: 30px;
    border: 1px solid #ddd;
  }

  .configuracion select {
    margin-bottom: 10px;
  }

</style>
