<template>
  <div
    class="drum-button"
    :class="{ 'drum-button--selected': this.isKeyPressed }"
    @mousedown="mouseDown"
    @mouseup="mouseUp"
  >
    <div class="drum-button__key">
      <span>{{ sample.key }}</span>
    </div>
  </div>
</template>

<script>
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
        // *Stops event firing infinite times if key is held down, issue on IE
        const repeat = event.repeat;

        repeat === false ? callback(event.keyCode, sample) : null;
      });
    },
    keyDown(eventKeyCode, sample) {
      if (sample.keyCode === event.keyCode) {
        this.isKeyPressed = true;
        const audio = new Audio(sample.sample);
        audio.pause();
        audio.play();
      }
    },
    keyUp(event) {
      this.isKeyPressed = false;
    },

    mouseDown(e) {
      console.log("click", e);
      this.isKeyPressed = true;

      const audio = new Audio(this.sample.sample);
      audio.pause();
      audio.play();
    },
    mouseUp(e) {
      this.isKeyPressed = false;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/index.scss";
.drum-button {
  height: 200px;
  width: 200px;
  background-color: $button-black;
  border: solid 10px $button-border-grey;

  &--selected {
    border: solid 10px $button-border-selected-red;
  }
}
</style>
