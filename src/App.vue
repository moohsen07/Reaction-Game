<template>
  <h1>Reaction Game Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Result v-if="showResult" :score="score" />
</template>

<script>
import Block from "./components/Block";
import Result from "./components/Result";

export default {
  name: "App",
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResult = false;
    },
    endGame(reaction) {
      this.score = reaction;
      this.isPlaying = false;
      this.showResult = true;
    },
  },
};
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
button {
  padding: 10px 40px;
  background-color: #07ad;
  border: none;
  border-radius: 10px;
  color: #fff;
  font-size: 17px;
  text-transform: uppercase;
  cursor: pointer;
}
button[disabled] {
  cursor: not-allowed;
  background-color: rgba(0, 119, 170, 0.404);
}
</style>
