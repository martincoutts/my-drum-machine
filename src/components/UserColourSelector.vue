<template>
  <div class="color-selector">
    <button
      v-for="(color, index) in userColours"
      :class="color.class"
      :key="index"
    ></button>

    <!-- <div>
      <span v-for="(color, index) in userColours" :key="index">
        {{ index }}
      </span>
    </div> -->
  </div>
</template>

<script>
export default {
  name: "UserColourSelector",
  data() {
    return {
      userColours: [
        {
          class: "color-selector__button color-selector__button--red",
          colourValue: "#e42c38",
        },
        {
          class: "color-selector__button color-selector__button--green",
          colourValue: "#33DB8F",
        },
        {
          class: "color-selector__button color-selector__button--blue",
          colourValue: "#4680CF",
        },
        {
          class: "color-selector__button color-selector__button--purple",
          colourValue: "8d67c8",
        },
      ],
      //   userColours: ["#e42c38", "#33DB8F", "#4680CF", "8d67c8"],
    };
  },
  methods: {
    changeColor(color) {
      const root = document.documentElement;
      root.style.setProperty("--user-button-color", color);
      console.log("change color", color);
    },
  },
};
</script>

<style lang="scss" scoped>
.color-selector {
  display: flex;
  justify-content: flex-end;
  margin-bottom: 1rem;
  &__button {
    height: 40px;
    width: 40px;
    margin-left: 0.75rem;

    background-color: blue;

    &:hover {
      cursor: pointer;
    }
  }
}
</style>
