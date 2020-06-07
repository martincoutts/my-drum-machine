<template>
  <div class="lpd-template">
    <img src="../assets/images/LPDComponentNoTemplate.svg" />
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
.lpd-template {
  position: absolute;
  top: 25%;
}
</style>
