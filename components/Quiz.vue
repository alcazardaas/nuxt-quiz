<template>
  <div>
    <Question v-for="(question, index) in questions" :key="index" :question="question" v-model="selectedAnswers[index]" />
    <button @click="submit">Submit</button>
  </div>
</template>

<script>
import axios from 'axios';
import Question from './Question.vue';

export default {
  components: {
    Question
  },
  data() {
    return {
      questions: [],
      selectedAnswers: []
    };
  },
  created() {
    axios.get('http://localhost:3001/question')
      .then(response => {
        this.questions = response.data;
        this.selectedAnswers = Array(this.questions.length).fill(null);
      })
      .catch(error => {
        console.log(error);
      });
  },
  methods: {
    submit() {
      // handle form submission here
      console.log('Selected answers:', this.selectedAnswers);
    }
  }
};
</script>
