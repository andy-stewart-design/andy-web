<template>
  <div class="grid-container">
    <div class="column">
      <div class="content-container"></div>
    </div>
    <div class="column">
      <div class="content-container"></div>
    </div>
    <div class="column">
      <div class="content-container"></div>
    </div>
    <div class="column">
      <div class="content-container"></div>
    </div>
    <div class="column desktop">
      <div class="content-container"></div>
    </div>
    <div class="column desktop">
      <div class="content-container"></div>
    </div>
    <div class="column desktop">
      <div class="content-container"></div>
    </div>
    <div class="column desktop">
      <div class="content-container"></div>
    </div>
    <div class="column desktop">
      <div class="content-container"></div>
    </div>
    <div class="column desktop">
      <div class="content-container"></div>
    </div>
    <div class="column desktop">
      <div class="content-container"></div>
    </div>
    <div class="column desktop">
      <div class="content-container"></div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
@use '@/assets/_base/mixins';

div.grid-container {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  width: 100vw;
  height: 100vh;
  padding: 0 0.5rem;
  z-index: 9999999;
  pointer-events: none;

  @include mixins.respond(md) {
    padding: 0 4.25rem;
  }

  div.column {
    flex: 1;
    height: 100%;
    padding: 0 0.5rem;

    &.desktop {
      display: none;
    }

    @include mixins.respond(md) {
      padding: 0 0.75rem;

      &.desktop {
        display: block;
      }
    }

    div.content-container {
      width: 100%;
      height: 100%;
      background-color: var(--blue);
      opacity: 0.35;
    }
  }
}

body:active {
  div.grid-container {
    display: none;
  }
}
</style>
