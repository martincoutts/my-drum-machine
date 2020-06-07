<template>
  <div id="app">
    <LPDTemplate />
    <!-- <DrumButtonContainer /> -->
  </div>
</template>

<script>
// import DrumButtonContainer from "./components/DrumButtonContainer";
import LPDTemplate from "./components/LPDTemplate";
export default {
  name: "App",
  // components: { DrumButtonContainer },
  components: { LPDTemplate },
};
</script>

<style lang="scss">
@import "./scss/index.scss";
body {
  background-color: $app-background-color;
}
#app {
  font-size: $font-size-base;
  display: flex;
  justify-content: center;
  align-content: center;
}
</style>
