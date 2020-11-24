<template>
  <nav class="nav">
    <nuxt-link :to="{ name: 'index' }" class="logo">
      <Logo class="LogoMark" />
    </nuxt-link>
    <p class="LogoType TypeTop">Andy Stew<span class="dash">—</span></p>
    <p class="LogoType TypeBot"><span class="dash">—</span>Art Design</p>
  </nav>
</template>

<script>
import Logo from '@/components/Logo'

export default {
  components: {
    Logo,
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

    @include breakpoints.respond(md) {
      width: 3rem;
      height: 3rem;
    }

    .LogoMark {
      width: 100%;
      fill: #fff;
      transition: fill 0.25s;
    }
  }

  .LogoType {
    position: fixed;
    font-family: 'Sohne Breit', sans-serif;
    text-transform: uppercase;
    font-size: 0.875rem;
    letter-spacing: 3px;
    color: #fff;
    width: 100%;
    text-align: center;
    z-index: 10000;

    .dash {
      font-family: Arial, Helvetica, sans-serif;
      font-weight: bold;
    }
  }

  @include breakpoints.respond(md) {
    font-size: 1rem;
  }

  .TypeTop {
    left: 0;
    top: 1.5rem;
    // border: 1px solid blue;

    @include breakpoints.respond(md) {
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

    @include breakpoints.respond(md) {
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
