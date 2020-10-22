<template>
  <form class="configuracion">
    <label for="dificultad">Difficulty</label>
    <select name="dificultad">
      <option value="" selected>Cualquiera</option>
      <option value="easy" >Facil</option>
      <option value="medium">Normal</option>
      <option value="hard">Dificil</option>
    </select>

    <label for="numPreguntas">Number of questions</label>
    <select name="numPreguntas">
      <option value="5" selected>5</option>
      <option value="10">10</option>
      <option value="15">15</option>
    </select>

    <label for="categorias">Category</label>
    <select name="categorias">
      <option value="" selected>Any Category</option>
      <option value="9">General Knowledge</option>
      <option value="10">Entertainment: Books</option>
      <option value="11">Entertainment: Film</option>
      <option value="12">Entertainment: Music</option>
      <option value="13">Entertainment: Musicals &amp; Theatres</option>
      <option value="14">Entertainment: Television</option>
      <option value="15">Entertainment: Video Games</option>
      <option value="16">Entertainment: Board Games</option>
      <option value="17">Science & Nature</option>
      <option value="18">Science: Computers</option>
      <option value="19">Science: Mathematics</option>
      <option value="20">Mythology</option>
      <option value="21">Sports</option>
      <option value="22">Geography</option>
      <option value="23">History</option>
      <option value="24">Politics</option>
      <option value="25">Art</option>
      <option value="26">Celebrities</option>
      <option value="27">Animals</option>
      <option value="28">Vehicles</option>
      <option value="29">Entertainment: Comics</option>
      <option value="30">Science: Gadgets</option>
      <option value="31">Entertainment: Japanese Anime & Manga</option>
      <option value="32">Entertainment: Cartoon & Animations</option>
    </select>
    <button>Let's play!</button>
  </form>
</template>

<script>
export default {
  name: 'ConfigGame',
}
</script>

<style>
.configuracion {
  width: 500px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 30px 30px 0;
  border: 1px solid #ddd;
}

.configuracion select {
  margin-bottom: 10px;
}
</style>