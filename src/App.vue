<template>
    <Header :gameTitle="gameTitle" :gameDescription="gameDescription" />
    <button @click="start" class="startButton"> Start </button>
    <Result v-if="isEndGame" :message="message" :isSuccess="isSuccess" />
    <Canvas v-if="isPlaying" :delay="delay" @end="endGame" />
</template>

<script>
  import Header from './components/Header.vue';
  import Canvas from './components/Canvas.vue';
  import Result from './components/Result.vue';

  export default {
    name: 'App',
    components: { Header, Canvas, Result },
    data() {
      return {
        gameTitle: "Ravenz Reaction Time",
        gameDescription: "How fast are you ?",
        delay: null,
        isPlaying: false,
        isEndGame: false,
        isSuccess: false,
        message: null,
      }
    },
    methods: {
      start() {
        this.isPlaying = true;
        this.delay = 2000 + Math.random() * 5000;
        this.isSuccess = false;
        this.isPlaying = true;
        this.isEndGame = false;
      },
      endGame(event) {
        this.isPlaying = false;
        this.isEndGame = true;

        if(event) {
          this.message = `Your Response Time is: ${event}ms`;
          this.isSuccess = true;
        } else {
          this.message = `Missed - Try Again`;
          this.isSuccess = false;
        }
      }
    }
  } 

</script>

<style scoped>
  .startButton {
    margin-top: 1rem;
    outline: unset;
    border: unset;
    background-color: #29AB87;
    color: #fff;
    padding: 1rem 2rem;
    cursor: pointer;
    transition: 0.2s;
    border-radius: 5px;
    font-size: 14px;
    font-weight: 600;
    text-transform: uppercase;
  }

  .startButton:hover {
    background-color: #239172;
    transition: 0.2s;
  }

  .outPutMessage {
    margin-top: 3rem;
    color: #ff4b4b;
  }

  .outPutMessage.success {
    color: #29AB87;
  }
</style>


