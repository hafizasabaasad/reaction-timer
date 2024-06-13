<template>
  <h1>Welcome to Single Page Application Demo</h1>
  <h2>Title: Ninja Reaction Timer</h2>
  
  <description />
  <button @click="start" :disabled="isPlaying">Play</button>
  <block v-if="isPlaying" :delay="delay" @end="endgame" />
  <result v-if="showResults" :score="score" />
</template>

<script>
import description from "./components/description.vue";
import block from "./components/block.vue";
import result from "./components/result.vue";
export default {
  name: "App",
  components: { block, result, description },
  data() {
    return {
      isPlaying: false,
      dalay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 1000 + Math.random() * 3000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endgame(reactiontime) {
      this.score = reactiontime;
      this.isPlaying = false;
      this.showResults = true;
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
  color: #396999;
  margin-top: 60px;
}
button {
  background: #d84636;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
