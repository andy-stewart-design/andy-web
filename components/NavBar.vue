<template>
  <nav class="nav">
    <nuxt-link :to="{ name: 'index' }" class="logo-mark-container nav-top">
      <Logo class="logo-mark" />
    </nuxt-link>
    <div class="trigger nav-top" @click="toggleModal">
      <icon-base viewbox="32" size="32"><hamburger /></icon-base>
    </div>
    <p class="logo-type type-top">Andy Stew—</p>
    <p class="logo-type type-bot">—Art Design</p>
  </nav>
</template>

<script>
export default {
  name: 'NavBar',
  methods: {
    toggleModal() {
      this.$emit('toggle-modal')
    },
  },
}
</script>

<style scoped lang="scss">
@use '@/assets/_base/mixins';

nav {
  --nav-position: 1rem;

  @mixin nav-top-styles {
    position: fixed;
    width: 2.5rem;
    height: 2.5rem;
    z-index: 100;
    color: var(--white);

    @include mixins.respond(landscape) {
      width: 3rem;
      height: 3rem;
    }
  }

  .nav-top {
    position: fixed;
    width: 2.5rem;
    height: 2.5rem;
    z-index: 100;
    color: var(--white);

    @include mixins.respond(landscape) {
      width: 3rem;
      height: 3rem;
    }

    &.logo-mark-container {
      top: var(--nav-position);
      left: var(--nav-position);

      .logo-mark {
        width: 100%;
        fill: currentColor;
      }
    }

    &.trigger {
      @include mixins.flex-center;
      top: var(--nav-position);
      right: var(--nav-position);

      &:hover {
        cursor: pointer;
      }
    }
  }

  .logo-type {
    position: fixed;
    font-family: var(--sans-wide);
    text-transform: uppercase;
    text-align: center;
    font-size: var(--text-sm);
    letter-spacing: 3px;
    color: var(--white);
    width: 100%;
    z-index: 99;

    @include mixins.respond(landscape) {
      font-size: var(--text-base);
    }

    &.type-top {
      left: 0;
      top: 1.5rem;

      @include mixins.respond(landscape) {
        top: 0;
        transform: rotate(90deg) translateY(-220%);
        transform-origin: 0 0;
        width: 100vh;
      }
    }

    &.type-bot {
      left: 0;
      bottom: 1.5rem;
      // border: 1px solid blue;

      @include mixins.respond(landscape) {
        top: 0;
        bottom: auto;
        left: auto;
        right: 0;
        transform: rotate(-90deg) translateY(-220%);
        transform-origin: 100% 0;
        width: 100vh;
      }
    }
  }
}
</style>
