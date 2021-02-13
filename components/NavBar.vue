<template>
  <nav class="nav">
    <div class="sidebar tl">
      <div class="inner">
        <nuxt-link :to="{ name: 'index' }" class="nav-icon">
          <div class="nav-icon">
            <NuxtLogo class="logo-mark" />
          </div>
        </nuxt-link>
        <LogotypeTop class="logo-type tl" />
      </div>
    </div>
    <div class="sidebar br">
      <div class="inner">
        <div class="trigger nav-icon" @click="toggleModal">
          <icon-base viewbox="32" size="32"><hamburger /></icon-base>
        </div>
        <LogotypeBot class="logo-type br" />
      </div>
    </div>
  </nav>
</template>

<script>
import NuxtLogo from '~/assets/img/svg/logoMark.svg?inline'

export default {
  name: 'NavBar',
  components: { NuxtLogo },
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
    position: relative;
    display: block;

    @include mixins.respond(md) {
      position: fixed;
      top: 0;
      height: 100vh;
      background: var(--black);

      &.tl {
        left: 0;
        border-right: 1px solid var(--white);
      }
      &.br {
        right: 0;
        border-left: 1px solid var(--white);
      }
    }

    .inner {
      position: relative;
      width: 100%;
      height: 100%;

      @include mixins.respond(md) {
        padding: var(--type-baseline);
      }
    }

    .nav-icon {
      color: var(--white);
      width: 2.5rem;
      height: 2.5rem;
      transition: color 0.25s;

      &:hover {
        cursor: pointer;
        color: var(--blue);
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

      @include mixins.respond(md) {
        display: block;
        position: absolute;
        top: 50%;
        left: 50%;
        color: var(--white);
        fill: currentColor;
        width: 8rem;
        transform: rotate(-90deg) translate(-50%, -50%);
        transform-origin: 0% 0%;
      }
    }
  }
}
</style>
