<template>
  <form class="configuracion" @submit.prevent="onSubmit">
    <label for="dificultad">Difficulty</label>
    <select name="dificultad" v-model="config.difficulty">
      <option
        v-for="(item, index) in difficulty"
        :key="index"
        :value="item.value">
        {{ item.content }}
      </option>
    </select>

    <label for="numQuestions">Number of questions</label>
    <select name="numQuestions" v-model="config.numQuestions">
      <option
        v-for="(item, index) in numQuestions"
        :key="index"
        :value="item.value">
        {{ item.content }}
      </option>
    </select>

    <label for="category">Category</label>
    <select name="category" v-model="config.category">
      <option
        v-for="(category, index) in categories"
        :key="index"
        :value="category.value">
        {{ category.content }}
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
        { value: '', content: 'Select difficulty' },
        { value: 'easy', content: 'Easy' },
        { value: 'medium', content: 'Medium' },
        { value: 'hard', content: 'Hard' },
      ],
      numQuestions: [
        { value: '', content: 'Select questions' },
        { value: 5, content: '5' },
        { value: 10, content: '10' },
        { value: 15, content: '15' },
      ],
      categories: [
        { value: '', content: 'Any Category'},
        { value:'9', content: 'General Knowledge'},
        { value:'10', content: 'Entertainment: Books'},
        { value:'11', content: 'Entertainment: Film'},
        { value:'12', content: 'Entertainment: Music'},
        { value:'13', content: 'Entertainment: Musicals &amp; Theatre'},
        { value:'14', content: 'Entertainment: Television'},
        { value:'15', content: 'Entertainment: Video Games'},
        { value:'16', content: 'Entertainment: Board Games'},
        { value:'17', content: 'Science & Nature'},
        { value:'18', content: 'Science: Computers'},
        { value:'19', content: 'Science: Mathematics'},
        { value:'20', content: 'Mythology'},
        { value:'21', content: 'Sports'},
        { value:'22', content: 'Geography'},
        { value:'23', content: 'History'},
        { value:'24', content: 'Politics'},
        { value:'25', content: 'Art'},
        { value:'26', content: 'Celebrities'},
        { value:'27', content: 'Animals'},
        { value:'28', content: 'Vehicles'},
        { value:'29', content: 'Entertainment: Comics'},
        { value:'30', content: 'Science: Gadgets'},
        { value:'31', content: 'Entertainment: Japanese Anime & Manga'},
        { value:'32', content: 'Entertainment: Cartoon & Animations'}
      ]
    }
  },
  methods: {
    onSubmit() {
      if(this.config.numQuestions == '') {
        this.config.numQuestions = 5
      }
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
