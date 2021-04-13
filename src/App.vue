<template>
  <h1>{{ title }}</h1>
  <button @click="startPlay" :disabled="isPlay">Play</button>
  <Block v-if="isPlay" :delay="delayShow" @end="endGame" />
  <Result v-if="showResult" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  data() {
    return {
      title: "Reaction Timer",
      isPlay: false,
      delayShow: null,
      showResult: false,
      score: null,
    };
  },
  components: {
    Block,
    Result,
  },
  methods: {
    startPlay() {
      this.isPlay = true;
      this.showResult = false;
      this.delayShow = 2000 + Math.random() * 5000;
    },
    endGame(reactionTime) {
      this.showResult = true;
      this.score = reactionTime;
      this.isPlay = false;
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
</style>
