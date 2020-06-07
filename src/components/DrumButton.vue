<template>
  <div class="drum-button" @click="logClick">DrumButton</div>
</template>

<script>
import testSample from "../assets/test-sample.wav";
export default {
  name: "DrumButton",
  methods: {
    logClick(e) {
      console.log("log click", e);
      var audio = new Audio(testSample);
      audio.play();
    }
  }
};
</script>

<style lang="scss" scoped>
.drum-button {
  height: 200px;
  width: 200px;
  border: solid 1px black;
}
</style>
