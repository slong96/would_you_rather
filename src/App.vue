<template>
  <div id="app"> 

    <h1>Welcome to Would You Rather</h1>
    <!-- -->
    <!-- v-on:answer-changed - calls "answerChanged" method when answer-change event happens -->
    <WouldYouRather v-for="wyrQuestion in questions" v-bind:key="wyrQuestion"
                    v-bind:questionsData="wyrQuestion"
                    v-on:answer-changed="answerChanged">
    </WouldYouRather>

    <h4>You would rather be a...</h4>
    <ul>
      <li v-for="answer1 in answerList1" v-bind:key="answer1"> {{answer1}} </li>
      <li v-for="answer2 in answerList2" v-bind:key="answer2"> {{answer2}} </li>
      <li v-for="answer3 in answerList3" v-bind:key="answer3"> {{answer3}} </li>
    </ul>

  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
      questions: [
        {
          id: 0,
          question: 'be a famous inventor or a famous writer?',
          answer1: 'Famous Inventor',
          answer2: 'Famous Writer'
        },
        {
          id: 1,
          question: 'be a wizard or a superhero?',
          answer1: 'Wizard',
          answer2: 'Superhero',
        },
        {
          id: 2,
          question: 'be a detective or a pilot?',
          answer1: 'Detective',
          answer2: 'Pilot',
        }
      ],
      // array list for each question answers
      answerList1: [],
      answerList2: [],
      answerList3: []
    }
  },
  methods: {
    answerChanged(answerSelected) {
      // push answers to array list for question 1
      if (answerSelected == this.questions[0].answer1) {
        this.answerList1.pop(answerSelected)
        this.answerList1.push(answerSelected)
      } else if (answerSelected == this.questions[0].answer2) {
        this.answerList1.pop(answerSelected)
        this.answerList1.push(answerSelected)
      }
      // push answers to array list for question 2
      if (answerSelected == this.questions[1].answer1) {
        this.answerList2.pop(answerSelected)
        this.answerList2.push(answerSelected)
      } else if (answerSelected === this.questions[1].answer2) {
        this.answerList2.pop(answerSelected)
        this.answerList2.push(answerSelected)
      }
      // push answers to array list for question 3
      if (answerSelected == this.questions[2].answer1) {
        this.answerList3.pop(answerSelected)
        this.answerList3.push(answerSelected)
      } else if (answerSelected == this.questions[2].answer2) {
        this.answerList3.pop(answerSelected)
        this.answerList3.push(answerSelected)
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
  margin-top: 60px;
}

#app li {
  list-style: none;
  font-size: 24px;
  font-weight: bold;
  background: yellow;
  margin: 5px;
}
</style>
