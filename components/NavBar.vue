<template>
  <nav class="nav">
    <nuxt-link :to="{ name: 'index' }" class="logo">
      <Logo class="LogoMark" />
    </nuxt-link>
    <div class="modal-trigger" @click="toggleModal">
      <div class="trigger-container">
        <svg class="trigger-icon" viewBox="0 0 32 32">
          <polygon
            class="line-bot"
            points="26,24 5,24 4.5,23.5 5,23 26,23 26.5,23.5 	"
          />
          <polygon
            class="line-mid"
            points="26,16.5 5,16.5 4.5,16 5,15.5 26,15.5 26.5,16 	"
          />
          <polygon
            class="line-top"
            points="26,9 5,9 4.5,8.5 5,8 26,8 26.5,8.5 	"
          />
        </svg>
      </div>
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
  .modal-trigger {
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

    .trigger-container {
      width: 32px;
      height: 32px;

      .trigger-icon {
        fill: var(--white);

        .line-top,
        .line-mid,
        .line-bot {
          transition: transform 0.375s cubic-bezier(0.33, 1, 0.68, 1);
        }

        .line-top {
          transform-origin: 16px 8.5px;
        }

        .line-mid {
          transform-origin: 16px 16px;
        }

        .line-bot {
          transform-origin: 16px 23.5px;
        }
      }
    }

    &:hover {
      cursor: pointer;

      .line-top {
        transform: rotate(-45deg) translate3d(-6px, -6px, 0);
      }

      .line-mid {
        transform: scaleX(1.5);
      }

      .line-bot {
        transform: rotate(45deg) translate3d(-6px, 6px, 0);
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
