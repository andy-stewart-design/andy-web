<template>
  <div class="container">
    <div class="above"></div>
    <div class="eye-container">
      <Eye class="HomeLogo" />
    </div>
    <div class="below">
      <p class="subhead">
        Andy Stewart is the
        <a href="https://turnstyle.studio/" target="_blank"
          >Digital Creative Director</a
        >
        at&nbsp;Turnstyle
      </p>
    </div>
  </div>
</template>

<script>
import Eye from '@/components/Eye'

export default {
  components: {
    Eye,
  },
  data() {
    return {
      title: 'The Graphic Design Portfolio of Andy Stewart',
      descr:
        'Andy Stewart is the Digital Creative Director at Turnstyle in Seattle',
    }
  },
  head() {
    return {
      title: this.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.descr,
        },
      ],
    }
  },
}
</script>

<style scoped lang="scss">
@use '@/assets/_base/breakpoints';

.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
  min-height: 520px;
  // border: 4px solid blue;

  .eye-container {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    // border: 1px solid blue;

    @include breakpoints.respond(landscape) {
      height: 84%;
    }

    .HomeLogo {
      width: 95%;
      height: 100%;
      margin: auto;
      // border: 2px solid yellow;

      @include breakpoints.respond(landscape) {
        width: 80%;
      }
    }
  }

  .above,
  .below {
    display: flex;
    flex: 1;
    justify-content: center;
    align-items: center;
    width: 100%;
    // padding-bottom: 2.5rem;
    // background: grey;

    @include breakpoints.respond(landscape) {
      align-items: center;
      height: 8%;
    }

    .subhead {
      font-size: 0.75rem;
      font-family: 'Sohne Bold', sans-serif;
      text-align: center;
      color: #bebebe;
      width: 80%;

      @include breakpoints.respond(landscape) {
        font-size: 0.875rem;
      }

      a {
        color: #c300ff;
        background: -webkit-linear-gradient(0deg, #c300ff 30%, #4346ff 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
      }
    }
  }

  .below {
    padding-bottom: 2.5rem;

    @include breakpoints.respond(landscape) {
      padding-bottom: 0rem;
    }
  }
}
</style>
