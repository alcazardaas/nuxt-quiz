<template>
  <div class="wrapper" ref="wrapper">
    <header>
      <img src="../static/waves.svg" class="background">
      <img src="../static/bubble.svg" class="foreground">
      <h1 class="title">
        {{ title }}
      </h1>
    </header>
    <form-questions @form-submitted="scrollToTop" />
  </div>
</template>

<script>
import { defineComponent } from 'vue';
import FormQuestions from '../components/FormQuestions.vue';

export default defineComponent({
  name: 'App',
  components: {
    FormQuestions,
  },
  data() {
    return {
      title: 'Quiz App',
    };
  },
  methods: {
    scrollToTop() {
      this.$refs.wrapper.scrollTo({
        top: 0,
        behavior: 'smooth'
      })
    }
  }
});
</script>

<style lang="less">
body {
  margin: 0;
}

html {
  background: #ccc;
}

#__nuxt {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #0012FF;

  .wrapper {
    height: 100vh;
    overflow-y: auto;
    overflow-x: hidden;
    perspective: 10px;

    header {
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100%;
      transform-style: preserve-3d;
      z-index: -1;

      .background,
      .foreground {
        position: absolute;
        width: 100%;
        height: 100%;
        object-fit: cover;
        z-index: -1;
      }

      .background {
        transform: translateZ(-10px) scale(2);
      }

      .foreground {
        opacity: 0.9;
        height: 319px;
        width: 322px;
        transform: translateZ(-5px) scale(1.5);

        @media screen and (min-width: 768px) {
          height: 623px;
          width: 677px;
        }

        @media screen and (min-width: 1200px) {
          height: 835px;
          width: 847px;
        }
      }
    }

    .title {
      font-size: 3rem;
      color: #fff;
      text-shadow: 0 0 5px #000;

      @media screen and (min-width: 768px) {
        font-size: 7rem;
      }
    }
  }
}
</style>
