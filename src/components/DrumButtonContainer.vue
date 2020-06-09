<template>
  <div class="drum-button-container">
    <fragment v-for="(sample, index) in sampleArray" :key="index">
      <DrumButton :sample="sample" :isToggled="isToggled" />
    </fragment>
  </div>
</template>

<script>
import { Fragment } from "vue-fragment";
import DrumButton from "./DrumButton";
import kick1 from "../assets/samples/kick1.wav";
import snare1 from "../assets/samples/snare1.wav";
import snare2 from "../assets/samples/snare2.wav";
import closedHat from "../assets/samples/closedHat.wav";
import openHat from "../assets/samples/openHat.wav";
import clap from "../assets/samples/clap.wav";
import snap from "../assets/samples/snap.wav";
import distortBass from "../assets/samples/distortBass.wav";

// *Used to loop through and populate DrumButton components
const sampleArray = [
  {
    keyCode: 65,
    sample: kick1,
    key: "A",
  },
  {
    keyCode: 83,
    sample: snare1,
    key: "S",
  },
  {
    keyCode: 68,
    sample: snare2,
    key: "D",
  },
  {
    keyCode: 70,
    sample: closedHat,
    key: "F",
  },
  {
    keyCode: 71,
    sample: openHat,
    key: "G",
  },
  {
    keyCode: 72,
    sample: clap,
    key: "H",
  },
  {
    keyCode: 74,
    sample: snap,
    key: "J",
  },
  {
    keyCode: 75,
    sample: distortBass,
    key: "K",
  },
];

export default {
  name: "DrumButtonContainer",
  components: { DrumButton },
  props: ["isToggled"],
  data() {
    return {
      sampleArray,
    };
  },
  methods: {},
};
</script>

<style lang="scss" scoped>
@import "../scss/index.scss";
.drum-button-container {
  background-color: $main-black;
  position: initial;
  padding: 1rem;
  display: grid;
  grid-template-columns: repeat(2, auto);
  grid-template-rows: repeat(4, auto);

  justify-items: center;

  @include md {
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(2, auto);
    row-gap: 1rem;
    align-self: center;
  }

  @include lg {
    background-color: none;
    padding: 0;
    height: 305px;
    width: 636px;
    position: absolute;
    z-index: 4;
    top: 22%;
    left: 21%;
    justify-self: center;
  }
}
</style>
