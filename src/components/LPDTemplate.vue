<template>
  <div class="lpd-template">
    <img
      src="../assets/images/LPDComponentNoTemplate.svg"
      class="lpd-template__image"
    />
    <DrumButtonContainer :isToggled="this.toggle.isToggled" />
    <div class="lpd-template__toggle-container">
      <Toggle
        :header="this.toggle.header"
        :toggleFunction="this.handleToggle"
      />
    </div>
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
        header: "Show Keys",
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
    display: grid;
    position: absolute;
    top: 25%;
  }

  &__toggle-container {
    display: none;
    @include lg {
      display: block;
      background-color: $main-black;
      margin: 1rem 0;
      padding: 0.25rem;
      border-radius: 6px;
      justify-self: flex-end;
    }
  }
}
</style>
