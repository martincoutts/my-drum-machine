<template>
  <div
    class="drum-button"
    :class="{ 'drum-button--selected': this.isKeyPressed }"
    @mousedown="mouseDown"
    @mouseup="mouseUp"
  >
    <div v-if="!this.isToggled" class="drum-button__key">
      <span>{{ sample.key }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "DrumButton",
  props: ["sample", "isToggled"],
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
  background-color: $button-black;
  border: solid 10px $button-border-grey;
  height: 140px;
  width: 140px;

  @include md {
    height: 160px;
    width: 160px;
  }
  @include lg {
    height: 130px;
    width: 130px;
  }

  &--selected {
    border: solid 10px $pad-border-color;
  }

  &__key {
    color: $drum-button-font-color;
    font-family: $font-primary;
    font-size: $drum-button-font-size;
    padding: 0.5rem;
  }
}
</style>
