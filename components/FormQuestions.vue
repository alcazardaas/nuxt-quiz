<template>
  <div>
    <loader-component v-if="questions.length === 0" :isCentered='true'/>
    <form v-else>
      <question-template :questions="questions" :scrollTop="scrollWrapper" />
    </form>
  </div>
</template>

<script>
import QuestionTemplate from './QuestionTemplate.vue';
import LoaderComponent from './LoaderComponent.vue'

export default {
  components: {
    QuestionTemplate,
    LoaderComponent
  },
  data() {
    return {
      questions: [],
    };
  },
  async created() {
    try {
      const response = await this.$axios.get('http://localhost:3001/questions');
      this.questions = response.data;
    } catch (error) {
      console.error(error);
    }
  },
  methods: {
    scrollWrapper() {
      this.$emit('form-submitted')
    }
  }
};
</script>
