<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    CLICK ME as fast as you can to check your reflexes!
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactiontime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactiontime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactiontime);
    },
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #4c067b;
  color: white;
  padding: 100px 0;
  margin: 40px auto;
  text-align: center;
}
</style>
