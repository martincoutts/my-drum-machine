<template>
  <div class="drum-button" @click="logClick"></div>
</template>

<script>
export default {
  name: "DrumButton",
  props: ["sample"],

  created() {
    this.addEventListener();
  },
  methods: {
    addEventListener() {
      window.addEventListener("keyup", function(event) {
        console.log("event");
      });
    },

    logClick(e) {
      var audio = new Audio(this.sample.sample);
      audio.play();
    },
    keyDown(e) {
      if (event.keyCode === 65) {
        var audio = new Audio(this.sample.sample);
        audio.play();
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.drum-button {
  height: 200px;
  width: 200px;
  border: solid 1px black;
}
</style>
