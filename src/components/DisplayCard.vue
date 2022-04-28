<template>
  <!-- When using methods function to call can/can't to put the () -->
  <!-- () is to pass data to the methods fucntion to call -->
  <div class="dialog" v-if="isShow" @click="stopTimer()">PRESS NOW</div>
</template>

<script>
export default {
  name: "DisplayCard",
  props: ["delay"],
  data() {
    return {
      isShow: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    console.log("First Mounted");
    setTimeout(() => {
      this.isShow = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
      console.log("the Timer", this.timer);
    },

    stopTimer() {
      clearInterval(this.timer);
      this.$emit("endTime", this.reactionTime);
      console.log("the reactionTime", this.reactionTime);
    },
  },
  // updated() {
  //   console.log("Update value");
  // },
  // unmounted() {
  //   console.log("UnMounted");
  // },
};
</script>

<style>
.dialog {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
  font-size: 30px;
  font-weight: 600;
}
</style>
