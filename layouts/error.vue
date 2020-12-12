<template>
  <div class="error">
    <h1 class="error-headline"><span class="shift">:</span>&nbsp;(</h1>
    <p class="error-text">
      Sorry, we can't find the page you're looking&nbsp;for
    </p>
    <nuxt-link :to="{ name: 'index' }" class="logo-mark-container nav-top">
      <p class="error-link">Take Me Home</p>
    </nuxt-link>
  </div>
</template>

<script>
export default {}
</script>

<style scoped lang="scss">
@use '@/assets/_base/mixins';

.error {
  position: relative;
  @include mixins.flex-center;
  flex-direction: column;
  width: 100vw;
  height: 100vh;

  .error-headline {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-family: var(--sans-cond);
    font-size: 32rem;
    text-transform: uppercase;
    color: var(--blue);
    line-height: 1;
    margin-top: -2.5rem;
    opacity: 0.75;
    user-select: none;

    .shift {
      position: relative;
      top: -1.5rem;
    }

    @include mixins.respond(landscape) {
      font-size: 40rem;
      margin-top: -3rem;

      .shift {
        top: -2rem;
      }
    }
  }

  .error-text {
    position: relative;
    width: 90%;
    font-family: var(--sans-wide);
    font-size: var(--text-lg);
    text-align: center;
    margin-top: var(--m-base);
    margin-bottom: var(--m-base);

    @include mixins.respond(landscape) {
      width: 60%;
    }
  }

  .error-link {
    position: relative;
    font-family: var(--sans-wide);
    font-size: var(--text-xs);
    text-transform: uppercase;
    letter-spacing: 1px;
    padding: 0.5rem 1rem;
    transition: color 0.25s;

    &:hover {
      color: var(--blue);
    }
  }
}
</style>
