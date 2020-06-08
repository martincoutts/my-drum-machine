<template>
  <div id="app">
    <LPDTemplate />
    <div class="drum-button-container__mobile-wrapper">
      <DrumButtonContainer />
    </div>
  </div>
</template>

<script>
import DrumButtonContainer from "./components/DrumButtonContainer";
import LPDTemplate from "./components/LPDTemplate";

export default {
  name: "App",

  components: { LPDTemplate, DrumButtonContainer },
};
</script>

<style lang="scss">
@import "./scss/index.scss";

#app {
  font-size: $font-size-base;
  display: grid;
  height: 90vh;
  width: 100%;

  .drum-button-container__mobile-wrapper {
    align-self: center;
    margin: 0 auto;
    width: 100%;

    @include lg {
      display: none;
    }
  }

  @include lg {
    display: flex;
    justify-content: center;
    align-content: center;
  }
}
</style>
