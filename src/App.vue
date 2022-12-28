<template>
  <div class="text-center">
    <h3 class="title mt-5">How Fast Can U Catch Me?</h3>
    <button @click="start" class="btn btn-secondary mt-2" :disabled="isPlaying">Play</button>
  </div>
  <p v-if="showText" class="text-muted text-center mt-3">
    After you press the play button, a box will appear after a few seconds. <br> Click that box and start playing the Game.
  </p>
  <Block v-if="isPlaying" @ended="ended" :waitingTime="waitingTime"/>
  <Result v-if="showResult" :result="result"/>
</template>

<script>
import Block from './components/Block.vue';
import Result from './components/Result.vue';

  export default {
    data() {
      return {
        isPlaying: false,
        waitingTime : null,
        result : 0,
        showResult : false,
        showText : true
      }
    },
    methods: {
      start() {
        this.isPlaying = true;
        this.showText = false;
        this.waitingTime = Math.floor(Math.random()*4000)+2000;
      },
      ended(score) {
        this.isPlaying = false;
        this.result = score;
        this.showResult = true;
      },
    },
    components: {
      Block,
      Result,
    },
  }
</script>

<style>
@import '../node_modules/bootstrap/dist/css/bootstrap.min.css';
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap');

body{
  font-family: 'Roboto', sans-serif;
}

.title{
  text-align: center;
  letter-spacing: 1px;
  text-transform: uppercase;
  color: brown;
}
</style>
