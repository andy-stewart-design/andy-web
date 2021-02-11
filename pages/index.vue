<template>
  <div class="hero-container">
    <div class="above"></div>
    <div class="eye-container">
      <Eye class="eye" />
    </div>
    <div class="below">
      <p class="subhead">
        Andy Stewart is the
        <a href="https://turnstyle.studio/" target="_blank"
          >Digital Creative Director This will be deleted</a
        >
        at&nbsp;Turnstyle
      </p>
    </div>
  </div>
</template>

<script>
export default {
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
@use '@/assets/_base/mixins';

.hero-container {
  @include mixins.flex-center;
  flex-direction: column;
  width: 100vw;
  height: 100vh;
  min-height: 440px;

  .eye-container {
    @include mixins.flex-center;
    width: 100%;

    @include mixins.respond(landscape) {
      height: 84%;
    }

    .eye {
      width: 95%;
      height: 100%;
      margin: auto;

      @include mixins.respond(landscape) {
        width: 80%;
      }
    }
  }

  .above,
  .below {
    @include mixins.flex-center;
    flex: 1;
    width: 100%;
    padding-bottom: 2.5rem;

    @include mixins.respond(landscape) {
      align-items: center;
      height: 8%;
      padding-bottom: 0rem;
    }

    .subhead {
      font-family: var(--sans-book);
      font-size: var(--text-xs);
      text-align: center;
      letter-spacing: 0.1px;
      color: var(--white800);
      width: 80%;

      @include mixins.respond(landscape) {
        font-size: var(--text-sm);
      }

      a {
        font-family: var(--sans-bold);
        color: var(--magenta);
        background: -webkit-linear-gradient(
          0deg,
          var(--magenta) 0%,
          var(--blue) 100%
        );
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
      }
    }
  }
}
</style>
