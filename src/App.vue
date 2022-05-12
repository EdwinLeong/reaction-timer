<template>
  <h1>Reaction Timer</h1>
  <p>Testing.....</p>
  <button @click="onClick" :disabled="isPlaying">play</button>
  <!-- <button @click="onClickTesting('hello world')">Tetsing</button> -->
  <DisplayCard v-if="isPlaying" :delay="delay" @endTime="endGame" />
  <FinalResults v-if="isDisplayScore" :score="score" />
</template>

<script>
import DisplayCard from "./components/DisplayCard.vue";
import FinalResults from "./components/FinalResults.vue";
export default {
  name: "App",
  components: {
    DisplayCard,
    FinalResults,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      isDisplayScore: false,
    };
  },
  methods: {
    // onClickTesting(e) {
    //   console.log("the e", e);
    // },

    onClick() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.isDisplayScore = false;
      console.log("the delay", this.delay);
    },

    endGame(e) {
      this.score = e;
      this.isDisplayScore = true;
      this.isPlaying = false;
      console.log("the value of e", e);
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
  color: #444;
  margin-top: 60px;
}
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
  font-weight: bold;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
