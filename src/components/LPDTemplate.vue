<template>
  <div class="lpd-template">
    <img
      src="../assets/images/LPDComponentNoTemplate.svg"
      class="lpd-template__image"
    />
    <DrumButtonContainer :isToggled="this.toggle.isToggled" />
    <Toggle :header="this.toggle.header" :toggleFunction="this.handleToggle" />
  </div>
</template>

<script>
// import LPDImage from '../assets/images/'
import DrumButtonContainer from "./DrumButtonContainer";
import Toggle from "./Toggle";
export default {
  name: "LPDTemplate",
  components: { DrumButtonContainer, Toggle },
  data() {
    return {
      toggle: {
        header: "Show Letters",
        isToggled: false,
      },
    };
  },
  methods: {
    handleToggle() {
      this.toggle.isToggled = !this.toggle.isToggled;
      console.log("handleToggle");
    },
  },
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
