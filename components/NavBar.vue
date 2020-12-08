<template>
  <nav class="nav">
    <nuxt-link :to="{ name: 'index' }" class="logo">
      <Logo class="LogoMark" />
    </nuxt-link>
    <div class="trigger" @click="toggleModal">
      <icon-base viewbox="32" size="32"><hamburger /></icon-base>
    </div>
    <p class="LogoType TypeTop">Andy Stew—</p>
    <p class="LogoType TypeBot">—Art Design</p>
  </nav>
</template>

<script>
import Logo from '@/components/Logo'
import IconBase from '@/components/IconBase'
import Hamburger from '@/components/icons/Hamburger'

export default {
  name: 'NavBar',
  components: {
    Logo,
    IconBase,
    Hamburger,
  },
  methods: {
    toggleModal() {
      this.$emit('toggle-modal')
    },
  },
}
</script>

<style scoped lang="scss">
@use '@/assets/_base/breakpoints';

nav {
  .logo {
    position: fixed;
    top: 1rem;
    left: 1rem;
    width: 2.5rem;
    height: 2.5rem;
    z-index: 100000;

    @include breakpoints.respond(landscape) {
      width: 3rem;
      height: 3rem;
    }

    .LogoMark {
      width: 100%;
      fill: var(--white);
      transition: fill 0.25s;
    }
  }
  .trigger {
    position: fixed;
    top: 1rem;
    right: 1rem;
    padding: 0.25rem;
    z-index: 100000;
    color: var(--white);

    @include breakpoints.respond(landscape) {
      padding: 0.5rem;
    }

    &:hover {
      cursor: pointer;
    }
  }

  .LogoType {
    position: fixed;
    font-family: 'Sohne Breit', sans-serif;
    text-transform: uppercase;
    font-size: 0.875rem;
    letter-spacing: 3px;
    color: var(--white);
    width: 100%;
    text-align: center;
    z-index: 10000;

    .dash {
      font-family: Arial, Helvetica, sans-serif;
      font-weight: bold;
    }
  }

  @include breakpoints.respond(landscape) {
    font-size: 1rem;
  }

  .TypeTop {
    left: 0;
    top: 1.5rem;
    // border: 1px solid blue;

    @include breakpoints.respond(landscape) {
      top: 0;
      transform: rotate(90deg) translateY(-240%);
      transform-origin: 0 0;
      width: 100vh;
    }
  }

  .TypeBot {
    left: 0;
    bottom: 1.5rem;
    // border: 1px solid blue;

    @include breakpoints.respond(landscape) {
      top: 0;
      bottom: auto;
      left: auto;
      right: 0;
      transform: rotate(-90deg) translateY(-240%);
      transform-origin: 100% 0;
      width: 100vh;
    }
  }
}
</style>
