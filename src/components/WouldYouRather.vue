<template>
  <div class="wyr">

    <h2>Would you rather...</h2>

    <!-- question from object array -->
    <h3>{{ questionsData.question }}</h3>

    <!-- v-on:change to call method (choiceMade) -->
    <input type="radio" v-model="answerSelected" 
                        v-bind:value="questionsData.answer1" 
                        v-on:change="choiceMade"> 
    
    <!-- display answer1 from object array -->
    <label>{{ questionsData.answer1 }}</label>
    
    <!-- v-on:change to call method (choiceMade) -->
    <input type="radio" v-model="answerSelected" 
                        v-bind:value="questionsData.answer2" 
                        v-on:change="choiceMade"> 
    
    <!-- display answer2 from object array -->
    <label>{{ questionsData.answer2 }}</label>

  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  props: {
    questionsData: Object,
  },
  data() {
    return {
      answerSelected: ''
    }
  },
  methods: {
    choiceMade() {
      // emit an event called 'answer-changed' and inculde the vale of the data "choice"
      this.$emit('answer-changed', this.answerSelected)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

.wyr {
  border: 1px rgb(0, 0, 0) solid;
  background: rgb(255, 205, 205);
  margin: 5px;
}

</style>
