<template>
  <div class="drum-button" @click="logClick">
    <div class="drum-button__key">
      <span>{{ sample.key }}</span>
    </div>
  </div>
</template>

<script>
const keyDown = (eventKeyCode, sample) => {
  const audio = new Audio(sample.sample);
  audio.pause();
  audio.play();
};

export default {
  name: "DrumButton",
  props: ["sample", "keyDown"],

  created() {
    this.addEventListener(this.sample);
  },
  methods: {
    addEventListener(sample) {
      window.addEventListener("keydown", function(event) {
        if (sample.keyCode === event.keyCode) {
          keyDown(event.keyCode, sample);
        }
      });
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
