<template>
  <div v-if="showBlock" @click="clicked" class="block">Click Me!</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
    clicked() {
      this.showBlock = false;
      this.stopTimer();
    },
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
};
</script>

<style>
.block {
  width: 100px;
  border-radius: 20px;
  padding: 2rem;
  margin: 40px auto;
  border: 2px solid black;
}
</style>
