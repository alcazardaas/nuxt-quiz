<template>
  <div>
    <h2>{{ question.text }}</h2>
    <ul>
      <li v-for="(answer, index) in question.answers" :key="index">
        <label>
          <input type="radio" :value="index" v-model="selectedAnswer" />
          {{ answer.text }}
        </label>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    question: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      selectedAnswer: null
    };
  },
  watch: {
    selectedAnswer() {
      this.$emit('input', this.selectedAnswer);
    }
  }
};
</script>
