<template>
  <div class="lpd-template">
    <img
      src="../assets/images/LPDComponentNoTemplate.svg"
      class="lpd-template__image"
    />
    <DrumButtonContainer />
  </div>
</template>

<script>
// import LPDImage from '../assets/images/'
import DrumButtonContainer from "./DrumButtonContainer";
export default {
  name: "LPDTemplate",
  components: { DrumButtonContainer },
};
</script>

<style lang="scss" scoped>
@import "../scss/index.scss";

.lpd-template {
  display: none;
  @include lg {
    display: block;
  }

  @include lg {
    position: absolute;
    top: 25%;
  }
}
</style>
