<template>
  <section class="button-hamburger" :class="classButton" @click="$emit('update:active', !active)">
    <span class="button-hamburger__content hamburguer">
      <span class="button-hamburger__bar bar-1"></span>
      <span class="button-hamburger__bar bar-2"></span>
      <span class="button-hamburger__bar bar-3"></span>
    </span>
  </section>
</template>

<script>
export default {
  props: {
    active: {
      type: Boolean,
      default: false
    }
  },

  computed: {
    classButton() {
      return { "button-hamburger--active": this.active };
    }
  }
};
</script>

<style lang="scss">
.button-hamburger {
  $self: &;

  position: relative;
  width: 50px;
  height: 50px;
  cursor: pointer;
  @include flex-and-center;

  &:active {
    transform: scale(0.9);
  }

  &__content {
    width: 32px;
    transition: 0.3s transform ease-in-out;
  }

  // Set each bar on center
  &__bar {
    display: block;
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    margin: auto;

    width: 32px;
    height: 3px;
    background: var(--accent-color);
    transition: 0.3s transform ease-in-out;
  }

  // Move up bar 1
  .bar-1 {
    transform: rotate(0) translate3d(0, -10px, 0);
  }

  // Move down bar 3
  .bar-3 {
    transform: rotate(0) translate3d(0, 10px, 0);
  }

  // Modifiers
  &--active {
    #{$self}__content {
      transform: rotate(180deg);

      .bar-1 {
        transform: rotate(45deg) translate3d(0, 0, 0);
      }
      .bar-2 {
        opacity: 0;
      }
      .bar-3 {
        transform: rotate(-45deg) translate3d(0, 0, 0);
      }
    }
  }
}
</style>
