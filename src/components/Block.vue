<template>
  <div class="block" v-if="blockShow" @click="stopTimer">click me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      blockShow: false,
      timer: null,
      reaction: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.blockShow = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reaction += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reaction);
    },
  },
};
</script>

<style scoped>
.block {
  width: 400px;
  padding: 100px 0;
  background-color: #07ad;
  color: #fff;
  margin: 40px auto;
  text-align: center;
  border-radius: 20px;
}
</style>