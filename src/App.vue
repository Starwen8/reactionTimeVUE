<template>
  <h1>Reaction timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <BlockBox v-if="isPlaying" :delay="delay" @end="endGame" />
  <Result v-if="showResult" :score="score" />
</template>

<script>
import BlockBox from "./components/BlockBox.vue";
import Result from "./components/Result.vue";
export default {
  name: "App",
  components: { BlockBox, Result },
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
      this.delay = 2000 + Math.random() * 3000;
      this.isPlaying = true;
      console.log(this.delay);
      this.showResult = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
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
</style>
