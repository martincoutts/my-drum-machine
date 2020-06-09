<template>
  <div class="lpd-template">
    <div class="colour-selector__container">
      <UserColourSelector />
    </div>
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
import DrumButtonContainer from "./DrumButtonContainer";
import Toggle from "./Toggle";
import UserColourSelector from "./UserColourSelector";
export default {
  name: "LPDTemplate",
  components: { DrumButtonContainer, Toggle, UserColourSelector },
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
    align-self: center;
  }

  &__image {
    grid-row: 2 / span 1;
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
