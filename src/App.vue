<template>
  <div id="app">
    <Header
        :numCorrect="numCorrect"
        :numTotal="numTotal"
    />
    <b-container>
      <b-row>
        <b-col sm="12" align-v="center">
          <QuestionBox
            v-if="questions.length"
            :currentQuestion="questions[index]"
            :next="next"
            :increment="increment"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from './components/Header';
import QuestionBox from './components/QuestionBox';

export default {
  name: 'App',
  components: {
    Header,
    QuestionBox
  },
  data() {
    return {
      questions: [],
      index: 0,
      numCorrect: 0,
      numTotal: 0,
    }
  },
  methods: {
    next() {
      this.index++
    },
    increment(isCorrect) {
      if(isCorrect) {
          this.numCorrect++
      }
        this.numTotal++
    }
  },
  mounted: function () {
    fetch("https://opentdb.com/api.php?amount=10&category=10&type=multiple", {
      method: "get"
    })
    .then((response) => {
      if(response.ok) {
        return response.json();
      } else {
        return Promise.reject(response);
      }
    })
    .then((jsonData) => {
        this.questions = jsonData.results;
        console.log(this.questions)
    })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
