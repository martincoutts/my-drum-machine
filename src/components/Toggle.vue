<template>
  <div class="toggle">
    <span>{{ this.header }}</span>
    <a-switch default-checked @change="this.toggleFunction" />
  </div>
</template>

<script>
export default {
  name: "Toggle",
  props: ["header", "label1", "label2", "toggleFunction"],
};
</script>

<style lang="scss" scoped>
.toggle {
  padding: 1rem;
}
</style>
