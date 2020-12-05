<template>
  <nav class="nav">
    <nuxt-link :to="{ name: 'index' }" class="logo">
      <Logo class="LogoMark" />
    </nuxt-link>
    <div class="trigger" @click="toggleModal">
      <div class="trigger-icon"></div>
    </div>
    <p class="LogoType TypeTop">Andy Stew—</p>
    <p class="LogoType TypeBot">—Art Design</p>
  </nav>
</template>

<script>
import Logo from '@/components/Logo'

export default {
  name: 'NavBar',
  components: {
    Logo,
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
    display: flex;
    align-items: center;
    justify-content: center;
    width: 2.5rem;
    height: 2.5rem;
    z-index: 100000;

    @include breakpoints.respond(landscape) {
      width: 3rem;
      height: 3rem;
    }

    .trigger-icon {
      width: 16px;
      height: 16px;
      background-color: var(--white);
      border-radius: 50%;
      transition: transform 0.375s cubic-bezier(0.65, 0, 0.35, 1);
    }

    &:hover {
      cursor: pointer;

      .trigger-icon {
        transform: scale(1.5);
      }
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
