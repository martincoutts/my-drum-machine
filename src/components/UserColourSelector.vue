<template>
  <div class="color-selector">
    <div class="color-selector__wrapper">
      <span class="color-selector__label">Pad Colour</span>
      <button
        v-for="(colour, index) in userColours"
        :key="index"
        :class="getClass(index, colour.class)"
        @click="changeColor(colour.colourValue, index)"
      ></button>
    </div>
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
          colourValue: "#73D5F0",
        },
        {
          class: "color-selector__button color-selector__button--purple",
          colourValue: "#8d67c8",
        },
        {
          class: "color-selector__button color-selector__button--yellow",
          colourValue: "#EEC95C",
        },
      ],
      activeButton: 0,
    };
  },
  methods: {
    changeColor(color, index) {
      const root = document.documentElement;
      root.style.setProperty("--user-button-color", color);
      this.activeButton = index;
    },
    getClass(index, colourClass) {
      return index === this.activeButton
        ? `${colourClass} active`
        : colourClass;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/index.scss";
.color-selector {
  display: none;

  @keyframes scaleButton {
    0% {
      transform: scale(1);

      -webkit-transform: scale(1);
    }
    100% {
      transform: scale(1.2);

      -webkit-transform: scale(1.2);
    }
  }

  .active {
    animation: scaleButton 1.2s cubic-bezier(0, 0.79, 0.86, 0.78) forwards;
    -webkit-animation: scaleButton 1.2s cubic-bezier(0, 0.79, 0.86, 0.78)
      forwards;
    animation-delay: 0.18s;
  }

  @include lg {
    display: flex;
    justify-content: flex-end;
    margin-bottom: 1rem;

    &__wrapper {
      display: flex;
      background-color: $main-black;
      padding: 1rem;
      border-radius: 6px;
    }

    &__label {
      align-self: center;
      font-size: $color-selector-font-size;
      color: #fff;
    }

    &__button {
      $colours: (
        "red": #e42c38,
        "green": #33db8f,
        "blue": #73d5f0,
        "purple": #8d67c8,
        "yellow": #eec95c,
      );

      height: 40px;
      width: 40px;
      margin-left: 0.75rem;
      border: solid 1px #fff;

      transition: border-width 0.5s ease;

      @each $name, $colourValue in $colours {
        &--#{$name} {
          background-color: $colourValue;
        }
      }

      &:hover {
        cursor: pointer;
        border-width: 4px;
      }
    }
  }
}
</style>
