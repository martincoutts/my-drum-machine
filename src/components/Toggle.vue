<template>
  <div class="toggle">
    <span class="toggle__header">{{ this.header }}</span>
    <a-switch
      class="toggle__switch"
      default-checked
      @change="this.toggleFunction"
    />
  </div>
</template>

<script>
export default {
  name: "Toggle",
  props: ["header", "label1", "label2", "toggleFunction"],
};
</script>

<style lang="scss" scoped>
@import "../scss/index.scss";
.toggle {
  padding: 1rem 0;
  font-size: $toggle-font-size;
  color: #fff;
  display: grid;
  align-items: center;

  grid-template-columns: 50px 40px 50px;
  grid-template-rows: 30px 30px;

  &__header {
    justify-self: center;

    grid-column: 1 / span 3;
    grid-row: 1 / span 1;
  }
  &__switch {
    grid-column: 2 / span 1;
    grid-row: 2 / span 1;
  }

  .ant-switch-checked {
    background-color: $pad-border-color;
  }
}
</style>
