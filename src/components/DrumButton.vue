<template>
  <div class="drum-button" @click="logClick">
    <div class="drum-button__key">
      <span>{{ sample.key }}</span>
    </div>
  </div>
</template>

<script>
// const keyDown = (eventKeyCode, sample) => {
//   if (sample.keyCode === event.keyCode) {
//     const audio = new Audio(sample.sample);
//     audio.pause();
//     audio.play();
//   }
// };
// const keyUp = (event) => {
//   console.log("keyup");
// };

export default {
  name: "DrumButton",
  props: ["sample"],
  data() {
    return {
      isKeyPressed: false,
    };
  },
  created() {
    this.addEventListener("keydown", this.keyDown, this.sample);
    this.addEventListener("keyup", this.keyUp, this.sample);
  },
  methods: {
    addEventListener(eventType, callback, sample) {
      window.addEventListener(eventType, function(event) {
        callback(event.keyCode, sample);
      });
    },
    keyDown(eventKeyCode, sample) {
      if (sample.keyCode === event.keyCode) {
        this.isKeyPressed = true;
        console.log("this.isKeyPressed", this.isKeyPressed);
        const audio = new Audio(sample.sample);
        audio.pause();
        audio.play();
      }
    },
    keyUp(event) {
      this.isKeyPressed = false;
      console.log("this.isKeyPressed", this.isKeyPressed);
    },

    logClick(e) {
      var audio = new Audio(this.sample.sample);
      audio.play();
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/index.scss";
.drum-button {
  height: 200px;
  width: 200px;
  border: solid 10px $button-border-grey;
}
</style>
