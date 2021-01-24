<template>
    <div class="question_box_container">
        <b-jumbotron>
            
            <template #lead>
              {{ currentQuestion.question }}
            </template>

            <hr class="my-4">
            <b-list-group>
                <b-list-group-item
                  v-for="(answer, index) in answers"
                  :key="index"
                  @click="selectAnswer(index)"
                  :class="[selectedIndex === index ? 'selected' : '' ]"
                >
                  {{ answer }}
                </b-list-group-item>
            </b-list-group>
            <b-button variant="primary" href="#">Submit</b-button>
            <b-button @click="next" variant="success" href="#">next</b-button>
        </b-jumbotron>
    </div>
</template>

<script>
export default {
    name: 'QuestionBox',
    props: {
      currentQuestion: Object,
      next: Function
    },
    data() {
      return {
          selectedIndex: null,
      }
    },
    computed: {
      answers() {
        let answers = [...this.currentQuestion.incorrect_answers]
        answers.push(this.currentQuestion.correct_answer)
        return answers;
      }
    },
    methods: {
      selectAnswer(index) {
        this.selectedIndex = index
      }
    },
    mounted() {
      console.log(this.currentQuestion)
    }
}
</script>

<style scoped>
    .list-group {
      margin-bottom: 0.8rem;
    }
    .list-group-item:hover {
      background-color: #eeeeee;
      cursor: pointer;
    }
    .btn {
      margin: 0 0.5rem;
    }
    .selected {
      background-color: lightblue;
    }
    .correct {
      background-color: lightgreen;
    }
    .incorrect {
      background-color: red;
    }
</style>