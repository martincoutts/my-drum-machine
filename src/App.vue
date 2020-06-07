<template>
  <div id="app">
    <DrumButtonContainer />
  </div>
</template>

<script>
import DrumButtonContainer from "./components/DrumButtonContainer";
export default {
  name: "App",
  components: { DrumButtonContainer },
};
</script>

<style lang="scss">
@import "./scss/index.scss";
body {
  background-color: $app-background-color;
}
#app {
  font-size: $font-size-base;
}
</style>
