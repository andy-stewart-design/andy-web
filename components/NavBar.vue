<template>
  <nav class="nav">
    <div class="sidebar tl">
      <nuxt-link :to="{ name: 'index' }" class="nav-icon">
        <div class="nav-icon">
          <Logo class="logo-mark" />
        </div>
      </nuxt-link>
      <p class="logo-type type-top">Andy Stew—</p>
    </div>
    <div class="sidebar br">
      <div class="trigger nav-icon" @click="toggleModal">
        <icon-base viewbox="32" size="32"><hamburger /></icon-base>
      </div>
      <p class="logo-type type-bot">—Art Design</p>
    </div>
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

  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100vw;
  padding: var(--type-baseline);
  background: var(--black);
  border-bottom: 1px solid var(--white);
  z-index: 100;
  overflow: hidden;

  @include mixins.respond(md) {
    position: relative;
    width: 0;
    height: 0;
    padding: 0;
  }

  .sidebar {
    display: block;

    @include mixins.respond(md) {
      position: fixed;
      top: 0;
      height: 100vh;
      background: var(--black);
      padding: var(--type-baseline);

      &.tl {
        left: 0;
        border-right: 1px solid var(--white);
      }
      &.br {
        right: 0;
        border-left: 1px solid var(--white);
      }
    }
  }

  .nav-icon {
    color: var(--white);
    width: 2.5rem;
    height: 2.5rem;

    &:hover {
      cursor: pointer;
    }

    .logo-mark {
      width: 100%;
      fill: currentColor;
    }

    &.trigger {
      @include mixins.flex-center;
    }
  }

  .logo-type {
    display: none;
    position: fixed;
    font-family: var(--sans-wide);
    text-transform: uppercase;
    text-align: center;
    font-size: var(--text-sm);
    letter-spacing: 2px;
    color: var(--white);
    width: 100%;
    z-index: 99;
    pointer-events: none;

    @include mixins.respond(landscape) {
      font-size: 14px;
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
